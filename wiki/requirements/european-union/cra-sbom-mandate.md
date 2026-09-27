---
type: Requirement
title: CRA SBOM Regulatory Requirement (Annex I Part II)
description: Regulatory analysis of the CRA requirement to generate and maintain machine-readable
  Software Bills of Materials covering top-level dependencies.
category: requirement
tags:
- requirement
- eu
- cra
- sbom
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
  provision: Annex I Part II(1)
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **Cyber Resilience Act (CRA)** establishes a legal requirement for manufacturers of products with digital elements to maintain a software inventory[^eu-cra-regulation].

**Binding / contractual / guidance**: Statutory binding regulation across all EU Member States.

# Core Requirements
- **Scope of Coverage**: Annex I Part II(1) explicitly requires covering "at the very least the top-level dependencies of the products".
- **Format Requirements**: Must use a commonly used, machine-readable format (such as SPDX, CycloneDX, or CSAF).
- **Technical Documentation Retention**: The SBOM forms part of the technical documentation required under Annex VII and must be kept available for market surveillance authorities for 10 years or the support period, whichever is longer.

# Harmonised Standards and Compliance
Harmonised European standards (such as prEN 40000-1-3) are being developed by CEN/CENELEC to provide presumption of conformity once cited in the Official Journal of the European Union (OJEU).

# Related concepts
- [CRA Supply Chain](../../law/eu/cra-supply-chain.md)
- [CRA Knowledge Base](https://github.com/JonasLundin/CRA-knowledge-base)
- [CycloneDX 1.7](../../standards/sbom-formats/cyclonedx-1-7.md)

[^eu-cra-regulation]: European Parliament and Council of the European Union, Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act), http://data.europa.eu/eli/reg/2024/2847/oj
