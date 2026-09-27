---
type: Standard
title: OWASP CycloneDX 1.7 (ECMA-424 2nd Edition)
description: Flagship software and system bill of materials specification featuring
  cryptographic assets, attestation, and machine learning components.
category: standard
tags:
- standard
- sbom
- cyclonedx
- format
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: cyclonedx-1-7-spec
  resource: https://github.com/CycloneDX/specification
  title: OWASP CycloneDX Software Bill of Materials Specification v1.7 (ECMA-424 2nd
    Edition)
  author: OWASP Foundation / Ecma International
  last_modified: '2025-10-21T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**OWASP CycloneDX 1.7**, approved in October 2025 and standardized as **ECMA-424 2nd Edition** in December 2025, represents the current international release of the CycloneDX bill of materials standard[^cyclonedx-1-7-spec].

# Architectural Capabilities
CycloneDX 1.7 provides rich multi-domain inventory capabilities:
- **Component Typology**: Covers application binaries, libraries, frameworks, containers, operating systems, hardware devices, firmware, machine learning models, and cryptographic assets.
- **Cryptographic Bill of Materials (CBOM)**: Uses `components[].type: cryptographic-asset` alongside dedicated `cryptoProperties` objects to inventory classical algorithms, keys, certificates, and post-quantum cryptographic primitives.
- **Integrated Vulnerability and VEX Support**: Embeds machine-readable VEX statements (`not_affected`, `affected`, `fixed`, `under_investigation`) directly within product metadata.
- **Attestation and Lifecycle Proof**: Supports software supply chain identity verification via cryptographic signatures and pedigree traceability.

# Intellectual Property and Licensing
OWASP CycloneDX is an open standard licensed under the Apache License 2.0. ECMA-424 is published under Ecma International copyright and royalty-free patent policies.

# Related concepts
- [CycloneDX 1.6 (Superseded)](cyclonedx-1-6.md)
- [CycloneDX VEX](../vex/cyclonedx-vex.md)
- [CISA 2026 Minimum Elements](../../requirements/united-states/cisa-minimum-elements-2026.md)

[^cyclonedx-1-7-spec]: OWASP Foundation / Ecma International, OWASP CycloneDX Software Bill of Materials Specification v1.7 (ECMA-424 2nd Edition), https://github.com/CycloneDX/specification
