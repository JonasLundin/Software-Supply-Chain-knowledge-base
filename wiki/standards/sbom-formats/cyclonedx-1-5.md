---
type: Format
title: OWASP CycloneDX 1.5 Specification
description: Full-spectrum Bill of Materials standard providing advanced support for software, cloud services (SaaSBOM), operations (OBOM), and integrated VEX disclosures.
category: format
tags:
  - sbom
  - cyclonedx
  - saas-bom
  - vex
  - format
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
  - id: cyclonedx-specification
    resource: https://cyclonedx.org/specification/overview/
    title: OWASP CycloneDX Software Bill of Materials Standard (ECMA-424)
    author: OWASP Foundation / Ecma International
    last_modified: '2024-05-01T00:00:00Z'
  - id: ntia-sbom-elements
    resource: https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
    title: The Minimum Elements For a Software Bill of Materials (SBOM)
    author: National Telecommunications and Information Administration (NTIA)
    last_modified: '2021-07-12T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  provision: CycloneDX v1.5
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**OWASP CycloneDX 1.5** is a comprehensive, security-focused Bill of Materials specification designed for modern software supply chain management, operational transparency, and continuous risk assessment[^cyclonedx-specification]. Maintained by the OWASP Foundation, CycloneDX was built from inception to integrate seamlessly with automated DevSecOps pipelines and software security analysis tools.

CycloneDX 1.5 goes substantially beyond simple component inventories to standardize Software Bills of Materials (SBOM), Software-as-a-Service Bills of Materials (SaaSBOM), Hardware Bills of Materials (HBOM), Operations Bills of Materials (OBOM), Formulation (build lifecycle recipes), and native Vulnerability Exploitability eXchange (VEX) statements. It satisfies all baseline requirements set by the US NTIA Minimum Elements[^ntia-sbom-elements] and EU CRA technical documentation mandates.

```
+-------------------------------------------------------------+
|                     CycloneDX 1.5 BOM                       |
|  - bomFormat: "CycloneDX", specVersion: "1.5"               |
|  - serialNumber: urn:uuid:... , version: 1                  |
+-------------------------------------------------------------+
                               |
                               +-----------------------------+
                               |                             |
                               v                             v
+---------------------------------------------+  +---------------------------+
|                  metadata                   |  |        components         |
|  - timestamp, tools, authors                |  |  - root application       |
|  - root component (manufacture, supplier)   |  |  - libraries / modules    |
|  - licenses, properties                     |  |  - purl, cpe, hashes      |
+---------------------------------------------+  +---------------------------+
                               |                               |
                               v                               v
+---------------------------------------------+  +---------------------------+
|                dependencies                 |  |      vulnerabilities      |
|  - ref: "bom-ref-1"                         |  |  - CVE / GHSA ID          |
|  - dependsOn: ["bom-ref-2", "bom-ref-3"]    |  |  - analysis (VEX state)   |
+---------------------------------------------+  |  - affects: [bom-ref]     |
                                                 +---------------------------+
```

# Technical Scope / Normative Requirements

### Structural Top-Level Fields

A valid CycloneDX 1.5 document is structured around a rigorous JSON Schema or XML Schema definition:

| Element | Requirement | Description |
| :--- | :--- | :--- |
| `bomFormat` | Mandatory | Must be the string literal `"CycloneDX"`. |
| `specVersion` | Mandatory | Declares version string, e.g. `"1.5"`. |
| `serialNumber` | Recommended | Unique URI formatted as a UUID URN (`urn:uuid:3e671687-395b-41f5-a30f-a58921a69b79`). |
| `version` | Mandatory | Integer incremented whenever the BOM content is modified (starting at `1`). |
| `metadata` | Recommended | Contains supplier information, generation timestamp, generator tools, and root component. |
| `components` | Optional | Array of discrete software, hardware, or service components. |
| `services` | Optional | Endpoints, cloud APIs, data flows, and trust boundaries (SaaSBOM). |
| `dependencies` | Recommended | Complete directed graph of component relationships via unique `bom-ref` anchors. |
| `vulnerabilities`| Optional | Native VEX declarations specifying vulnerability impact and remediation. |
| `formulation` | Optional | Build workflows, tasks, environmental parameters, and build toolchains. |

### Component Identification & Evidence

