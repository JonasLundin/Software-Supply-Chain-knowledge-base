---
type: Standard
title: OWASP Software Component Verification Standard (SCVS)
description: Community standard defining functional requirements for identifying,
  analyzing, and controlling third-party software components.
category: standard
tags:
- standard
- framework
- owasp
- scvs
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: owasp-scvs-spec
  resource: https://owasp.org/www-project-software-component-verification-standard/
  title: OWASP Software Component Verification Standard (SCVS)
  author: OWASP Foundation
  last_modified: '2023-10-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **OWASP Software Component Verification Standard (SCVS)** establishes an objective verification benchmark for evaluating third-party software component risk in application stacks[^owasp-scvs-spec].

# Core Control Areas
1. **Inventory**: Verification that all software components, libraries, and transitive dependencies are cataloged in an automated SBOM.
2. **Analysis**: Ongoing inspection of identified components against vulnerability catalogs, end-of-life status, and license compatibility matrices.
3. **Integrity**: Validation of digital signatures, cryptographic hashes, and provenance metadata prior to runtime deployment.

# Related concepts
- [CycloneDX 1.7](../sbom-formats/cyclonedx-1-7.md)
- [CRA SBOM Mandate](../../requirements/european-union/cra-sbom-mandate.md)

[^owasp-scvs-spec]: OWASP Foundation, OWASP Software Component Verification Standard (SCVS), https://owasp.org/www-project-software-component-verification-standard/
