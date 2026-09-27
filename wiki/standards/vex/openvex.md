---
type: Format
title: OpenVEX Specification
description: Minimalist, interoperable JSON-LD specification for exchanging vulnerability exploitability assertions across container scanners and automated CI/CD pipelines.
category: format
tags:
  - vex
  - openvex
  - vulnerability-management
  - format
  - openssf
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
  provision: OpenVEX v0.2.0 Specification
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**OpenVEX** is an open-source, lightweight, interoperable specification designed specifically to communicate Vulnerability Exploitability eXchange (VEX) statements with minimal implementation friction[^ntia-sbom-elements]. Created by Chainguard and hosted under the Open Source Security Foundation (OpenSSF), OpenVEX eliminates the verbose overhead associated with legacy advisory formats, providing a streamlined JSON-LD document optimized for container scanners, software package repositories, and automated build pipelines.

OpenVEX is engineered to be embedded directly inside in-toto attestations or distributed as standalone metadata files, allowing scanners such as Grype, Trivy, and Clair to filter out non-exploitable vulnerabilities automatically during CI/CD security quality gates.

```
+-------------------------------------------------------------+
|                      OpenVEX Document                       |
|  - @context: "https://openvex.dev/ns/v0.2.0"                |
|  - @id: "https://openvex.dev/docs/acme-vex-001"             |
|  - author: "Acme Security Engineering"                      |
|  - timestamp: "2026-09-27T08:00:00Z", version: 1            |
+-------------------------------------------------------------+
                               |
                               v
+-------------------------------------------------------------+
|                         statements                          |
|  - vulnerability: { name: "CVE-2023-38545" }                |
|  - products: [ "pkg:apk/wolfi/curl@8.4.0-r0" ]              |
|  - status: "not_affected"                                   |
|  - justification: "vulnerable_code_not_present"             |
|  - impact_statement: "SOCKS5 buffer overflow disabled       |
|    at build time via compiler flags."                       |
+-------------------------------------------------------------+
```

# Technical Scope / Normative Requirements

### Structural Specification (v0.2.0)

An OpenVEX document consists of top-level document provenance followed by an array of atomic statements:

| Field | Type | Description |
| :--- | :--- | :--- |
| `@context` | URI | Fixed JSON-LD context string (`https://openvex.dev/ns/v0.2.0`). |
| `@id` | URI | Canonical URI identifying this specific VEX document instance. |
| `author` | String | Identifier or organization name asserting the VEX claim. |
| `role` | String (Optional) | Role of the author (e.g. `Project Maintainer`, `Security Team`, `Vendor`). |
| `timestamp` | ISO 8601 UTC | Timestamp of document publication. |
| `version` | Integer | Monotonically increasing revision counter (starts at `1`). |
| `statements` | Array | One or more discrete vulnerability assessment statements. |

### Statement Properties

Each atomic statement in OpenVEX evaluates a single vulnerability against one or more products:

- `vulnerability`: Object containing `name` (e.g. `CVE-2023-38545` or `GHSA-xxxx-yyyy-zzzz`) and optional `description`.
- `products`: Array of package identifiers, ideally expressed as Package URLs (`purl`) or cryptographic hashes.
- `subcomponents`: Optional array of specific sub-libraries contained within the evaluated products.
- `status`: Must be exactly one of the four NTIA-standardized statuses:
  - `not_affected`
  - `affected`
  - `fixed`
  - `under_investigation`
- `justification`: Required when `status` is `not_affected`. Must match one of five standardized values:
  - `component_not_present`
  - `vulnerable_code_not_present`
  - `vulnerable_code_not_in_execute_path`
  - `vulnerable_code_cannot_be_controlled_by_adversary`
  - `inline_mitigations_already_exist`
- `impact_statement`: Human-readable context providing technical justification for the assessment.
- `action_statement`: Remediation or mitigation instructions provided when status is `affected`.

# Applicability & Operational Impact

OpenVEX is particularly suited for high-velocity software delivery and cloud-native environments:

- **Container Image Hardening**: Base-image vendors (such as Chainguard Images, Red Hat UBI, Ubuntu Pro) ship signed OpenVEX documents alongside container digests.
- **Automated Gate Decoupling**: Build pipelines can ingest vendor OpenVEX files directly during vulnerability scanning, suppressing unfixable upstream noise without modifying scanner rulefiles or creating brittle exemption lists.
- **Tooling Compatibility**: Supported out-of-the-box by the `vexctl` toolchain and natively ingested by Trivy and Grype.

# Practical Implementation

### Creating an OpenVEX Document with `vexctl`

The official OpenSSF `vexctl` CLI provides a declarative way to generate and sign OpenVEX documents:

```bash
# Create an initial OpenVEX statement asserting non-exploitability
vexctl create \
  --vuln "CVE-2024-21626" \
  --product "pkg:oci/auth-proxy@sha256:d8c47...e1" \
  --status "not_affected" \
  --justification "inline_mitigations_already_exist" \
  --impact "Binary runs under rootless container runtime where file descriptor leaks cannot access host filesystem." \
  --file auth-proxy.openvex.json
```

### Filtering Scans in CI/CD with Trivy or Grype

```bash
# Scan container image using OpenVEX to eliminate false positives
trivy image --vex auth-proxy.openvex.json acme/auth-proxy:latest

# In Grype
grype acme/auth-proxy:latest --vex auth-proxy.openvex.json
```

### Complete OpenVEX JSON-LD Example

```json
{
  "@context": "https://openvex.dev/ns/v0.2.0",
  "@id": "https://openvex.dev/docs/acme/auth-proxy-vex-v1",
  "author": "Acme Product Security Team",
  "role": "Software Producer",
  "timestamp": "2026-09-27T08:30:00Z",
  "version": 1,
  "statements": [
    {
      "vulnerability": {
        "name": "CVE-2024-21626"
      },
      "products": [
        "pkg:oci/auth-proxy@sha256:d8c47b59451d8d21c430e386e686524b071e69d7b420f1df2ce245b78000b0e1"
      ],
      "status": "not_affected",
      "justification": "inline_mitigations_already_exist",
      "impact_statement": "Execution occurs strictly within an unprivileged User Namespace where leaking container file descriptors cannot cross system mount points."
    }
  ]
}
```

# Dates and Transitions

- **December 2022**: OpenVEX specification announced by Chainguard and OpenSSF.
- **Mid-2023**: OpenVEX v0.2.0 finalized with full JSON-LD normalization and `vexctl` integration.
- **2024–2026**: Broad integration across enterprise container scanning tools and DevSecOps pipelines.

# Related concepts

- [CSAF 2.0 VEX Profile](csaf-vex.md)
- [CycloneDX Native VEX](cyclonedx-vex.md)
- [VEX Glossary Term](../../glossary/vex.md)
- [Vulnerability Matching and VEX Procedure](../../procedures/vulnerability-matching-and-vex.md)
- [NTIA Minimum Elements](../../requirements/ntia-minimum-elements.md)

[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
