---
type: Standard
title: Sigstore Signing and Verification Ecosystem
description: Open-source public infrastructure project for keyless cryptographic signing, certificate issuance (Fulcio), and transparent ledger verification (Rekor).
category: standard
tags:
  - supply-chain
  - sigstore
  - cosign
  - fulcio
  - rekor
  - signing
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
  - id: slsa-framework
    resource: https://slsa.dev/spec/v1.0/
    title: Supply chain Levels for Software Artifacts (SLSA) Specification v1.0
    author: OpenSSF SLSA Working Group
    last_modified: '2023-04-18T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  provision: Sigstore Architecture Specification
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Sigstore** is an open-source public good project under the Open Source Security Foundation (OpenSSF) and the Linux Foundation designed to make cryptographic signing and verification of software artifacts ubiquitous, accessible, and automated[^slsa-framework]. Historically, cryptographic signing of software (via PGP or long-lived PKI certificates) suffered from catastrophic friction: private keys were frequently leaked, lost, or improperly managed, and revocation mechanisms were slow or absent.

Sigstore eliminates the long-term private key management problem through **keyless signing**. By tying ephemeral cryptographic key pairs to verifiable OpenID Connect (OIDC) identities (such as GitHub Actions, GitLab CI, or developer Google accounts) and logging all signatures into an immutable, append-only transparency log (Rekor), Sigstore provides unforgeable auditability for binaries, containers, SBOMs, and supply-chain attestations.

```
+-----------------------------------------------------------------------------------------+
|                                    Developer / CI Pipeline                              |
|  1. Obtains OIDC Token (Identity: ci-runner@acme.com)                                   |
|  2. Generates ephemeral keypair in memory (public/private)                              |
+-----------------------------------------------------------------------------------------+
         |                                                                 ^
         | OIDC Token + Ephemeral Public Key                               |
         v                                                                 |
+-------------------------+                                                |
|         Fulcio          |                                                |
| (Short-lived Root CA)   |                                                |
| Issues 10-minute cert   |                                                |
| with OIDC Subject SAN   |                                                |
+-------------------------+                                                |
         |                                                                 |
         | Returns Certificate                                             |
         +-----------------------------------------------------------------+
         |
         | Signs Artifact & Attestations with Ephemeral Private Key
         | Destroys Private Key immediately
         v
+-----------------------------------------------------------------------------------------+
|                                         Rekor                                           |
| (Tamper-evident, Append-Only Transparency Log / Merkle Tree)                             |
| Records: Artifact Digest + Fulcio Cert + Signature + Inclusion Proof                     |
+-----------------------------------------------------------------------------------------+
                                         |
                                         v
+-----------------------------------------------------------------------------------------+
|                                  Consumer / Verifier                                    |
| Checks: (1) Fulcio Root of Trust, (2) Subject Identity in Cert, (3) Proof in Rekor Log  |
+-----------------------------------------------------------------------------------------+
```

# Technical Scope / Normative Requirements

### 1. Architectural Components

Sigstore is composed of three interconnected foundational components:

| Component | Role & Function | Key Protocols & Standards |
| :--- | :--- | :--- |
| **Fulcio** | A free, public Certificate Authority that issues short-lived X.509 certificates (typically valid for 10 minutes). Fulcio verifies an incoming OIDC bearer token and embeds the subject identity in the Subject Alternative Name (SAN) extension of the certificate. | X.509, OpenID Connect (OIDC), RFC 5280. |
| **Rekor** | An append-only, tamper-evident transparency log based on a cryptographic Merkle tree (Trillian). Rekor provides an unforgeable public ledger where every signature and attestation is recorded alongside an inclusion proof and a signed log root. | Merkle tree, JSON schema, RFC 6962 inspiration. |
| **Cosign** | A developer-facing CLI and Go library designed to sign, verify, and store containers, arbitrary blobs, SBOMs, and in-toto attestations inside OCI registries without requiring sidecar databases. | OCI Registry Spec, DSSE, in-toto. |
| **Timestamp Authority (TSA)** | An RFC 3161 compliant timestamping service that asserts the exact time a signature was produced, guaranteeing validity long after the short-lived Fulcio certificate has expired. | RFC 3161, PKI time-stamping. |

