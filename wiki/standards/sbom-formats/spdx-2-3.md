---
type: Format
title: SPDX 2.3 (ISO/IEC 5962:2021)
description: International standard format (ISO/IEC 5962:2021) for exchanging software package data, component provenance, licensing metadata, and security references.
category: format
tags:
  - sbom
  - spdx
  - iso-iec-5962
  - format
  - open-source
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
  - id: spdx-iso-5962
    resource: https://spdx.dev/specifications/
    title: Software Package Data Exchange (SPDX) Specification (ISO/IEC 5962:2021)
    author: Linux Foundation / ISO/IEC JTC 1
    last_modified: '2021-09-01T00:00:00Z'
  - id: ntia-sbom-elements
    resource: https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
    title: The Minimum Elements For a Software Bill of Materials (SBOM)
    author: National Telecommunications and Information Administration (NTIA)
    last_modified: '2021-07-12T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  provision: ISO/IEC 5962:2021
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**SPDX 2.3** is an open standard and de jure international standard (ISO/IEC 5962:2021) designed to express the components, licenses, copyrights, security references, and provenance of software packages[^spdx-iso-5962]. Maintained by the Linux Foundation's SPDX Project and recognized by international standards bodies, SPDX 2.3 represents the mature culmination of the SPDX 2.x specification line.

SPDX 2.3 provides a structured, machine-readable data model that directly addresses the regulatory requirements for Software Bills of Materials (SBOMs), including the United States NTIA Minimum Elements[^ntia-sbom-elements] mandated under Executive Order 14028 and European requirements under the Cyber Resilience Act.

```
+-------------------------------------------------------------+
|                      SPDX 2.3 Document                      |
|  - Document Creation Info (ID, Creators, Timestamp, CC0)    |
|  - External Document References                             |
+-------------------------------------------------------------+
                               | DESCRIBES
                               v
+-------------------------------------------------------------+
|                      SPDX Package                           |
|  - Name, Version, Supplier, Originator                      |
|  - Download Location, Homepage, Verification Code           |
|  - Checksums (SHA-256, SHA-1), External Refs (purl, CPE)   |
|  - Concluded License, Declared License, Copyright Text      |
+-------------------------------------------------------------+
          |                                      |
          | CONTAINS                             | DEPENDS_ON
          v                                      v
+-----------------------+              +----------------------+
|       SPDX File       |              |  Dependent Package   |
|  - File Name          |              |  (Sub-dependency)    |
|  - Checksums          |              +----------------------+
|  - License / Copyright|
+-----------------------+
```

# Technical Scope / Normative Requirements

The SPDX 2.3 specification organizes metadata into discrete sections connected by formal directional relationships.

### Document Creation Information

Every SPDX 2.3 document begins with mandatory header metadata establishing document identity, governance, and immutability:

| Field | Mandatory | Type / Constraint | Description |
| :--- | :--- | :--- | :--- |
| `spdxVersion` | Yes | String (`SPDX-2.3`) | The version of the specification used. |
| `dataLicense` | Yes | String (`CC0-1.0`) | Explicit license under which the SPDX document itself is published. |
| `SPDXID` | Yes | String (`SPDXRef-DOCUMENT`) | Unique identifier for the document within its namespace. |
| `name` | Yes | String | Human-readable document name. |
| `documentNamespace` | Yes | URI | Globally unique URI identifying the document instance (often a UUID or HTTPS URI). |
| `creationInfo.creators` | Yes | List of Strings | Entity generating the document: `Person:`, `Organization:`, or `Tool:`. |
| `creationInfo.created` | Yes | ISO 8601 UTC timestamp | Exact timestamp of document completion (`YYYY-MM-DDTHH:MM:SSZ`). |

### Package Information

A package represents any discrete piece of software (application, library, container image, or operating system package):

- **Identity**: `PackageName`, `PackageVersion`, `PackageFileName`, `SPDXID` (e.g. `SPDXRef-Package-log4j-core`).
- **Supplier & Originator**: `PackageSupplier` (must declare `Person: <name>`, `Organization: <name>`, or `NOASSERTION`), `PackageOriginator`.
- **Integrity**: `PackageChecksum` supporting algorithms including SHA-256, SHA-1, SHA-512, MD5; `PackageVerificationCode` computed across constituent files.
- **External Identifiers**: `externalRefs` supporting `PACKAGE-MANAGER` with `purl` (Package URL) and `SECURITY` with `cpe22Type` / `cpe23Type`.
- **Licensing & Legal**: `PackageLicenseConcluded`, `PackageLicenseDeclared`, `PackageLicenseComments`, `PackageCopyrightText`.

### Relationships

SPDX 2.3 represents dependencies through explicit relationship assertions:

$$\text{Element}_{\text{source}} \xrightarrow{\quad\text{RelationshipType}\quad} \text{Element}_{\text{target}}$$

