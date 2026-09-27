---
type: Procedure
title: "Procedure: Dependency Due Diligence and Governance"
description: Continuous auditing of open source components for license compliance,
  malicious code injection, and abandoned maintenance.
category: procedure
tags:
- supply-chain
- procedure
- governance
- cra
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
  authority_level: guidance
  instrument_status: in_force
  provision: CRA Article 13(5), OpenSSF Scorecard
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Dependency Due Diligence** is the systematic procedural vetting, continuous monitoring, and risk management of third-party and open-source software libraries integrated into commercial software products[^eu-cra-regulation].

Under Article 13(5) of the Cyber Resilience Act, manufacturers are legally mandated to exercise due diligence when integrating components from third parties so as not to compromise product cybersecurity.

# Operational Vetting Framework

```
                          DEPENDENCY DUE DILIGENCE PIPELINE
+-----------------------+     +-----------------------+     +-----------------------+
|  1. Ingestion Vetting | ==> |  2. Static & Malicious| ==> | 3. Continuous Runtime |
|  - Maintainer health  |     |     Code Analysis     |     |     Monitoring        |
|  - OpenSSF Scorecard  |     |  - License compliance |     |  - Automated CVE match|
|  - Typosquatting check|     |  - Secret detection   |     |  - Pinned lockfiles   |
+-----------------------+     +-----------------------+     +-----------------------+
```

### Evaluation Criteria
- **Maintainer Viability**: Check commit frequency, number of active maintainers, and response time on security issues.
- **Automated Scorecards**: Leverage OpenSSF Scorecard checks (branch protection, code reviews, SAST, dependency update tools).
- **Supply-Chain Integrity**: Enforce cryptographic package verification and monitor for known malware injection campaigns.

# Related concepts
- [Software Producer](../roles/software-producer.md)
- [Open-Source Steward](../roles/open-source-steward.md)
- [CRA Supply Chain Provisions](../law/eu/cra-supply-chain.md)

[^eu-cra-regulation]: European Parliament and Council of the European Union, Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act), http://data.europa.eu/eli/reg/2024/2847/oj
