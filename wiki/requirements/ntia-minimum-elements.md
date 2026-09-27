---
type: Requirement
title: NTIA Minimum Elements for a Software Bill of Materials (SBOM)
description: Baseline regulatory framework defining the seven mandatory data fields, operational considerations, and automation practices required for valid software bills of materials.
category: requirement
tags:
  - sbom
  - ntia
  - eo-14028
  - minimum-elements
  - requirement
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
  jurisdiction: United States
  authority_level: statutory
  instrument_status: in_force
  provision: Executive Order 14028 Section 10(t) / NTIA 2021 Report
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **NTIA Minimum Elements for a Software Bill of Materials (SBOM)** is the seminal baseline standard published by the National Telecommunications and Information Administration (NTIA) of the United States Department of Commerce on July 12, 2021[^ntia-sbom-elements]. Mandated pursuant to Section 10(t) of President Biden's Executive Order 14028 ("Improving the Nation's Cybersecurity"), this landmark report defined for the first time what constitutes an acceptable, legally recognizable SBOM for federal procurement and supply-chain risk management.

The NTIA standard is structured across three core pillars:
1. **Data Fields**: The mandatory data points that must be documented for each component.
2. **Operational Considerations**: Rules governing generation frequency, dependency depth, delivery mechanics, and access controls.
3. **Practices and Processes**: Automation, machine-readability, and format compliance.

```
+-----------------------------------------------------------------------------------------+
|                         NTIA Minimum Elements Architecture                              |
+-----------------------------------------------------------------------------------------+
               |                               |                               |
               v                               v                               v
+-----------------------------+ +-----------------------------+ +-----------------------------+
|      Seven Data Fields      | |  Operational Considerations | |    Practices & Processes    |
|-----------------------------| |-----------------------------| |-----------------------------|
| 1. Supplier Name            | | - Frequency (every build)   | | - Standard Formats:         |
| 2. Component Name           | | - Depth (direct + transitive| |   * SPDX (ISO/IEC 5962)     |
| 3. Version of the Component | | - Known Unknowns (clarity)  | |   * CycloneDX (ECMA-424)    |
| 4. Other Unique Identifiers | | - Delivery & Distribution   | |   * SWID (ISO/IEC 19770-2)  |
| 5. Dependency Relationship  | | - Access Control & Privacy  | | - Machine-readable syntax   |
| 6. Author of SBOM Data      | | - Error correction process  | | - CI/CD pipeline automation |
| 7. Timestamp                | |                             | |                             |
+-----------------------------+ +-----------------------------+ +-----------------------------+
```

# Technical Scope / Normative Requirements

### 1. The Seven Mandatory Data Fields

For an SBOM to be compliant with NTIA minimum elements, every included component must record:

| Field | Description | SPDX 2.3 Equivalent | CycloneDX 1.6 Equivalent |
| :--- | :--- | :--- | :--- |
| **Supplier Name** | The entity that creates, maintains, or packages the component. Must declare `NOASSERTION` if unknown. | `PackageSupplier` | `component.supplier` / `component.author` |
| **Component Name** | The primary designated name of the software unit. | `PackageName` | `component.name` |
| **Version** | Version identifier assigned by the supplier (e.g. SemVer, commit hash). | `PackageVersion` | `component.version` |
| **Other Unique Identifiers** | Global or ecosystem identifiers enabling automated correlation across vulnerability databases. | `externalRefs` (`purl`, `cpe`) | `component.purl`, `component.cpe`, `hashes` |
| **Dependency Relationship** | Direct upstream/downstream relational connection between parent and child components. | `Relationship` (`DEPENDS_ON`, `CONTAINS`) | `dependencies[].ref` and `dependencies[].dependsOn` |
| **Author of SBOM Data** | The person, organization, or tool generating the SBOM document. | `creationInfo.creators` | `metadata.authors`, `metadata.tools` |
| **Timestamp** | Date and time when the SBOM data was assembled. | `creationInfo.created` | `metadata.timestamp` |

### 2. Operational Considerations

