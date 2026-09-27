---
type: Law
title: Cyber Resilience Act (Regulation (EU) 2024/2847) Supply-Chain Provisions
description: Statutory software supply-chain requirements, vulnerability handling
  duties, and SBOM mandates under the EU Cyber Resilience Act.
category: law
tags:
- law
- eu
- cra
- sbom
- supply-chain
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-11T00:00:00Z'
sources:
- id: eu-cra-regulation
  resource: http://data.europa.eu/eli/reg/2024/2847/oj
  title: Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products
    with digital elements (Cyber Resilience Act)
  author: European Parliament and Council of the European Union
  last_modified: '2024-11-20T00:00:00Z'
x-software-supply-chain:
  jurisdiction: EU
  authority_level: statutory
  instrument_status: in_force
  provision: Regulation (EU) 2024/2847 Articles 13, 14, 24, and Annex I
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Regulation (EU) 2024/2847 (Cyber Resilience Act — CRA)** establishes horizontal cybersecurity requirements for products with digital elements made available on the European Union single market[^eu-cra-regulation].

# Essential Supply-Chain Provisions

### 1. Mandatory SBOM Generation (Annex I Part II point 1)
Manufacturers must:
> "identify and document vulnerabilities and components contained in products with digital elements, including by drawing up a software bill of materials in a commonly used and machine-readable format covering at the very least the top-level dependencies of the products".

### 2. Upstream Component Vulnerability Notification (Article 13(6))
Where a manufacturer identifies a vulnerability in a third-party software component integrated into its product, Article 13(6) mandates that the manufacturer must report the vulnerability to the person or entity maintaining that component and take appropriate remediation measures.
*(Note: Early-warning reporting of actively exploited vulnerabilities to CSIRTs and ENISA within 24 hours is governed separately under Article 14).*

### 3. Open-Source Software Stewards (Article 24)
Article 24 establishes a proportionate regulatory regime for open-source software stewards:
- Under Article 24(3), stewards must put in place a cybersecurity policy fostering coordinated vulnerability handling and cooperation with market surveillance authorities.
- Stewards are not treated as commercial manufacturers, but they remain subject to general civil and product liability regimes (including Directive (EU) 2024/2853 on liability for defective products) where commercial activities or damages occur.

# Related concepts
- [CRA SBOM Mandate](../../requirements/european-union/cra-sbom-mandate.md)
- [CRA Knowledge Base](https://github.com/JonasLundin/CRA-knowledge-base)
- [NIS2 Supply Chain](nis2-article-21-supply-chain.md)

[^eu-cra-regulation]: European Parliament and Council of the European Union, Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act), http://data.europa.eu/eli/reg/2024/2847/oj
