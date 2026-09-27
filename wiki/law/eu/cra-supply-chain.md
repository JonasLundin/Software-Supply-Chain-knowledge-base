---
type: Law
title: 'Cyber Resilience Act: Supply Chain Provisions (Regulation (EU) 2024/2847)'
description: Statutory supply-chain cybersecurity obligations for manufacturers, open-source
  stewards, and economic operators under the CRA.
category: law
tags:
- supply-chain
- law
- cra
- regulation-eu-2024-2847
- due-diligence
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
  jurisdiction: International
  authority_level: binding
  instrument_status: in_force
  provision: Articles 13, 14, 24, Annex I Section 2
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Regulation (EU) 2024/2847 (Cyber Resilience Act - CRA)** introduces the European Union's first binding, horizontal statutory regime governing software and hardware supply-chain cybersecurity[^eu-cra-regulation].

Rather than treating digital products as isolated monolithic artifacts, the CRA legally codifies the reality of multi-tiered component assembly, requiring manufacturers to exercise continuous due diligence over third-party and open-source dependencies.

# Key Statutory Provisions for the Software Supply Chain

### 1. Component Due Diligence (Article 13(5))
Manufacturers who integrate components sourced from third parties (commercial or open source) must:
- Verify that the components do not compromise the security of the product with digital elements;
- Exercise due diligence to ensure that the integrated components have been developed in accordance with the essential cybersecurity requirements set out in Annex I Section 1;
- Ensure that the component developer does not introduce known exploitable vulnerabilities.

### 2. Mandatory Component Inventory & Machine-Readable SBOM (Annex I Section 2(1))
Manufacturers must:
> *"identify and document components and vulnerabilities, including by drawing up a software bill of materials in a commonly used and machine-readable format covering at the very least the top-level dependencies of the products."*

While the CRA does not mandate a specific commercial format, accepted standards meeting this obligation include **SPDX 2.3/3.0** and **CycloneDX 1.5/1.6**.

### 3. Open-Source Software Stewards (Article 24)
Recognizing that open-source foundations and individual maintainers do not operate for commercial profit, the CRA establishes a specialized regime for **Open-Source Software Stewards**:
- Stewards are exempt from third-party conformity assessment, CE marking, and product liability.
- Stewards must establish a cybersecurity policy and a Coordinated Vulnerability Disclosure (CVD) process.
- Direct cooperation channels with market surveillance authorities to share non-confidential vulnerability intelligence.

### 4. Supply Chain Vulnerability Propagation (Article 13(6) & Article 14)
- When a manufacturer discovers an actively exploited vulnerability in an upstream third-party component, the manufacturer must report the flaw via ENISA's Single Reporting Platform (SRP) within **24 hours** of awareness.
- Manufacturers must make available security updates and patches free of charge to downstream consumers for the entire declared support period (minimum 5 years, or matching expected product lifetime).

# Timelines and Applicability
- **Entry into Force**: December 2024.
- **Reporting Obligations (Article 14)**: Mandatory from **11 September 2026**.
- **Full Supply Chain & SBOM Mandates**: Mandatory from **11 December 2027**.

# Related concepts
- [CRA Component Inventory & Vulnerability Identification](../../requirements/european-union/../../requirements/european-union/cra-sbom-mandate.md)
- [NIS2 Article 21(2)(d): Supply Chain Risk Management](nis2-article-21-supply-chain.md)
- [Software Producer Role](../../roles/software-producer.md)
- [Open-Source Steward Role](../../roles/open-source-steward.md)

[^eu-cra-regulation]: European Parliament and Council of the European Union, Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act), http://data.europa.eu/eli/reg/2024/2847/oj