### 2. Trust Model & Keyless Verification

Because the ephemeral private key is discarded seconds after signature generation, traditional certificate expiration checks would fail. Sigstore's trust model resolves this by requiring the verifier to prove:
1. The signature was valid at the exact time it was logged into Rekor (verified via Rekor's signed timestamp or external TSA).
2. The signing certificate was issued by an authentic Fulcio root of trust.
3. The identity embedded in the certificate matches the expected policy (e.g. `issuer == "https://token.actions.githubusercontent.com"` and `subject == "https://github.com/acme/repo/.github/workflows/build.yml@refs/heads/main"`).
4. The entry exists within the Rekor transparency log via an inclusion proof.

# Applicability & Operational Impact

Sigstore has become the default signing technology across the open-source supply chain:

- **Package Registries**: Adopted by npm, PyPI, and Homebrew for publishing provenance attestations.
- **Container Registries & OCI**: Signatures and in-toto attestations are stored directly in OCI registries as image tag tags (e.g. `sha256-...sig` and `sha256-...att`).
- **Policy Admission Controllers**: Kubernetes admission controllers (e.g. Sigstore Policy Controller, Kyverno) enforce that only images with valid Sigstore signatures from trusted GitHub workflows are scheduled onto production clusters.

# Practical Implementation

### Signing a Container Keylessly in GitHub Actions

In GitHub Actions, the runner obtains an OIDC token automatically if given `id-token: write` permissions:

```bash
# Keyless signing of a container image
cosign sign --yes registry.acme.com/apps/payment-engine:v1.0.0
```

### Attesting an SBOM to an OCI Image

```bash
# Attach an SPDX or CycloneDX SBOM as an in-toto attestation
cosign attest --yes \
  --type cyclonedx \
  --predicate sbom.cdx.json \
  registry.acme.com/apps/payment-engine:v1.0.0
```

### Verifying Signatures and Identity

The consumer or deployment policy enforces identity constraints:

```bash
cosign verify \
  --certificate-identity-regexp "^https://github.com/acme/.*" \
  --certificate-oidc-issuer "https://token.actions.githubusercontent.com" \
  registry.acme.com/apps/payment-engine:v1.0.0
```

### Verifying an Attested SBOM

```bash
# Retrieve and verify the attached CycloneDX SBOM
cosign verify-attestation \
  --type cyclonedx \
  --certificate-identity "https://github.com/acme/payment-engine/.github/workflows/release.yml@refs/heads/main" \
  --certificate-oidc-issuer "https://token.actions.githubusercontent.com" \
  registry.acme.com/apps/payment-engine:v1.0.0 | jq -r .payload | base64 -d | jq .predicate
```

# Dates and Transitions

- **March 2021**: Sigstore project announced by the Linux Foundation and Red Hat.
- **October 2022**: Sigstore General Availability (GA) declared for public good infrastructure.
- **2023–2024**: npm and PyPI implement default Sigstore keyless attestation for maintainers.
- **2026**: Broad international recognition as a standard mechanism for satisfying US EO 14028 and EU CRA cryptographic provenance expectations.

# Related concepts

- [in-toto Attestation Framework](in-toto.md)
- [SLSA v1.0 Specification](slsa-1-0.md)
- [SBOM Verification and Signing](../../procedures/sbom-verification-and-signing.md)
- [Package Registry Role](../../roles/package-registry.md)
- [Build Platform Role](../../roles/build-platform.md)

[^slsa-framework]: OpenSSF SLSA Working Group, Supply chain Levels for Software Artifacts (SLSA) Specification v1.0, https://slsa.dev/spec/v1.0/
