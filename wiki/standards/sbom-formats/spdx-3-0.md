---
type: Format
title: SPDX 3.0 Specification
description: Next-generation modular graph-based specification for software, AI models, hardware, datasets, security attestations, and VEX statements.
category: format
tags:
  - sbom
  - spdx
  - spdx-3-0
  - format
  - ai-bom
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
  provision: SPDX 3.0.1
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**SPDX 3.0** is a major architectural redesign of the Software Package Data Exchange specification, transforming SPDX from a document-centric flat inventory model into a modular, graph-oriented metadata framework[^spdx-iso-5962]. Published by the Linux Foundation, SPDX 3.0 expands beyond traditional open-source software licensing and packaging to encompass artificial intelligence (AI) models, training datasets, hardware systems, build provenance, and native Vulnerability Exploitability eXchange (VEX) statements.

SPDX 3.0 fulfills and exceeds regulatory mandates such as the US NTIA Minimum Elements[^ntia-sbom-elements] and the EU Cyber Resilience Act by decoupling domain-specific concerns into independent, interoperable profiles built upon an extensible core object model.

```
+---------------------------------------------------------------+
|                      SPDX 3.0 Core Model                      |
|  - Element (Identity, CreationInfo, Integrity)                |
|  - Relationship (From Element -> To Element)                  |
|  - Bundle / SpdxDocument                                      |
+---------------------------------------------------------------+
         |                     |                     |
         v                     v                     v
+------------------+  +------------------+  +-------------------+
| Software Profile |  | Security Profile |  |    AI Profile     |
| - Package        |  | - Vulnerability  |  | - AI Model        |
| - File           |  | - VexAssessment  |  | - Dataset         |
| - Snippet        |  | - Justification  |  | - Training Lineage|
+------------------+  +------------------+  +-------------------+
         |                     |                     |
         +---------------------+---------------------+
                               |
                               v
+---------------------------------------------------------------+
|                      Build & Licensing                        |
|  - Build Profile (Invocation, Inputs, Outputs, Config)        |
|  - SimpleLicensing Profile (SPDX license expressions)         |
+---------------------------------------------------------------+
```

# Technical Scope / Normative Requirements

### Architectural Foundations: Core Model

In SPDX 3.0, every entity is an **Element**. All elements inherit a set of universal core properties:
- `@id`: Globally unique IRI (Internationalized Resource Identifier) identifying the element.
- `@type`: Qualified class name (e.g. `software_Package`, `security_Vulnerability`).
- `creationInfo`: Author, timestamp, toolchain identity, and license governance for that specific element.
- `extension`: Extensible key-value metadata mechanism for domain-specific annotations.

Elements are connected through first-class **Relationships**, permitting multi-directional, typed directed acyclic graphs (DAGs) rather than rigid hierarchical tree structures.

### Modular Profile Architecture

SPDX 3.0 structures its domain capabilities into discrete profiles:

| Profile | Namespace | Target Domain & Key Classes |
| :--- | :--- | :--- |
| **Core** | `core` | `Element`, `Bundle`, `SpdxDocument`, `Relationship`, `Annotation`, `ExternalMap`. |
| **Software** | `software` | `Package`, `File`, `Snippet`, `SoftwareArtifact`, `SoftwarePurpose`. |
| **Security (VEX)** | `security` | `Vulnerability`, `VexAssessmentRelationship` (`affects`, `doesNotAffect`, `fixedIn`, `underInvestigation`). |
| **Build (Provenance)** | `build` | `Build`, `BuildTool`, `EnvironmentVariable`, build inputs and outputs (aligning with SLSA). |
| **AI / ML** | `ai` | `AIPackage`, `AIEnergyConsumption`, `AIEthicMetric`, model parameters, hyperparameters. |
| **Dataset** | `dataset` | Training datasets, sensor captures, dataset governance, data licensing. |
| **Licensing** | `simplelicensing` | `AnyLicenseInfo`, `CustomLicense`, license expressions (e.g. `Apache-2.0 OR MIT`). |

### Serialization Formats

