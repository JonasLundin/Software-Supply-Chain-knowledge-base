---
type: Requirement
title: NTIA Minimum Elements for a Software Bill of Materials (SBOM)
description: The foundational United States federal baseline defining data fields,
  operational considerations, and support practices for SBOMs.
category: requirement
tags:
- supply-chain
- requirement
- ntia
- eo-14028
- sbom-elements
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
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  provision: NTIA Report (July 12, 2021) pursuant to EO 14028 Section 2(e)
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **Minimum Elements for a Software Bill of Materials (SBOM)** is the landmark technical standard published on July 12, 2021, by the United States National Telecommunications and Information Administration (**NTIA**) pursuant to Executive Order 14028 on *Improving the Nation's Cybersecurity*[^ntia-sbom-elements].

The NTIA report established the universal global definition of what constitutes an acceptable, functional SBOM across enterprise software procurement and regulatory compliance.

# The Three Pillars of the NTIA Specification

```
+-------------------------------------------------------------------+
|                     NTIA MINIMUM ELEMENTS (2021)                  |
+-------------------------------------------------------------------+
| 1. DATA FIELDS: Baseline component identity & pedigree metadata   |
+-------------------------------------------------------------------+
| 2. OPERATIONAL CONSIDERATIONS: Frequency, depth, delivery, access |
+-------------------------------------------------------------------+
| 3. SUPPORT PRACTICES: Automation, tooling integration, licensing  |
+-------------------------------------------------------------------+
```

# Pillar 1: The 7 Mandatory Baseline Data Fields

To satisfy NTIA minimum elements, an SBOM must record seven core attributes for every documented component:

| Field Name | Description & Specification | Example Value |
| :--- | :--- | :--- |
| **Supplier Name** | The entity that creates, defines, and identifies the component. | `Apache Software Foundation` |
| **Component Name** | The designation assigned to the software unit by the supplier. | `log4j-core` |
| **Version of Component** | The identifier specifying the exact release or build of the component. | `2.17.1` |
| **Other Unique Identifiers** | Globally unique package identifiers, such as Package URL (purl) or CPE. | `pkg:maven/org.apache.logging.log4j/log4j-core@2.17.1` |
| **Dependency Relationship** | Characterizes the relationship between software elements (`CONTAINS`, `DEPENDS_ON`). | `Direct dependency of Product X` |
| **Author of SBOM Data** | The person or organization that created the SBOM metadata. | `Syft Build Engine v1.0.0` |
| **Timestamp** | The record of the exact date and time the SBOM data was assembled. | `2026-03-15T08:30:00Z` |

# Pillar 2: Operational Considerations

- **Frequency of Generation**: A new SBOM must be generated whenever a software component is modified, updated, or re-released in a new build.
- **Depth**: An SBOM must cover all top-level direct dependencies, with a recommended goal of documenting complete transitive dependencies recursively down the tree.
- **Delivery & Access**: SBOMs must be provided in a timely manner alongside the software product or hosted securely via authenticated repositories, access control portals, or well-known endpoints.

# Pillar 3: Support Practices

- **Accepted Data Formats**: Only machine-readable, open, and standardized formats are compliant:
  1. **SPDX** (ISO/IEC 5962)
  2. **CycloneDX** (ECMA-424)
- **Automation Support**: Tooling must support automated generation in continuous integration/continuous delivery (CI/CD) pipelines and automated ingestion into vulnerability scanners.

# Related concepts
- [SPDX 2.3 Standard](../standards/sbom-formats/spdx-2-3.md)
- [CycloneDX 1.6 Standard](../standards/sbom-formats/cyclonedx-1-6.md)
- [CRA Component Inventory Mandate](cra-sbom-mandate.md)
- [NIST Secure Software Development Framework (SSDF)](ssdf-nist-sp-800-218.md)

[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
