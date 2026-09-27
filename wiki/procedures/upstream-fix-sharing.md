---
type: Procedure
title: Upstream Fix Sharing and Responsible Coordination
description: Operational procedure for contributing security patches, bug fixes, and
  vulnerability reports back to upstream open-source maintainers.
category: procedure
tags:
- procedure
- upstream
- maintenance
- cra
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
  jurisdiction: International
  authority_level: guidance
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Upstream fix sharing** encompasses the engineering workflows by which commercial software manufacturers share security remediations with the open-source projects they consume[^eu-cra-regulation].

# Operational Process
1. **Private Notification**: When a vulnerability is found in an external dependency, the finding organization notifies maintainers via documented security channels (`security.txt`, security advisories, or encrypted email).
2. **Coordinated Patching**: Developing pull requests in private repositories to avoid premature public zero-day disclosure.
3. **Regulatory Compliance**: Fulfills the explicit manufacturer duty under CRA Article 13(6) to report third-party component vulnerabilities to upstream maintainers.

# Related concepts
- [CRA Supply Chain](../law/eu/cra-supply-chain.md)
- [Open Source Steward](../roles/open-source-steward.md)

[^eu-cra-regulation]: European Parliament and Council of the European Union, Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act), http://data.europa.eu/eli/reg/2024/2847/oj
