---
type: Standard
title: Dead Simple Signing Envelope (DSSE)
description: Cryptographic envelope format separating payload content from cryptographic
  signatures to prevent canonicalization vulnerabilities.
category: standard
tags:
- standard
- attestation
- dsse
- signing
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: dsse-spec
  resource: https://github.com/secure-systems-lab/dsse
  title: Dead Simple Signing Envelope (DSSE) Specification
  author: Secure Systems Lab (New York University)
  last_modified: '2023-02-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

Developed by the Secure Systems Lab, the **Dead Simple Signing Envelope (DSSE)** is a signature envelope standard designed to securely sign arbitrary supply chain payloads (such as in-toto statements, SBOMs, and provenance proofs)[^dsse-spec].

# Architectural Security Features
- **Canonicalization Defense**: Eliminates complex in-band XML/JSON canonicalization vulnerabilities by enforcing Pre-Authentication Encoding (PAE) over payload type and body.
- **Format Agnostic**: Accepts arbitrary binary or text payloads (JSON, CBOR, protobuf).
- **Widespread Integration**: Serves as the primary signing wrapper within Sigstore Cosign, in-toto attestations, and SLSA provenance artifacts.

# Intellectual Property and Licensing
DSSE is published by Secure Systems Lab under the Apache License 2.0.

# Related concepts
- [in-toto Attestation](in-toto.md)
- [Sigstore](sigstore.md)

[^dsse-spec]: Secure Systems Lab (New York University), Dead Simple Signing Envelope (DSSE) Specification, https://github.com/secure-systems-lab/dsse
