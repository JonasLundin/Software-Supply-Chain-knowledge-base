---
type: Jurisdiction
title: European Union Software Supply Chain Framework
description: Statutory cybersecurity framework in the European Union established by
  the Cyber Resilience Act and NIS2 Directive.
category: jurisdiction
tags:
- jurisdiction
- eu
- cra
- nis2
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
- id: eu-nis2-directive
  resource: http://data.europa.eu/eli/dir/2022/2555/oj
  title: Directive (EU) 2022/2555 on measures for a high common level of cybersecurity
    across the Union (NIS2)
  author: European Parliament and Council of the European Union
  last_modified: '2022-12-14T00:00:00Z'
x-software-supply-chain:
  jurisdiction: EU
  authority_level: statutory
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **European Union** enforces binding horizontal legislation governing software supply chain integrity through the Cyber Resilience Act (Regulation (EU) 2024/2847) and the NIS2 Directive (Directive (EU) 2022/2555)[^eu-cra-regulation][^eu-nis2-directive].

# Key Regulatory Requirements
- **Mandatory SBOM Generation**: CRA Annex I Part II(1) mandates machine-readable SBOMs for all products with digital elements made available on the EU single market.
- **Upstream Vulnerability Remediation**: CRA Article 13(6) requires manufacturers to report flaws in third-party components to maintainers.
- **Critical Infrastructure Due Diligence**: NIS2 Article 21(2)(d) requires essential and important entities to assess and mitigate risks arising from direct ICT suppliers.

# Related concepts
- [CRA Supply Chain](../law/eu/cra-supply-chain.md)
- [NIS2 Supply Chain](../law/eu/nis2-article-21-supply-chain.md)

[^eu-cra-regulation]: European Parliament and Council of the European Union, Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act), http://data.europa.eu/eli/reg/2024/2847/oj
[^eu-nis2-directive]: European Parliament and Council of the European Union, Directive (EU) 2022/2555 on measures for a high common level of cybersecurity across the Union (NIS2), http://data.europa.eu/eli/dir/2022/2555/oj
