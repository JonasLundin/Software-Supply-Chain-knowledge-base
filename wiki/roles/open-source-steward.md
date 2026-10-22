---
type: Role
title: "Role: Open-Source Software Steward"
description: Legal person or foundation providing sustained support, infrastructure,
  and governance for open-source digital products.
category: role
tags:
- supply-chain
- role
- oss-steward
- cra
- open-source
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
  provision: CRA Article 3(14), Article 24
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

An **Open-Source Software Steward** is a legal person, other than a manufacturer, that provides support for the development of open-source software products with digital elements intended for commercial activities, playing a main role in ensuring the viability of those products[^eu-cra-regulation].

Introduced explicitly in Regulation (EU) 2024/2847 (CRA), this distinct regulatory role establishes a proportionate governance regime tailored to open-source foundations (e.g., Linux Foundation, Apache Software Foundation, Eclipse Foundation).

# Legal Framework & Lightweight Obligations

Unlike commercial manufacturers who place products on the market in the course of commercial activities, open-source software stewards are subject to a tailored, proportionate regulatory regime under CRA Article 24:
- **Cybersecurity Policy (Art 24(1))**: Stewards must establish and verify the implementation of a cybersecurity policy to foster the development of secure products with digital elements.
- **Coordinated Vulnerability Disclosure (Art 24(2))**: Stewards must put in place a coordinated vulnerability disclosure policy pursuant to Annex I, Part II, point (1), including designating a clear point of contact for vulnerability reports, facilitating vulnerability remediation, and supporting notification workflows where actively exploited vulnerabilities are identified pursuant to Article 14(1).
- **Administrative Cooperation (Art 24(3))**: Upon request by national market surveillance authorities, stewards must cooperate and provide documented evidence demonstrating compliance with their Article 24 obligations.
- **Regulatory Demarcation**: Stewards are exempt from commercial manufacturer obligations, notably conformity assessment procedures under Article 32, technical documentation duties under Article 31, and CE marking under Article 30.

# Supply-Chain Impact

Open-source stewards play a critical role in establishing default security mechanisms across the ecosystem:
- Enforcing two-factor authentication (2FA) and signed commits across repository contributors.
- Hosting automated CI/CD infrastructure providing reproducible builds and SLSA Level 3 attestations.
- Providing central vulnerability notification and coordination services.

# Related concepts
- [Software Producer](software-producer.md)
- [Package Registry](package-registry.md)
- [Cyber Resilience Act: Supply Chain Provisions](../law/eu/cra-supply-chain.md)

[^eu-cra-regulation]: European Parliament and Council of the European Union, Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act), http://data.europa.eu/eli/reg/2024/2847/oj