SPDX 3.0 uses **JSON-LD** (JavaScript Object Notation for Linked Data) as its canonical syntax, grounding every field in a formal semantic ontology (`https://spdx.org/rdf/3.0.0/spdx-context.jsonld`). Alternate serializations include Turtle (RDF), JSON without linked data annotations, and YAML.

# Applicability & Operational Impact

The introduction of SPDX 3.0 has profound implications for enterprise security and compliance operations:

- **Unified Asset Inventory**: Organizations can describe hybrid systems containing proprietary firmware, open-source libraries, container base layers, and machine learning models within a single unified graph.
- **In-Band VEX Coordination**: Security teams can attach real-time exploitability assessments (`doesNotAffect` with justifications) directly to the software graph without generating disconnected advisory files.
- **Build Reproducibility & Provenance**: Integrates directly with build systems to capture the exact build invocation and input hashes, reducing the gap between SBOMs and SLSA provenance.

# Practical Implementation

### Sample SPDX 3.0 JSON-LD Object

The following example illustrates a minimal SPDX 3.0 document combining the Software and Security profiles:

```json
{
  "@context": "https://spdx.org/rdf/3.0.0/spdx-context.jsonld",
  "@graph": [
    {
      "@type": "SpdxDocument",
      "@id": "https://spdx.acme.com/doc/release-42",
      "creationInfo": {
        "specVersion": "3.0.0",
        "created": "2026-09-27T08:30:00Z",
        "createdBy": ["https://spdx.acme.com/agents/ci-pipeline"]
      },
      "rootElement": ["https://spdx.acme.com/pkg/payment-gateway-2.0.0"]
    },
    {
      "@type": "software_Package",
      "@id": "https://spdx.acme.com/pkg/payment-gateway-2.0.0",
      "name": "payment-gateway",
      "packageVersion": "2.0.0",
      "packageSupplier": "Organization: Acme Financial Services",
      "downloadLocation": "https://internal.repo/pkg/payment-gateway.tgz",
      "externalRef": [
        {
          "externalRefType": "purl",
          "locator": "pkg:generic/payment-gateway@2.0.0"
        }
      ]
    },
    {
      "@type": "security_Vulnerability",
      "@id": "https://spdx.acme.com/vuln/CVE-2024-99999",
      "externalIdentifier": "CVE-2024-99999"
    },
    {
      "@type": "security_VexAssessmentRelationship",
      "@id": "https://spdx.acme.com/rel/vex-assessment-1",
      "from": "https://spdx.acme.com/vuln/CVE-2024-99999",
      "to": ["https://spdx.acme.com/pkg/payment-gateway-2.0.0"],
      "relationshipType": "doesNotAffect",
      "security_vexJustification": "vulnerableCodeNotPresent",
      "security_impactStatement": "The vulnerable sub-routine is eliminated during tree-shaking compilation."
    }
  ]
}
```

### Tooling Integration and Verification

Tooling supporting SPDX 3.0 leverages the `spdx3-tools` Python suite:

```bash
# Validate SPDX 3.0 JSON-LD against SHACL shapes and JSON schema
spdx3-validate --file spdx3-manifest.jsonld --profile software security
```

# Dates and Transitions

- **April 2024**: SPDX 3.0.0 officially released by the Linux Foundation.
- **Mid-2024 to 2026**: Transition period. Tooling vendors progressively add dual support for SPDX 2.3 and SPDX 3.0.
- **December 2027**: Cyber Resilience Act full compliance deadline. SPDX 3.0 serves as a premier format capable of fulfilling CRA technical documentation requirements.

# Related concepts

- [SPDX 2.3 (ISO/IEC 5962:2021)](spdx-2-3.md)
- [OWASP CycloneDX 1.6 (ECMA-424)](cyclonedx-1-6.md)
- [OpenVEX Specification](../vex/openvex.md)
- [CRA SBOM Mandate](../../requirements/cra-sbom-mandate.md)
- [NTIA Minimum Elements](../../requirements/ntia-minimum-elements.md)

[^spdx-iso-5962]: Linux Foundation / ISO/IEC JTC 1, Software Package Data Exchange (SPDX) Specification (ISO/IEC 5962:2021), https://spdx.dev/specifications/
[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