Standard relationship types include:
- `DESCRIBES`: The document describes a specific primary package or artifact.
- `DEPENDS_ON`: The source package runtime depends on the target package.
- `CONTAINS`: The package physically bundles another package or file.
- `DYNAMIC_LINK` / `STATIC_LINK`: Explains linking mechanics between modules.
- `PREREQUISITE_FOR`: Build-time or deployment dependency.

### Supported Serializations

SPDX 2.3 formally standardizes five interchangeable concrete serializations:
1. **JSON** (`.spdx.json`): Modern default serialization for automated tooling.
2. **YAML** (`.spdx.yaml`): Human-readable structured format.
3. **Tag:Value** (`.spdx`): Traditional line-delimited format used in legacy systems.
4. **XML** (`.spdx.xml`): Enterprise standard interchange.
5. **RDF/XML** (`.spdx.rdf`): Semantic web graph representation.

# Applicability & Operational Impact

SPDX 2.3 is applicable across the entire software delivery lifecycle, with specific operational impact on key supply chain roles:

- **Software Producers**: Used to satisfy customer contractual mandates and federal procurement criteria (e.g. US OMB M-22-18 and NTIA minimum elements).
- **Open-Source Stewards & Maintainers**: Enables automated licensing compliance and clear attribution across complex multi-license dependency trees.
- **Software Consumers & Enterprise Buyers**: Ingested into vulnerability management scanners and software asset management (SAM) systems.
- **Tooling Ecosystem**: Broadly supported by build scanners (Syft, Trivy, Microsoft sbom-tool, cve-bin-tool) and enterprise platforms (Dependency-Track, Snyk, Black Duck).

# Practical Implementation

### Automated Generation via CLI

In continuous integration pipelines, tools such as Anchore Syft generate valid SPDX 2.3 JSON documents directly from repository sources or container images:

```bash
# Generate SPDX 2.3 JSON from a compiled container image
syft packages alpine:latest -o spdx-json=sbom-alpine.spdx.json

# Generate SPDX 2.3 JSON from a source directory or lockfile
syft packages dir:. -o spdx-json=sbom-project.spdx.json
```

### Validating SPDX 2.3 Documents

Documents can be verified against the official JSON schema using the official Python SPDX tools:

```bash
# Install the official SPDX validator
pip install spdx-tools

# Validate document syntax and semantic rules
pyspdxtools -i sbom-project.spdx.json
```

### Example SPDX 2.3 JSON Fragment

```json
{
  "spdxVersion": "SPDX-2.3",
  "dataLicense": "CC0-1.0",
  "SPDXID": "SPDXRef-DOCUMENT",
  "name": "acme-service-sbom",
  "documentNamespace": "https://spdx.acme.com/spdxdocs/acme-service-2.1.0-4fa3b1e",
  "creationInfo": {
    "creators": [
      "Organization: Acme Security Corp",
      "Tool: Syft-0.105.0"
    ],
    "created": "2026-09-27T08:00:00Z"
  },
  "packages": [
    {
      "name": "express",
      "SPDXID": "SPDXRef-Package-npm-express-4.18.2",
      "versionInfo": "4.18.2",
      "supplier": "Organization: OpenJS Foundation",
      "downloadLocation": "https://registry.npmjs.org/express/-/express-4.18.2.tgz",
      "filesAnalyzed": false,
      "checksums": [
        {
          "algorithm": "SHA256",
          "checksumValue": "4865fb6660fbdbbe3f8f107f9cff98bfbe44c5b3c5e8c15eb18f2d7bf8e5c51f"
        }
      ],
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "copyrightText": "Copyright (c) 2009-2014 TJ Holowaychuk <tj@vision-media.ca>",
      "externalRefs": [
        {
          "referenceCategory": "PACKAGE-MANAGER",
          "referenceType": "purl",
          "referenceLocator": "pkg:npm/express@4.18.2"
        }
      ]
    }
  ],
  "relationships": [
    {
      "spdxElementId": "SPDXRef-DOCUMENT",
      "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-npm-express-4.18.2"
    }
  ]
}
```

# Dates and Transitions

- **September 2021**: SPDX 2.2 adopted as ISO/IEC 5962:2021.
- **November 2022**: SPDX 2.3 released, introducing improved external references (`purl`), security advisory fields, and expanded relationship taxonomies.
- **April 2024**: SPDX 3.0 launched, providing a modular graph architecture. SPDX 2.3 remains the operational workhorse for enterprise compliance through 2026–2027 while tooling transitions to SPDX 3.0.

# Related concepts

- [SPDX 3.0 Specification](spdx-3-0.md)
- [OWASP CycloneDX 1.6 (ECMA-424)](cyclonedx-1-6.md)
- [Package URL Specification](../../glossary/package-url.md)
- [NTIA Minimum Elements](../../requirements/united-states/ntia-minimum-elements.md)
- [SBOM Generation in Build Pipelines](../../procedures/sbom-generation-at-build.md)

[^spdx-iso-5962]: Linux Foundation / ISO/IEC JTC 1, Software Package Data Exchange (SPDX) Specification (ISO/IEC 5962:2021), https://spdx.dev/specifications/
[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
