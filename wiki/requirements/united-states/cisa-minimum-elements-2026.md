---
type: Requirement
title: CISA 2026 Minimum Elements for a Software Bill of Materials (SBOM)
description: Federal SBOM baseline issued by CISA on 2026-07-29, updating and replacing
  the 2021 NTIA minimum elements.
category: requirement
tags:
- requirement
- us
- cisa
- sbom
- minimum-elements
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: cisa-minimum-elements-2026
  resource: https://www.cisa.gov/resources-tools/resources/2026-minimum-elements-software-bill-materials-sbom
  title: 2026 Minimum Elements for a Software Bill of Materials (SBOM)
  author: Cybersecurity and Infrastructure Security Agency (CISA)
  last_modified: '2026-07-29T00:00:00Z'
x-software-supply-chain:
  jurisdiction: US
  authority_level: guidance
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

Published on July 29, 2026, the **CISA 2026 Minimum Elements for an SBOM** officially updates and replaces the original 2021 NTIA minimum elements guide[^cisa-minimum-elements-2026].

**Binding / contractual / guidance**: Federal civilian guidance and contractual baseline for federal procurement.

# Evolution from NTIA 2021 to CISA 2026
The 2026 baseline modernizes terminology and expands data requirements:
- **Renamed Fields**:
  - `Author Name` -> `SBOM Author`
  - `Supplier Name` -> `Component Producer`
  - `Version String` -> `Component Version`
- **New Mandatory Elements**:
  - `Component Hash Algorithm`: Explicit declaration of hashing algorithm alongside hash value.
  - `Component License`: Documented component license expression or declaration.
  - `SBOM Tool Name`: Name and version of the automated tool generating the SBOM.
  - `SBOM Generation Context`: Build-time, source-time, or runtime analysis context.
- **Recognized Formats**: SPDX (2.2.1, 2.3, 3.0), OWASP CycloneDX (1.5, 1.6, 1.7), and ISO/IEC 19770-2 (SWID).

# Related concepts
- [NTIA Minimum Elements (Superseded)](ntia-minimum-elements.md)
- [SPDX 2.3](../../standards/sbom-formats/spdx-2-3.md)
- [CycloneDX 1.7](../../standards/sbom-formats/cyclonedx-1-7.md)

[^cisa-minimum-elements-2026]: Cybersecurity and Infrastructure Security Agency (CISA), 2026 Minimum Elements for a Software Bill of Materials (SBOM), https://www.cisa.gov/resources-tools/resources/2026-minimum-elements-software-bill-materials-sbom