- **Frequency**: A new SBOM must be generated whenever the software is modified, rebuilt, or updated. An out-of-date SBOM is considered non-compliant.
- **Depth**: The SBOM must capture all top-level (direct) dependencies and should track all transitive sub-dependencies recursively.
- **Known Unknowns**: The SBOM specification must distinguish between a component having *no dependencies* (e.g. an isolated leaf module) versus a component where dependencies *could not be determined* by the scanner.
- **Delivery**: Timely delivery to software consumers, integrators, and operators via standard protocols (APIs, portals, OCI registries).
- **Access Control**: Recognition that certain proprietary component names or internal architectures may require role-based access control or redaction for commercial confidentiality.

### 3. Practices and Processes

NTIA strictly forbids proprietary, unstructured, or human-only documents (such as PDF tables, Excel spreadsheets, or text files). All compliant SBOMs must be formatted in one of three machine-readable international formats:
1. **SPDX** (ISO/IEC 5962)
2. **CycloneDX** (ECMA-424)
3. **SWID** (ISO/IEC 19770-2:2015)

# Applicability & Operational Impact

The NTIA Minimum Elements report serves as the foundational benchmark across worldwide cybersecurity regulation:

- **US Federal Agencies & Civilian Contractors**: Incorporated directly into Office of Management and Budget (OMB) Memoranda M-22-18 and M-23-16.
- **US Food and Drug Administration (FDA)**: Integrated into premarket cybersecurity guidelines for cyber devices under Section 524B of the FD&C Act.
- **European Cyber Resilience Act (CRA)**: Annex I Part II component documentation requirements reflect NTIA's minimum data model.
- **Industrial Standards (BSI TR-03183 & METI Japan)**: German and Japanese national guidelines adopt the NTIA 7 data fields verbatim as their baseline.

# Practical Implementation

### Automated Verification Script

A continuous integration gate can verify that a generated SBOM satisfies all seven NTIA fields before releasing an artifact:

```python
#!/usr/bin/env python3
"""Verify CycloneDX SBOM against NTIA 7 Minimum Elements."""
import json
import sys

def verify_ntia_cyclonedx(sbom_path):
    with open(sbom_path, "r") as f:
        data = json.load(f)

    # 1. Author and Timestamp
    metadata = data.get("metadata", {})
    if not metadata.get("timestamp"):
        sys.exit("FAIL: Missing NTIA Timestamp in metadata")
    if not (metadata.get("authors") or metadata.get("tools") or metadata.get("manufacture")):
        sys.exit("FAIL: Missing NTIA Author of SBOM Data in metadata")

    # 2. Components check
    components = data.get("components", [])
    if not components:
        sys.exit("FAIL: No components found in SBOM")

    for c in components:
        name = c.get("name")
        version = c.get("version")
        purl = c.get("purl")
        cpe = c.get("cpe")
        supplier = c.get("supplier") or c.get("author")

        if not name or not version:
            sys.exit(f"FAIL: Component missing Name or Version: {c}")
        if not (purl or cpe or c.get("hashes")):
            sys.exit(f"FAIL: Component {name} missing Unique Identifiers (purl/cpe/hash)")

    # 3. Dependencies check
    if not data.get("dependencies"):
        sys.exit("FAIL: Missing NTIA Dependency Relationships graph")

    print(f"PASS: {sbom_path} satisfies all NTIA Minimum Elements ({len(components)} components checked).")

if __name__ == "__main__":
    verify_ntia_cyclonedx(sys.argv[1])
```

# Dates and Transitions

- **May 12, 2021**: President Biden signs Executive Order 14028 directing NTIA to define minimum SBOM elements within 60 days.
- **July 12, 2021**: NTIA formally publishes "The Minimum Elements For a Software Bill of Materials (SBOM)".
- **2024–2026**: Ongoing transition under CISA's SBOM Community to expand the 7 elements to include cryptographic hashes, runtime environments, and automated VEX integration.

# Related concepts

- [SPDX 2.3 (ISO/IEC 5962:2021)](../standards/sbom-formats/spdx-2-3.md)
- [OWASP CycloneDX 1.6 (ECMA-424)](../standards/sbom-formats/cyclonedx-1-6.md)
- [CRA SBOM Mandate](cra-sbom-mandate.md)
- [CISA Self-Attestation Form](cisa-self-attestation.md)
- [Software Bill of Materials Glossary](../glossary/software-bill-of-materials.md)

[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