Components within CycloneDX 1.5 feature rich identification and provenance properties:
- `type`: Explicit component classification: `application`, `framework`, `library`, `container`, `operating-system`, `device`, `firmware`, `file`.
- `name` and `version`: Basic package coordinates.
- `bom-ref`: Unique identifier within the BOM instance, allowing unambiguous cross-referencing in dependency trees and vulnerability tables.
- `purl`: Canonical Package URL format (e.g. `pkg:npm/lodash@4.17.21`).
- `cpe`: Common Platform Enumeration identifier (e.g. `cpe:2.3:a:lodash:lodash:4.17.21:*:*:*:*:*:*:*`).
- `hashes`: Cryptographic digests (SHA-256, SHA-512, BLAKE3).
- `evidence`: Empirical proof of identity, including file occurrences, callstack execution traces, and binary fingerprints.

### Dependency Graph Model

CycloneDX avoids ambiguity by separating component inventory from relational linkage:

```json
{
  "dependencies": [
    {
      "ref": "pkg:npm/express@4.18.2",
      "dependsOn": [
        "pkg:npm/body-parser@1.20.1",
        "pkg:npm/cookie@0.5.0",
        "pkg:npm/debug@2.6.9"
      ]
    }
  ]
}
```

# Applicability & Operational Impact

CycloneDX 1.5 is the de facto standard across cloud-native application security, container pipelines, and enterprise vulnerability management:

- **SecOps and Vulnerability Management**: Direct native ingestion into OWASP Dependency-Track, Trivy, Grype, and commercial ASPM platforms.
- **Microservices & SaaS Architecture**: Enables engineering organizations to produce SaaSBOMs documenting endpoint APIs, external third-party SaaS dependencies, and data classifications.
- **Enterprise Procurement**: Meets federal and industrial procurement criteria without requiring extraneous semantic web tooling.

# Practical Implementation

### Generating CycloneDX 1.5 via cdxgen and Syft

CycloneDX BOMs are generated dynamically during build pipelines:

```bash
# Using Anchore Syft for container images
syft packages docker.io/library/nginx:alpine -o cyclonedx-json=nginx-sbom.1.5.json

# Using CycloneDX CLI generator (cdxgen) for multi-language source repos
cdxgen -r -o sbom.cdx.json --spec-version 1.5
```

### Schema Validation via cyclonedx-cli

```bash
# Install CycloneDX CLI
npm install -g @cyclonedx/cyclonedx-cli

# Validate the generated document against the official 1.5 JSON schema
cyclonedx-cli validate --input-file sbom.cdx.json --spec-version 1.5
```

### Example CycloneDX 1.5 Fragment

```json
{
  "$schema": "http://cyclonedx.org/schema/bom-1.5.schema.json",
  "bomFormat": "CycloneDX",
  "specVersion": "1.5",
  "serialNumber": "urn:uuid:6b4d32e9-4e7a-4a4c-811c-2977d61245fa",
  "version": 1,
  "metadata": {
    "timestamp": "2026-09-27T08:45:00Z",
    "tools": [
      {
        "vendor": "CycloneDX",
        "name": "cdxgen",
        "version": "10.0.0"
      }
    ],
    "component": {
      "type": "application",
      "bom-ref": "acme-api-root",
      "name": "acme-api",
      "version": "3.4.1"
    }
  },
  "components": [
    {
      "type": "library",
      "bom-ref": "pkg:npm/debug@2.6.9",
      "name": "debug",
      "version": "2.6.9",
      "purl": "pkg:npm/debug@2.6.9",
      "hashes": [
        {
          "alg": "SHA-256",
          "content": "673cf2d0bbfd469abac63d2ce893bcdd1a62d37c770c793ff0e98ff7b711e646"
        }
      ],
      "licenses": [
        {
          "license": {
            "id": "MIT"
          }
        }
      ]
    }
  ],
  "dependencies": [
    {
      "ref": "acme-api-root",
      "dependsOn": [
        "pkg:npm/debug@2.6.9"
      ]
    }
  ]
}
```

# Dates and Transitions

- **June 2023**: CycloneDX 1.5 officially published by OWASP.
- **June 2024**: CycloneDX 1.6 ratified as Ecma International ECMA-424, adding CBOM and AIBOM capabilities.
- **2025–2027**: CycloneDX 1.5 remains heavily supported across all major open-source security tools as organizations upgrade to ECMA-424 (CycloneDX 1.6).

# Related concepts

- [OWASP CycloneDX 1.6 (ECMA-424)](cyclonedx-1-6.md)
- [CycloneDX Native VEX](../vex/cyclonedx-vex.md)
- [SPDX 2.3 (ISO/IEC 5962:2021)](spdx-2-3.md)
- [Package URL Specification](../../glossary/package-url.md)
- [NTIA Minimum Elements](../../requirements/united-states/ntia-minimum-elements.md)

[^cyclonedx-specification]: OWASP Foundation / Ecma International, OWASP CycloneDX Software Bill of Materials Standard (ECMA-424), https://cyclonedx.org/specification/overview/
[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
