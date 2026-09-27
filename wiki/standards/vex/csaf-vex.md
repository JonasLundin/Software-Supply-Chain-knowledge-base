---
type: Format
title: CSAF 2.0 Vulnerability Exploitability eXchange (VEX) Profile
description: OASIS Common Security Advisory Framework v2.0 standardized machine-readable profile for vendor-asserted vulnerability exploitability, status tracking, and remediation guidance.
category: format
tags:
  - vex
  - csaf
  - oasis
  - vulnerability-management
  - format
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
  provision: CSAF 2.0 (OASIS Standard) - VEX Profile
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**CSAF 2.0 (Common Security Advisory Framework)** is an international OASIS standard designed for publishing and exchanging machine-readable cybersecurity advisories. The **CSAF VEX Profile** is one of five official CSAF profiles specifically tailored to convey Vulnerability Exploitability eXchange (VEX) assertions[^ntia-sbom-elements].

When organizations ingest Software Bills of Materials (SBOMs), automated vulnerability scanners frequently trigger hundreds of false-positive alerts on latent, uncalled, or mitigated component vulnerabilities. The CSAF VEX profile allows software manufacturers and suppliers to issue authoritative, digitally signed statements clarifying whether an identified Common Vulnerabilities and Exposures (CVE) identifier actually impacts their product in its shipping configuration, drastically reducing wasted triage labor.

```
+-------------------------------------------------------------+
|                      CSAF 2.0 VEX Document                  |
|  - document.category: "csaf_vex"                            |
|  - document.publisher (Vendor identity, contact, namespace) |
|  - document.tracking (ID, initial/current release, status)  |
+-------------------------------------------------------------+
                               |
                               +-----------------------------+
                               |                             |
                               v                             v
+---------------------------------------------+  +---------------------------+
|                product_tree                 |  |      vulnerabilities      |
|  - full_product_names                       |  |  - cve: "CVE-2023-XXXXX"  |
|  - product_id: "CSAFPID-0001"               |  |  - product_status:        |
|  - product_identification_helper            |  |    * known_not_affected   |
|    (purl, cpe, hashes)                      |  |    * known_affected       |
+---------------------------------------------+  |    * fixed                |
                               |                 |    * under_investigation  |
                               +---------------->|  - threats / justifications|
                                   referenced    |  - remediations           |
                                   by product_id +---------------------------+
```

# Technical Scope / Normative Requirements

### Structural Envelope and Mandatory Fields

A CSAF VEX document must validate against the strict OASIS JSON Schema and conform to the Profile 4 (`csaf_vex`) constraints:

| Section | Key Fields | Normative Constraints |
| :--- | :--- | :--- |
| `document` | `category`, `csaf_version`, `title`, `publisher`, `tracking` | `category` must be `"csaf_vex"`. `csaf_version` must be `"2.0"`. `tracking.status` must be `final`, `interim`, or `draft`. |
| `product_tree`| `branches`, `full_product_names`, `relationships` | Every product asserted upon must have a unique `product_id`. Should include `product_identification_helper` containing canonical `purl` or `cpe`. |
| `vulnerabilities` | `cve`, `product_status`, `flags`, `threats`, `remediations` | At least one vulnerability entry must be present. Must contain a `product_status` mapping. |

### The Four VEX Statuses in CSAF

Under `vulnerabilities[].product_status`, products are mapped into one of four mutually exclusive statuses:

1. **`known_not_affected`**: The vulnerability has been analyzed and confirmed to not impact the product.
2. **`known_affected`**: The vulnerability is exploitable or presents actionable risk in the product.
3. **`fixed`**: The product previously contained the vulnerability, but this version includes an integrated remediation.
4. **`under_investigation`**: The vendor is actively evaluating exploitability; no definitive determination has been reached yet.

### Normative Justifications for `known_not_affected`

