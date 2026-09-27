---
type: Jurisdiction
title: 'Jurisdiction: European Union'
description: European regulatory regime mandating horizontal SBOM inventories, vulnerability
  handling, and supply chain security under the CRA and NIS2.
category: jurisdiction
tags:
- supply-chain
- jurisdiction
- eu
- cra
- nis2
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: eu-cra-regulation
  resource: http://data.europa.eu/eli/reg/2024/2847/oj
  title: Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products
    with digital elements (Cyber Resilience Act)
  author: European Parliament and Council of the European Union
  last_modified: '2024-11-20T00:00:00Z'
x-software-supply-chain:
  jurisdiction: European Union
  authority_level: guidance
  instrument_status: in_force
  provision: Regulation (EU) 2024/2847, Directive (EU) 2022/2555
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **European Union** has established the world's most legally binding and comprehensive horizontal supply-chain cybersecurity framework through the **Cyber Resilience Act (Regulation (EU) 2024/2847)** and the **NIS2 Directive (Directive (EU) 2022/2555)**[^eu-cra-regulation].

# Legislative Landscape

### 1. Cyber Resilience Act (CRA)
- **Mandatory Component Inventory**: Annex I Section 2(1) obligates manufacturers of all products with digital elements to maintain an inventory of components, including automated software bills of materials.
- **Duty of Care**: Manufacturers must identify and document vulnerabilities, continuously assess third-party components, and deploy automated security patches.
- **Open-Source Protections**: Recognizes open-source software stewards under a specialized, proportionate regime (Article 24).

### 2. NIS2 Directive
- **Article 21(2)(d)**: Mandates essential and important entities across 18 critical sectors to manage cybersecurity risks throughout their supply chains and supplier relationships.

# Enforcement & Timelines
- CRA vulnerability reporting obligations apply from **11 September 2026**.
- Full CRA product conformity, CE marking, and SBOM inventory requirements apply from **11 December 2027**.

# Related concepts
- [CRA Component Inventory & Vulnerability Identification](../requirements/cra-sbom-mandate.md)
- [Cyber Resilience Act: Supply Chain Provisions](../law/cra-supply-chain.md)
- [NIS2 Article 21(2)(d): Supply Chain Risk Management](../law/nis2-article-21-supply-chain.md)

[^eu-cra-regulation]: European Parliament and Council of the European Union, Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act), http://data.europa.eu/eli/reg/2024/2847/oj
