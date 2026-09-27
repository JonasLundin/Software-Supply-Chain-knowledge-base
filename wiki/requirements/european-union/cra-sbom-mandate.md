---
type: Requirement
title: Cyber Resilience Act (CRA) SBOM & Component Identification Mandate
description: Mandatory statutory obligation under Regulation (EU) 2024/2847 Annex I Part II(1) and Article 13 to maintain machine-readable SBOMs and exercise third-party due diligence.
category: requirement
tags:
  - cra
  - sbom
  - european-union
  - regulation-2024-2847
  - requirement
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
  - id: eu-cra-regulation
    resource: http://data.europa.eu/eli/reg/2024/2847/oj
    title: Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act)
    author: European Parliament and Council of the European Union
    last_modified: '2024-11-20T00:00:00Z'
x-software-supply-chain:
  jurisdiction: European Union
  authority_level: binding
  instrument_status: in_force
  provision: Regulation (EU) 2024/2847, Annex I Part II(1) & Article 13(5)-(6)
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

Under the **Cyber Resilience Act (Regulation (EU) 2024/2847)**, the European Union established the world's first comprehensive horizontal legal mandate requiring manufacturers of products with digital elements to create, maintain, and retain a Software Bill of Materials (SBOM)[^eu-cra-regulation]. Set out in Annex I, Part II, point (1) and Article 13, this requirement transforms software component transparency from a voluntary procurement preference into a legally binding market-access condition for the EU Single Market.

Manufacturers cannot legally place software or connected hardware products on the EU market without establishing an automated component inventory, exercising technical due diligence over integrated open-source and proprietary libraries, and continuously monitoring that inventory for newly disclosed vulnerabilities throughout the product's defined support period.

```
+-----------------------------------------------------------------------------------------+
|                  CRA Component Documentation Lifecycle (Regulation 2024/2847)          |
+-----------------------------------------------------------------------------------------+
                                             |
             +-------------------------------+-------------------------------+
             |                                                               |
             v                                                               v
+---------------------------------------+       +---------------------------------------+
|  Annex I, Part II, Point (1) Mandate  |       |     Article 13(5)-(6) Due Diligence   |
|---------------------------------------|       |---------------------------------------|
| - Identify & document all components  |       | - Verify 3rd-party code security      |
| - Machine-readable format             |       | - Do not compromise overall integrity|
| - At least top-level dependencies     |       | - Continuous vulnerability monitoring |
| - Include in Technical Documentation  |       | - Deploy security patches without delay|
+---------------------------------------+       +---------------------------------------+
             |                                                               |
             +-------------------------------+-------------------------------+
                                             |
                                             v
+-----------------------------------------------------------------------------------------+
|                           Regulatory Ingestion & Enforcement                            |
|  - Retained in Technical Documentation for 10 years or support period (Annex VII)       |
|  - Provided to Market Surveillance Authorities (MSAs) upon official inquiry             |
|  - Non-compliance penalties: Fines up to €15,000,000 or 2.5% global annual turnover     |
+-----------------------------------------------------------------------------------------+
```

# Technical Scope / Normative Requirements

### 1. The Statutory Requirement (Annex I, Part II, Point 1)

Annex I, Part II, Point (1) of Regulation (EU) 2024/2847 states that manufacturers must:
> *"identify and document components and vulnerabilities, including by drawing up a software bill of materials in a commonly used and machine-readable format covering at the very least the top-level dependencies of the product."*

Normative requirements derived from this text and corresponding recitals include:
- **Commonly Used Format**: The European Commission and standardization bodies (CEN/CENELEC) recognize SPDX (ISO/IEC 5962) and CycloneDX (ECMA-424) as standard machine-readable formats.
- **Dependency Scope**: While the legal floor specifies "at the very least top-level dependencies", effective conformity with the vulnerability monitoring obligation (Article 13(6)) practically requires full recursive (transitive) dependency coverage.
- **Vulnerability Tracking**: The component inventory must directly correlate with the manufacturer's internal vulnerability handling processes.