When a product is categorized under `known_not_affected`, CSAF 2.0 requires machine-readable justifications defined in `flags[].label` or `threats`:
- `component_not_present`: The vulnerable sub-component or library is not packaged in the shipping binary.
- `vulnerable_code_not_present`: The library is present, but the vulnerable function was stripped, removed, or refactored.
- `vulnerable_code_not_in_execute_path`: The code exists in the artifact, but cannot be invoked or reached during execution.
- `vulnerable_code_cannot_be_controlled_by_adversary`: The code is executed, but adversary control over input parameters is impossible.
- `inline_mitigations_already_exist`: Environmental or operational mitigations (e.g. compiler sanitizers, capability drops, sandbox barriers) neutralize exploitability.

# Applicability & Operational Impact

CSAF 2.0 VEX is widely adopted across enterprise hardware vendors, industrial automation, and governmental cybersecurity authorities:

- **German Federal Office for Information Security (BSI)**: Recommends and utilizes CSAF 2.0 across German critical infrastructure and manufacturer reporting guidelines.
- **Enterprise Product Security Incident Response Teams (PSIRTs)**: Cisco, Siemens, Red Hat, and Schneider Electric publish advisory feeds natively in CSAF 2.0.
- **Automated Ingestion**: Vulnerability platforms ingest CSAF feeds via ROLIE (RFC 8322) feeds and automated HTTPS discovery endpoints (`/.well-known/csaf/provider-metadata.json`).

# Practical Implementation

### Sample CSAF 2.0 VEX Document

```json
{
  "document": {
    "category": "csaf_vex",
    "csaf_version": "2.0",
    "title": "Acme Gateway VEX Advisory for CVE-2024-38816",
    "publisher": {
      "category": "vendor",
      "name": "Acme Security Technologies",
      "namespace": "https://acme.com"
    },
    "tracking": {
      "id": "ACME-VEX-2026-0042",
      "current_release_date": "2026-09-27T08:00:00Z",
      "initial_release_date": "2026-09-27T08:00:00Z",
      "status": "final",
      "version": "1.0.0"
    }
  },
  "product_tree": {
    "full_product_names": [
      {
        "name": "Acme API Gateway 4.2.0",
        "product_id": "PROD-ACME-GW-420",
        "product_identification_helper": {
          "purl": "pkg:generic/acme-gateway@4.2.0"
        }
      }
    ]
  },
  "vulnerabilities": [
    {
      "cve": "CVE-2024-38816",
      "product_status": {
        "known_not_affected": [
          "PROD-ACME-GW-420"
        ]
      },
      "flags": [
        {
          "label": "vulnerable_code_not_in_execute_path",
          "product_ids": [
            "PROD-ACME-GW-420"
          ]
        }
      ],
      "threats": [
        {
          "category": "impact",
          "details": "The vulnerable Spring framework method is excluded from the compilation classpath.",
          "product_ids": [
            "PROD-ACME-GW-420"
          ]
        }
      ]
    }
  ]
}
```

### Discovery and Ingestion Architecture

CSAF standardizes public discovery via well-known web directories:

```bash
# Retrieve provider metadata from vendor domain
curl -s https://sec.acme.com/.well-known/csaf/provider-metadata.json | jq .

# Validate CSAF document using official csaf-validator-service
csaf-validator --file ACME-VEX-2026-0042.json
```

# Dates and Transitions

- **January 2023**: CSAF 2.0 published as an official OASIS Standard.
- **2023–2025**: Broad enterprise adoption by industrial manufacturers (Siemens, Phoenix Contact) and European national certs (BSI, CERT-Bund).
- **December 2027**: Alignment with the European Cyber Resilience Act obligation to notify and coordinate vulnerability remediations with downstream integrators.

# Related concepts

- [OpenVEX Specification](openvex.md)
- [CycloneDX Native VEX](cyclonedx-vex.md)
- [VEX Glossary Term](../../glossary/vex.md)
- [Vulnerability Matching and VEX Procedure](../../procedures/vulnerability-matching-and-vex.md)
- [NTIA Minimum Elements](../../requirements/united-states/ntia-minimum-elements.md)

[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
