---
type: Standard
title: Sigstore Software Signing Ecosystem
description: Open-source project for standardizing keyless cryptographic signing,
  verification, and transparency logging of software artifacts.
category: standard
tags:
- standard
- signing
- attestation
- sigstore
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: sigstore-project
  resource: https://www.sigstore.dev/
  title: Sigstore Signing and Transparency Architecture
  author: OpenSSF / Linux Foundation
  last_modified: '2024-06-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Sigstore** is an OpenSSF project providing non-profit, automated cryptographic signing and transparency services to eliminate traditional private key management overhead in software supply chains[^sigstore-project].

# Core Components
- **Fulcio**: A free, automated Certificate Authority issuing short-lived X.509 certificates based on OpenID Connect (OIDC) identities (e.g., GitHub Actions, Google, or corporate OAuth).
- **Rekor**: An immutable, tamper-evident transparency log recording signed artifact hashes and certificates.
- **Cosign**: Container signing, verification, and storage of SBOMs and attestations within OCI image registries.

# Intellectual Property and Licensing
Sigstore is published under the Apache License 2.0.

# Related concepts
- [in-toto Attestation](in-toto.md)
- [SLSA v1.2](slsa-1-2.md)

[^sigstore-project]: OpenSSF / Linux Foundation, Sigstore Signing and Transparency Architecture, https://www.sigstore.dev/
