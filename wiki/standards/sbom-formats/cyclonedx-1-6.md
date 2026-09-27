---
type: Format
title: OWASP CycloneDX 1.6 Specification (ECMA-424)
description: Ecma International standard (ECMA-424) introducing Cryptographic Bill of Materials (CBOM), AI model cards, and CycloneDX Attestations (CDXA).
category: format
tags:
  - sbom
  - cyclonedx
  - ecma-424
  - cbom
  - ai-bom
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
  provision: ECMA-424 / CycloneDX 1.6
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**OWASP CycloneDX 1.6** is the flagship release of the CycloneDX standard, formally recognized as an international standard through its ratification as **ECMA-424** by Ecma International in June 2024[^cyclonedx-specification]. CycloneDX 1.6 extends the bill of materials paradigm to address emerging security frontiers, including Cryptographic Asset Inventories (CBOM) for post-quantum cryptographic transitions, Artificial Intelligence and Machine Learning model transparency (AIBOM), and native Attestations (CDXA).

CycloneDX 1.6 establishes a direct technical pathway for fulfilling the requirements of the EU Cyber Resilience Act, US federal software procurement mandates[^ntia-sbom-elements], and NIST SP 800-218 (SSDF) guidelines within a single, schema-validated file.

```
+-------------------------------------------------------------+
|               CycloneDX 1.6 (ECMA-424) Standard             |
+-------------------------------------------------------------+
   |                  |                  |                 |
   v                  v                  v                 v
+-------------+  +--------------+  +--------------+  +---------------+
|  Software   |  | Cryptography |  |  AI / Model  |  | Attestations  |
|    (SBOM)   |  |    (CBOM)    |  |   (AIBOM)    |  |    (CDXA)     |
|-------------|  |--------------|  |--------------|  |---------------|
| Application |  | Algorithms   |  | Model Cards  |  | Claims        |
| Libraries   |  | Key sizes    |  | Parameters   |  | Evidence      |
| PURL / CPE  |  | Protocols    |  | Datasets     |  | Signatures    |
| Dependencies|  | PQC Readiness|  | Governance   |  | Counterclaims |
+-------------+  +--------------+  +--------------+  +---------------+
```

# Technical Scope / Normative Requirements

CycloneDX 1.6 introduces major structural additions to the specification schema:

### 1. Cryptographic Bill of Materials (CBOM)

Under the `declarations.cryptography` object, CycloneDX 1.6 allows precise inventorying of cryptographic assets:
- **Algorithms**: Identifies primitives (e.g. `AES-GCM`, `RSA-PSS`, `ML-KEM`, `Dilithium`), operational parameters, key lengths, and security levels in bits.
- **Post-Quantum Cryptography (PQC) Readiness**: Attributes designating classical vs quantum-resistant algorithms, facilitating compliance with White House NSM-10 and NIST PQC migration timetables.
- **Certificates & Keys**: X.509 certificate chains, key life-cycle states, validity spans, and hardware security module (HSM) bindings.
- **Protocol Instances**: TLS, SSH, IPsec protocol configurations and cipher suites.

### 2. Artificial Intelligence / Machine Learning Bill of Materials (AIBOM)

CycloneDX 1.6 incorporates formal model cards directly under component types `machine-learning-model`:
- **Model Parameters**: Architecture family (transformer, diffusion, CNN), parameter counts, quantization levels (e.g. `Q4_K_M`).
- **Data Lineage**: Training datasets, validation datasets, preprocessing pipelines, and governance metadata.
- **Environmental & Performance Metrics**: Energy consumed during training, CO2 footprint, precision, recall, and safety evaluations.

### 3. CycloneDX Attestations (CDXA)

The `declarations.assessments` and `attestations` schema models allow organizations to assert compliance claims and link them directly to cryptographically verifiable evidence:
- **Claims**: Pre-defined or custom claims against standards (e.g. NIST SP 800-218 tasks, ISO 27001 controls).
- **Evidence**: Artifact references, logs, scanner output hashes, and reviewer sign-offs.
- **Counter-Claims & Concessions**: Transparent documentation of known gaps, mitigations, and approved architectural deviations.

### Standard Schema Metadata

```json
{
  "$schema": "http://cyclonedx.org/schema/bom-1.6.schema.json",
  "bomFormat": "CycloneDX",
  "specVersion": "1.6",
  "serialNumber": "urn:uuid:f81d4fae-7dec-11d0-a765-00a0c91e6bf6",
  "version": 1
}
```

# Applicability & Operational Impact

The ECMA-424 ratification of CycloneDX 1.6 provides critical legal and standardisation certainty for international compliance:

- **Defense and Public Procurement**: Regulated entities subject to federal procurement rules can leverage ECMA-424 as an internationally sanctioned standard alongside ISO/IEC 5962.
- **Financial Institutions & DORA**: Financial entities implementing the Digital Operational Resilience Act (DORA) utilize CBOM features to audit cryptographic resilience across payment gateways.
- **EU CRA Compliance**: The rich component hierarchy, direct/transitive dependency mapping, and built-in VEX capabilities provide turn-key conformance with CRA Annex I requirements.

# Practical Implementation

### Sample Cryptographic Asset (CBOM) Declaration

```json
{
  "$schema": "http://cyclonedx.org/schema/bom-1.6.schema.json",
  "bomFormat": "CycloneDX",
  "specVersion": "1.6",
  "serialNumber": "urn:uuid:7c9e6679-7425-40de-944b-e07fc1f90ae7",
  "version": 1,
  "metadata": {
    "timestamp": "2026-09-27T09:00:00Z",
    "component": {
      "type": "application",
      "name": "acme-crypto-gateway",
      "version": "1.0.0"
    }
  },
  "components": [
    {
      "type": "cryptographic-asset",
      "bom-ref": "crypto-primitive-kyber768",
      "name": "ML-KEM-768",
      "cryptoProperties": {
        "assetType": "algorithm",
        "algorithmProperties": {
          "primitive": "kem",
          "parameterSetIdentifier": "ML-KEM-768",
          "classicalSecurityLevel": 192,
          "nistQuantumSecurityLevel": 3
        },
        "oid": "2.16.840.1.101.3.4.4.2"
      }
    }
  ]
}
```

### Command-Line Generation and Validation

```bash
# Generate CycloneDX 1.6 BOM with cdxgen
cdxgen -r --spec-version 1.6 -o sbom-1.6.cdx.json

# Validate against official ECMA-424 JSON Schema
cyclonedx-cli validate --input-file sbom-1.6.cdx.json --spec-version 1.6
```

# Dates and Transitions

- **June 2024**: CycloneDX 1.6 ratified as ECMA-424 at the 127th Ecma General Assembly.
- **2024–2026**: Broad adoption across enterprise DevSecOps pipelines and open-source scanners (Syft, Trivy, cdxgen).
- **December 2027**: European Cyber Resilience Act full enforcement date; CycloneDX 1.6 serves as a benchmark standard.

# Related concepts

- [OWASP CycloneDX 1.5 Specification](cyclonedx-1-5.md)
- [CycloneDX Native VEX](../vex/cyclonedx-vex.md)
- [SPDX 3.0 Specification](spdx-3-0.md)
- [CRA SBOM Mandate](../../requirements/cra-sbom-mandate.md)
- [SBOM Generation in Build Pipelines](../../procedures/sbom-generation-at-build.md)

[^cyclonedx-specification]: OWASP Foundation / Ecma International, OWASP CycloneDX Software Bill of Materials Standard (ECMA-424), https://cyclonedx.org/specification/overview/
[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