### 2. Third-Party Component Due Diligence (Article 13(5))

Article 13(5) establishes that integrating third-party software (commercial, open-source, or firmware) does not reduce the manufacturer's ultimate legal liability. Manufacturers must:
1. Exercise due diligence when selecting and integrating third-party code.
2. Verify that integrated components do not compromise the essential cybersecurity requirements of the product.
3. Keep third-party software components up to date with security patches.

### 3. Confidentiality and Market Access (Recital 47)

Recital 47 clarifies a crucial commercial distinction:
- The SBOM forms part of the product's **Technical Documentation** (Article 31 and Annex VII).
- Manufacturers are **not** required to publish their complete, confidential SBOM publicly on the internet for general consumers.
- However, the SBOM must be immediately accessible to **Market Surveillance Authorities (MSAs)** upon formal request and may be shared with business-to-business (B2B) integrators under commercial agreements.

# Applicability & Operational Impact

- **Addressees**: Every manufacturer, importer, and distributor placing products with digital elements on the EU market (ranging from operating systems, microcontrollers, and smart consumer devices to enterprise ERP platforms).
- **Documentation Retention**: Technical files, including baseline and release-specific SBOMs, must be retained for at least 10 years after the product was placed on the market, or for the duration of the support period, whichever is longer.
- **Sanctions & Penalties (Article 64)**: Failure to comply with Annex I essential cybersecurity requirements can result in administrative fines of up to **€15,000,000 or 2.5% of total worldwide annual turnover**, along with potential market withdrawal orders.

# Practical Implementation

### CI/CD Pipeline Artifact Archiving Workflow

To maintain full compliance with CRA Annex VII documentation retention, CI/CD pipelines should produce immutable, signed SBOM archives alongside each production build:

```yaml
# GitHub Actions snippet for CRA SBOM generation & compliance archiving
name: CRA Technical Documentation Release
on:
  push:
    tags: ['v*']

jobs:
  sbom-archive:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Build Application
        run: make release

      - name: Generate CycloneDX 1.6 SBOM
        uses: CycloneDX/gh-node-module-generatebom@v1
        with:
          output: "build/cra-sbom-v${{ github.ref_name }}.cdx.json"
          spec-version: "1.6"

      - name: Retain in Immutable Compliance Storage
        run: |
          aws s3 cp build/cra-sbom-v${{ github.ref_name }}.cdx.json \
            s3://acme-cra-technical-records/products/pde-4001/${{ github.ref_name }}/sbom.cdx.json \
            --object-lock-mode COMPLIANCE \
            --object-lock-retain-until-date "2037-12-31T23:59:59Z"
```

# Dates and Transitions

- **November 20, 2024**: Regulation (EU) 2024/2847 published in the Official Journal of the European Union.
- **December 11, 2024**: Entry into force of the Cyber Resilience Act.
- **September 11, 2026**: Early application of obligations regarding actively exploited vulnerabilities and severe incident reporting (Article 14).
- **December 11, 2027**: Full statutory application. Mandatory enforcement of Annex I essential requirements, including SBOM generation, CE marking, and market surveillance oversight.

# Related concepts

- [CRA Supply Chain Provisions](../../law/eu/../../law/eu/cra-supply-chain.md)
- [European Union Jurisdiction Overview](../../jurisdictions/european-union.md)
- [Dependency Due Diligence Procedure](../../procedures/dependency-due-diligence.md)
- [NTIA Minimum Elements](../united-states/ntia-minimum-elements.md)
- [OWASP CycloneDX 1.6 (ECMA-424)](../../standards/sbom-formats/cyclonedx-1-6.md)

[^eu-cra-regulation]: European Parliament and Council of the European Union, Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act), http://data.europa.eu/eli/reg/2024/2847/oj
