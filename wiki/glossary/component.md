---
type: Glossary
title: Software Component
description: Statutory and technical definition of an integrated sub-element or library
  within a software product.
category: glossary
tags:
- glossary
- cra
- component
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
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
  provision: CRA Article 3(6)
  checked_at: '2026-09-27T00:00:00Z'
---

# Definition

Under Article 3(6) of Regulation (EU) 2024/2847 (Cyber Resilience Act)[^eu-cra-regulation], a **software component** refers to software intended to be integrated into a product with digital elements, or software that is integrated into such a product.

# Context and Supply Chain Governance

A software component represents a discrete, functional unit of software—such as a library, module, driver, firmware image, or container layer—developed internally or acquired from third parties or open-source ecosystems. Tracking components through automated SBOM generation allows asset owners to identify inherited vulnerabilities, verify cryptographic signatures, and maintain rigorous supply chain visibility across the entire product lifecycle.

# Related concepts
- [Software Bill of Materials](software-bill-of-materials.md)
- [Package URL](../standards/identifiers/package-url.md)

[^eu-cra-regulation]: European Parliament and Council of the European Union, Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act), http://data.europa.eu/eli/reg/2024/2847/oj
