---
type: Jurisdiction
title: 'Jurisdiction: Germany (BSI)'
description: German Federal Office for Information Security (BSI) technical standards
  and procurement guidelines for cyber resilience and SBOMs.
category: jurisdiction
tags:
- supply-chain
- jurisdiction
- germany
- bsi
- tr-03183
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: ntia-sbom-elements
  resource: https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
  title: The Minimum Elements For a Software Bill of Materials (SBOM)
  author: National Telecommunications and Information Administration (NTIA)
  last_modified: '2021-07-12T00:00:00Z'
x-software-supply-chain:
  jurisdiction: Germany (BSI)
  authority_level: guidance
  instrument_status: in_force
  provision: BSI TR-03183
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Germany**, through the Federal Office for Information Security (**BSI** - *Bundesamt für Sicherheit in der Informationstechnik*), provides authoritative national technical guidelines aligning domestic procurement with European regulations[^ntia-sbom-elements].

# Technical Guideline BSI TR-03183

The landmark **BSI TR-03183** (*Cyber Resilience Requirements for Manufacturers and Products*) serves as the national technical operationalization for software supply chain transparency:
- **Part 1 - SBOM Requirements**: Specifies concrete requirements for machine-readable SBOM formats (CycloneDX and SPDX), requiring inclusion of package hashes, direct and transitive dependencies, and purl identifiers.
- **Part 2 - Vulnerability Handling & VEX**: Prescribes automated vulnerability status communication via CSAF 2.0 VEX profiles.
- **Government Procurement Integration**: Public tenders across German federal and state administrations reference TR-03183 as a mandatory technical compliance baseline.

# Related concepts
- [European Union](european-union.md)
- [CycloneDX 1.6](../standards/sbom-formats/cyclonedx-1-6.md)
- [CSAF 2.0 VEX Profile](../standards/vex/csaf-vex.md)

[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
