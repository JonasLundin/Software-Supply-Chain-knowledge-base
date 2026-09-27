---
type: Format
title: CycloneDX Native VEX
description: Integrated Vulnerability Exploitability eXchange (VEX) specification within the OWASP CycloneDX standard for co-locating component inventories and security analysis.
category: format
tags:
  - vex
  - cyclonedx
  - vulnerability-management
  - format
  - ecma-424
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
  provision: CycloneDX v1.5 / v1.6 (ECMA-424) VEX
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**CycloneDX Native VEX** is the integrated Vulnerability Exploitability eXchange capability embedded directly within the OWASP CycloneDX standard (ratified as ECMA-424)[^cyclonedx-specification]. Unlike standalone advisory specifications that require separate distribution files and external product identification databases, CycloneDX allows vulnerability exploitability assertions to be tightly bound directly to components within the Software Bill of Materials (SBOM).

CycloneDX VEX supports two primary architectural deployment models:
1. **Co-located VEX**: Vulnerability assessments and component metadata are packaged together within the same BOM file at build time.
2. **Standalone VEX BOM**: Out-of-band VEX documents that reference external components by Package URL (`purl`) or cryptographic hash, published as dynamic security feeds throughout the product support lifecycle[^ntia-sbom-elements].

```
+-------------------------------------------------------------+
|                     CycloneDX 1.6 BOM                       |
+-------------------------------------------------------------+
               |                               |
               v                               v
+-----------------------------+ +-----------------------------+
|         components          | |       vulnerabilities       |
|-----------------------------| |-----------------------------|
| bom-ref: "lib-xml2-v29"     | | id: "CVE-2024-12345"        |
| name: "libxml2", ver: "2.9" | | affects: ["lib-xml2-v29"]   |
| purl: "pkg:deb/...@2.9.14"  | | analysis:                   |
+-----------------------------+ |   state: "not_affected"     |
                                |   justification:            |
                                |     "code_not_reachable"    |
                                |   response: ["will_not_fix"]|
                                |   detail: "XPath parser not |
                                |     exposed to untrusted    |
                                |     network interfaces."    |
                                +-----------------------------+
```

# Technical Scope / Normative Requirements

### The `vulnerabilities` Schema Model

In CycloneDX (versions 1.4, 1.5, and 1.6), VEX data is populated within the top-level `vulnerabilities` array. Key elements include:

| Property | Requirement | Description |
| :--- | :--- | :--- |
| `id` | Mandatory | Vulnerability identifier (CVE, GHSA, OSV, or internal vendor identifier). |
| `source` | Optional | Authority publishing the identifier (e.g. `NVD`, `GitHub Security Advisory`). |
| `references` | Optional | Web URLs and advisories providing full vulnerability details. |
| `affects` | Mandatory | Array of targets affected, linking to component `bom-ref` values or target PURLs. |
| `analysis` | Mandatory for VEX | Object containing vendor exploitability determinations and rationale. |

### Analysis States and Justifications

The `analysis` object defines the precise operational disposition:

- **`analysis.state`**:
  - `resolved`: Vulnerability has been fixed.
  - `resolved_with_pedigree`: Vulnerability addressed through backporting or source modification.
  - `exploitable`: Code is vulnerable and reachable; immediate remediation recommended.
  - `in_triage`: Investigation is ongoing.
  - `false_positive`: Vulnerability was reported in error or does not apply.
  - `not_affected`: Confirmed non-impacted.
- **`analysis.justification`**: Standardized rationale required when state is `not_affected`:
  - `code_not_present`: Vulnerable module removed or excluded.
  - `code_not_reachable`: Vulnerable execution path cannot be triggered.
  - `requires_configuration`: Vulnerability only triggers under non-default, unconfigured conditions.
  - `requires_dependency`: Missing prerequisite library prevents exploitation.
  - `requires_environment`: Operating environment or platform architecture prevents flaw.
  - `protected_by_compiler`: Modern compiler protections (ASLR, stack canaries, FORTIFY_SOURCE) neutralize exploit.
  - `protected_at_runtime`: Runtime security controls (AppArmor, SELinux, seccomp) block execution.
  - `protected_at_perimeter`: Firewall, WAF, or network segmentation mitigates threat.
  - `protected_by_mitigating_control`: Compensating architectural controls eliminate risk.
- **`analysis.response`**: Vendor action plan (`can_not_fix`, `will_not_fix`, `update`, `rollback`, `workaround_available`).
- **`analysis.detail`**: Detailed technical commentary explaining the justification.

# Applicability & Operational Impact

CycloneDX Native VEX is widely implemented across the software supply chain:

- **OWASP Dependency-Track**: Natively correlates CycloneDX SBOMs with CycloneDX VEX files, updating vulnerability dashboards in real time without rescanning binaries.
- **Regulatory Transparency**: Satisfies European Cyber Resilience Act Article 13(6) expectations by documenting which vulnerabilities in third-party libraries have been triaged and mitigated.
- **Enterprise SecOps**: Greatly accelerates incident response by preventing wasted engineer hours investigating CVEs that are demonstrably unexploitable.

# Practical Implementation

### Sample Embedded CycloneDX VEX Entry

```json
{
  "$schema": "http://cyclonedx.org/schema/bom-1.6.schema.json",
  "bomFormat": "CycloneDX",
  "specVersion": "1.6",
  "serialNumber": "urn:uuid:8b3e839e-4e4a-4d43-85f2-9011e4bf6b7e",
  "version": 1,
  "components": [
    {
      "type": "library",
      "bom-ref": "pkg:npm/axios@0.21.1",
      "name": "axios",
      "version": "0.21.1",
      "purl": "pkg:npm/axios@0.21.1"
    }
  ],
  "vulnerabilities": [
    {
      "bom-ref": "vuln-cve-2020-28168",
      "id": "CVE-2020-28168",
      "source": {
        "name": "NVD",
        "url": "https://nvd.nist.gov/vuln/detail/CVE-2020-28168"
      },
      "affects": [
        {
          "ref": "pkg:npm/axios@0.21.1"
        }
      ],
      "analysis": {
        "state": "not_affected",
        "justification": "code_not_reachable",
        "response": ["will_not_fix"],
        "detail": "Axios is executed strictly in backend Node.js microservices where HTTP proxy redirection headers are not parsed or routed."
      }
    }
  ]
}
```

### CLI Generation via cdxgen

```bash
# Generate CycloneDX SBOM with automated vulnerability auditing
cdxgen -r --include-crypto --spec-version 1.6 -o sbom-with-vex.json
```

# Dates and Transitions

- **Early 2022**: CycloneDX 1.4 introduced formal VEX analysis schema fields.
- **June 2023**: CycloneDX 1.5 added expanded justifications and multi-target affect structures.
- **June 2024**: CycloneDX 1.6 (ECMA-424) ratified with advanced cryptographic and attestation linking.
- **December 2027**: Cyber Resilience Act requires ongoing vulnerability handling throughout product lifecycle.

# Related concepts

- [CSAF 2.0 VEX Profile](csaf-vex.md)
- [OpenVEX Specification](openvex.md)
- [OWASP CycloneDX 1.6 (ECMA-424)](../sbom-formats/cyclonedx-1-6.md)
- [VEX Glossary Term](../../glossary/vex.md)
- [Vulnerability Matching and VEX Procedure](../../procedures/vulnerability-matching-and-vex.md)

[^cyclonedx-specification]: OWASP Foundation / Ecma International, OWASP CycloneDX Software Bill of Materials Standard (ECMA-424), https://cyclonedx.org/specification/overview/
[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
