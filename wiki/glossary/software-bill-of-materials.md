---
type: Glossary
title: Software Bill of Materials (SBOM)
description: A formal, machine-readable inventory of software components, dependencies,
  metadata, and hierarchical relationships.
category: glossary
tags:
- supply-chain
- glossary
- software-bill-of-materials
status: draft
generated:
  by: agent:antigravity
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: ntia-sbom-elements
  resource: https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
  title: The Minimum Elements For a Software Bill of Materials (SBOM)
  author: National Telecommunications and Information Administration (NTIA)
  last_modified: '2021-07-12T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: guidance
  instrument_status: in_force
  provision: Software Bill of Materials (SBOM)
  checked_at: '2026-09-27T00:00:00Z'
---

# Definition

A **Software Bill of Materials (SBOM)** is a formal, machine-readable inventory of software components, dependencies, metadata, and hierarchical relationships comprising a software application or system[^ntia-sbom-elements].

# Operational Importance

Modern software products incorporate hundreds of open-source and proprietary third-party libraries. An SBOM provides foundational transparency across the software supply chain, enabling organizations to rapidly locate vulnerable dependencies (e.g., during zero-day disclosure events like Log4j), track software license obligations, verify regulatory compliance under the EU Cyber Resilience Act, and establish provenance across the continuous integration lifecycle. Standard formats include SPDX, CycloneDX, and SWID.

# Related concepts
- [Glossary Index](index.md)
- [SPDX 3.0 Standard](../standards/sbom-formats/spdx-3-0.md)
- [CycloneDX Standard](../standards/sbom-formats/cyclonedx-1-7.md)

[^ntia-sbom-elements]: National Telecommunications and Information Administration, The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
