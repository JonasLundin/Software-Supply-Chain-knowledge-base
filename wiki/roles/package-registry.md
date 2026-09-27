---
type: Role
title: 'Role: Package Registry'
description: Central repository hosting, indexing, and serving software packages,
  containers, signatures, and provenance tokens.
category: role
tags:
- supply-chain
- role
- registry
- npm
- pypi
- oci
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
- id: spdx-iso-5962
  resource: https://spdx.dev/specifications/
  title: Software Package Data Exchange (SPDX) Specification (ISO/IEC 5962:2021)
  author: Linux Foundation / ISO/IEC JTC 1
  last_modified: '2021-09-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: guidance
  instrument_status: in_force
  provision: OpenSSF / SLSA Ecosystem Guidance
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

A **Package Registry** is a centralized or distributed repository service (e.g., npm, PyPI, Maven Central, crates.io, Docker Hub, OCI registries) that ingests, indexes, validates, and distributes compiled packages or container images to downstream consumers[^slsa-framework].

Registries operate at the vital intersection of open-source distribution and enterprise supply-chain consumption.

# Critical Integrity Capabilities

To protect against account takeovers, dependency confusion, and malware injection, modern package registries implement:
- **Mandatory Multi-Factor Authentication (MFA)**: Requiring hardware security keys or authenticator apps for all maintainers.
- **Cryptographic Signature Verification**: Validating Sigstore or PGP signatures before publishing artifacts.
- **Provenance Verification**: Ingesting SLSA provenance attestations and exposing provenance verification badges on package web portals.
- **Namespace Protection & Typosquatting Defenses**: Automated heuristic scans blocking homoglyph attacks and namespace squatting.

# Related concepts
- [Software Producer](software-producer.md)
- [Package URL (purl)](../glossary/package-url.md)
- [Sigstore Ecosystem](../standards/attestation-and-provenance/sigstore.md)

[^slsa-framework]: OpenSSF SLSA Working Group, Supply chain Levels for Software Artifacts (SLSA) Specification v1.0, https://slsa.dev/spec/v1.0/
[^spdx-iso-5962]: Linux Foundation / ISO/IEC JTC 1, Software Package Data Exchange (SPDX) Specification (ISO/IEC 5962:2021), https://spdx.dev/specifications/
