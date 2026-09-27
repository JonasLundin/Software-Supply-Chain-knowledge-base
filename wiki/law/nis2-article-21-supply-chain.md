---
type: Law
title: 'NIS2 Directive Article 21(2)(d): Supply Chain Security'
description: Statutory requirements for essential and important entities to assess
  and mitigate cybersecurity risks across their ICT supply chain.
category: law
tags:
- supply-chain
- law
- nis2
- directive-eu-2022-2555
- risk-management
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
  provision: Directive (EU) 2022/2555 Article 21(2)(d)
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Article 21(2)(d) of Directive (EU) 2022/2555 (NIS2)** imposes a direct statutory obligation on essential and important entities across 18 critical sectors to manage cybersecurity risks throughout their supply chains and supplier relationships[^eu-cra-regulation].

NIS2 recognizes that adversaries frequently compromise critical infrastructure by breaching smaller, less-defended upstream software suppliers, service providers, and managed service operators (MSPs).

# Statutory Requirements under Article 21(2)(d) & Article 21(3)

Under Article 21(2)(d), risk management measures must explicitly address:
> *"supply chain security, including security-related aspects concerning the relationships between each entity and its direct suppliers or service providers."*

### Key Mandates for Regulated Entities:
1. **Supplier Vulnerability Assessments**: Entities must account for the vulnerabilities specific to each direct supplier and service provider.
2. **Quality of Cybersecurity Practices**: Entities must evaluate the overall quality and cybersecurity hygiene of their suppliers' products and development practices, including secure coding procedures.
3. **Coordinated Union-Level Risk Assessments**: Entities must take into account the results of coordinated risk assessments of critical supply chains conducted by the Cooperation Group and ENISA (e.g. 5G cybersecurity toolbox, ICT supply chain assessments).
4. **Contractual Security Guarantees**: Regulated entities must embed mandatory cybersecurity obligations into commercial supplier contracts:
   - Mandatory delivery of component inventories (SBOMs);
   - Rapid notification of zero-day vulnerabilities (matching NIS2 early warning clocks);
   - Right to audit supplier security controls and software development environments.

# Enforcement & Penalties
Failure to implement supply chain risk management measures subjects entities to severe administrative sanctions under Article 34:
- Essential entities: Administrative fines up to **€10,000,000** or **2% of total global annual turnover**.
- Important entities: Administrative fines up to **€7,000,000** or **1.4% of total global annual turnover**.

# Related concepts
- [CRA Supply Chain Provisions](cra-supply-chain.md)
- [Software Consumer Role](../roles/software-consumer.md)
- [Dependency Due Diligence Procedure](../procedures/dependency-due-diligence.md)

[^eu-cra-regulation]: European Parliament and Council of the European Union, Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act), http://data.europa.eu/eli/reg/2024/2847/oj
