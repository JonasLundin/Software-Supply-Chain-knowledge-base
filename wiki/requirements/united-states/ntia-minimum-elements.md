---
type: Requirement
title: NTIA Minimum Elements for an SBOM (2021)
description: Historical minimum elements baseline published by NTIA pursuant to Executive
  Order 14028.
category: requirement
tags:
- requirement
- us
- ntia
- sbom
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-06-30T00:00:00Z'
sources:
- id: ntia-sbom-elements
  resource: https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
  title: The Minimum Elements For a Software Bill of Materials (SBOM)
  author: National Telecommunications and Information Administration (NTIA)
  last_modified: '2021-07-12T00:00:00Z'
x-software-supply-chain:
  jurisdiction: US
  authority_level: guidance
  instrument_status: superseded
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

Published on July 12, 2021, pursuant to Section 8(e) of Executive Order 14028, the **NTIA Minimum Elements** defined the initial federal definition of an SBOM[^ntia-sbom-elements].

**Binding / contractual / guidance**: Non-binding historical guidance (superseded).

> [!NOTE]
> **Superseded Baseline**: This 2021 document has been formally updated and replaced by the [CISA 2026 Minimum Elements for an SBOM](cisa-minimum-elements-2026.md).

# Three Core Areas
The 2021 guidance structured SBOM expectations into three areas:
1. **Data Fields**: Supplier Name, Component Name, Version of the Component, Other Unique Identifiers, Dependency Relationship, Author of SBOM Data, and Timestamp.
2. **Automation Support**: Machine-readable formats including SPDX, CycloneDX, and SWID tags.
3. **Practices and Processes**: Frequency of generation, depth of dependencies, known unknowns, and accommodation of mistakes.

# Related concepts
- [CISA 2026 Minimum Elements](cisa-minimum-elements-2026.md)
- [EO 14028](../../law/united-states/eo-14028.md)

[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
