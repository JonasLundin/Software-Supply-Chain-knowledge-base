---
type: Standard
title: in-toto Attestation Framework
description: CNCF Graduated cryptographic framework for defining, recording, and verifying multi-step software supply chain pipelines and metadata envelopes.
category: standard
tags:
  - supply-chain
  - in-toto
  - attestation
  - dsse
  - provenance
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
  provision: in-toto Specification v1.0 / in-toto Attestation v1
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**in-toto** is a cryptographic framework and Cloud Native Computing Foundation (CNCF) Graduated project that provides comprehensive, end-to-end integrity guarantees for the entire software supply chain[^slsa-framework]. Developed originally by researchers at New York University (NYU), in-toto models the software production process as an ordered sequence of discrete steps performed by authorized functionaries (humans or automated machines).

By combining signed supply chain layouts, cryptographic link metadata, and standard attestation envelopes (such as the in-toto Statement and Dead Simple Signing Envelope / DSSE), in-toto enables verifiers to mathematically prove that an end product was built strictly according to authorized procedures without unauthorized alterations.

```
       +-------------------------------------------------------------+
       |                  Project Owner Root Key                     |
       |  Signs the Software Supply Chain Layout (Governance Rules)  |
       +-------------------------------------------------------------+
                                      |
         +----------------------------+----------------------------+
         |                                                         |
         v                                                         v
+-------------------------------+                         +-------------------------------+
|     Step 1: Clone & Test      |                         |      Step 2: Build & Pack     |
| - Functionary: CI Runner      |---- Products (hashes) ->| - Functionary: Build Agent    |
| - Generates: link.test.json   |                         | - Generates: link.build.json  |
+-------------------------------+                         +-------------------------------+
         |                                                         |
         +----------------------------+----------------------------+
                                      |
                                      v
+-----------------------------------------------------------------------------------------+
|                                    Client Verifier                                      |
|  - Ingests Layout + Links + Final Artifact                                              |
|  - Executes `in-toto-verify`: matches materials against products across all steps       |
+-----------------------------------------------------------------------------------------+
```

# Technical Scope / Normative Requirements

### 1. Supply Chain Layouts and Functionaries

The project owner defines a **Layout** file signed by an offline cryptographic key. The layout defines:
- **Steps**: Discrete pipeline actions (e.g. `checkout`, `build`, `test`, `package`).
- **Functionaries**: Public keys authorized to perform each specific step.
- **Artifact Rules**: Match rules that tie inputs (`materials`) to outputs (`products`). For instance, a rule can specify that the artifact compiled in step 2 must strictly match the cryptographic digest of the source code checked out in step 1.
- **Inspections**: Automated checks run during verification (e.g. inspecting an unpacked tarball).

### 2. Link Metadata

When a functionary completes a step, it generates a signed **Link** record capturing:
- `name`: Name of the step corresponding to the layout.
- `materials`: Cryptographic hashes (SHA-256) of all files present when the step began.
- `products`: Cryptographic hashes of all files produced by the step.
- `byproducts`: Standard output, standard error, and exit codes.
- `signatures`: Digital signature of the functionary.

### 3. The in-toto Attestation Framework (Statement v1)

Beyond traditional link files, the in-toto community standardized the generic **in-toto Attestation Framework**, which serves as the universal envelope for supply chain metadata across the industry:

```json
{
  "_type": "https://in-toto.io/Statement/v1",
  "subject": [
    {
      "name": "myapp-v1.0.tar.gz",
      "digest": {
        "sha256": "47a3e819b5c2a129ef99...38a2"
      }
    }
  ],
  "predicateType": "https://slsa.dev/provenance/v1",
  "predicate": { ... }
}
```

The statement links one or more target artifacts (`subject`) to a typed claim (`predicate`). Standardized predicate types include:
- `https://slsa.dev/provenance/v1`: SLSA build provenance.
- `https://cyclonedx.org/bom`: Embedded CycloneDX SBOM.
- `https://spdx.dev/Document`: Embedded SPDX SBOM.
- `https://openvex.dev/ns/v0.2.0`: OpenVEX exploitability statements.

### 4. Dead Simple Signing Envelope (DSSE)

in-toto attestations are transported within a DSSE envelope (`application/vnd.dsse.envelope.v1+json`), completely separating signature encoding from the payload:

```json
{
  "payloadType": "application/vnd.in-toto+json",
  "payload": "eyJfdHlwZSI6ICdodHRwczovL2luLXRvdG8uaW8vU3RhdGVtZW50L3YxJy4uLn0=",
  "signatures": [
    {
      "keyid": "SHA256:4y+81vD...",
      "sig": "MEUCIQDxvG7Y..."
    }
  ]
}
```

# Applicability & Operational Impact

in-toto forms the foundational metadata layer for modern software supply chain security:

- **SLSA Provenance Foundation**: All SLSA provenance assertions rely on the in-toto Statement specification.
- **Sigstore and Cosign**: Cosign's `--predicate` attestation subsystem natively consumes and verifies in-toto statements.
- **Policy Enforcement**: Admission controllers (Kyverno, Conftest, OPA Gatekeeper) evaluate in-toto predicates to enforce organizational deployment guardrails.

# Practical Implementation

### Recording a Step with in-toto CLI

```bash
# Record the build step executed by an authorized build key
in-toto-run --step-name build \
            --materials src/ \
            --products target/myapp.bin \
            --key build-key.pem \
            -- make release
```

### End-to-End Layout Verification

```bash
# Verify entire pipeline execution against signed root layout
in-toto-verify --layout root.layout \
               --layout-keys root-key.pub \
               --link-dir ./metadata/
```

### Packaging as DSSE via Cosign

```bash
# Attest an in-toto statement to an OCI container image
cosign attest --yes \
  --key cosign.key \
  --type https://slsa.dev/provenance/v1 \
  --predicate provenance.json \
  docker.io/acme/my-service:1.0.0
```

# Dates and Transitions

- **2016**: in-toto project launched at New York University.
- **2019**: in-toto accepted into the CNCF.
- **2021**: IETF standardization of DSSE; widespread adoption by Sigstore and OpenSSF SLSA.
- **March 2024**: in-toto graduated from the Cloud Native Computing Foundation.

# Related concepts

- [SLSA v1.0 Specification](slsa-1-0.md)
- [Sigstore Signing & Verification](sigstore.md)
- [Software Provenance Glossary](../../glossary/provenance.md)
- [SBOM Verification and Signing](../../procedures/sbom-verification-and-signing.md)
- [Build Platform Role](../../roles/build-platform.md)

[^slsa-framework]: OpenSSF SLSA Working Group, Supply chain Levels for Software Artifacts (SLSA) Specification v1.0, https://slsa.dev/spec/v1.0/
