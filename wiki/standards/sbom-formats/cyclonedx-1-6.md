---
type: Standard
title: OWASP CycloneDX 1.6 (ECMA-424 1st Edition)
description: Prior version of the CycloneDX specification standardized as ECMA-424
  1st Edition in June 2024.
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
stale_after: '2027-06-30T00:00:00Z'
sources:
- id: cyclonedx-1-6-spec
  resource: https://cyclonedx.org/docs/1.6/
  title: OWASP CycloneDX Software Bill of Materials Specification v1.6 (ECMA-424 1st
    Edition)
  author: OWASP Foundation / Ecma International
  last_modified: '2024-06-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: superseded
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**OWASP CycloneDX 1.6** was published in spring 2024 and formally ratified as **ECMA-424 1st Edition** in June 2024[^cyclonedx-1-6-spec].

> [!NOTE]
> **Superseded Standard**: CycloneDX 1.6 is superseded by [CycloneDX 1.7 (ECMA-424 2nd Edition)](cyclonedx-1-7.md).

# Core Capabilities and Cryptographic Asset Inventory
- **Cryptographic Bill of Materials (CBOM)**: Introduced cryptographic asset modeling using `components[].type: cryptographic-asset` coupled with `cryptoProperties` (specifying algorithm family, key length, mode of operation, and security level).
- **Machine Learning BOM (ML-BOM)**: Standardized representations of deep learning models, training data provenance, hyper-parameters, and model card metadata.
- **Formulations and Lifecycle**: Captured build steps, workflows, and toolchains within the `declarations` and `formulation` elements.

# Intellectual Property and Licensing
OWASP CycloneDX is licensed under the Apache License 2.0.

# Related concepts
- [CycloneDX 1.7](cyclonedx-1-7.md)
- [CycloneDX 1.5](cyclonedx-1-5.md)

[^cyclonedx-1-6-spec]: OWASP Foundation / Ecma International, OWASP CycloneDX Software Bill of Materials Specification v1.6 (ECMA-424 1st Edition), https://cyclonedx.org/docs/1.6/
