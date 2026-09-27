---
type: Role
title: 'Role: Open-Source Software Steward'
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
  provision: CRA Article 3(15), Article 24
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

An **Open-Source Software Steward** is a legal person, other than a manufacturer, that provides support for the development of open-source software products with digital elements intended for commercial activities, playing a main role in ensuring the viability of those products[^eu-cra-regulation].

Introduced explicitly in Regulation (EU) 2024/2847 (CRA), this distinct regulatory role establishes a proportionate governance regime tailored to open-source foundations (e.g., Linux Foundation, Apache Software Foundation, Eclipse Foundation).

# Legal Framework & Lightweight Obligations

Unlike commercial manufacturers, open-source stewards do not place products on the market for profit and are subject to lightweight, tailored requirements under CRA Article 24:
- **Cybersecurity Policy**: Must put in place a cybersecurity policy to foster development of secure products.
- **Coordinated Vulnerability Disclosure**: Must establish a public CVD policy and intake mechanism for vulnerability handling.
- **Cooperation**: Must cooperate with market surveillance authorities upon request to provide relevant non-confidential information.
- **Exemption from Conformity Assessment**: Stewards are exempt from third-party conformity assessment, CE marking, and product liability regimes.

# Supply-Chain Impact

Open-source stewards play a critical role in establishing default security mechanisms across the ecosystem:
- Enforcing two-factor authentication (2FA) and signed commits across repository contributors.
- Hosting automated CI/CD infrastructure providing reproducible builds and SLSA Level 3 attestations.
- Providing central vulnerability notification and coordination services.

# Related concepts
- [Software Producer](software-producer.md)
- [Package Registry](package-registry.md)
- [Cyber Resilience Act: Supply Chain Provisions](../law/cra-supply-chain.md)

[^eu-cra-regulation]: European Parliament and Council of the European Union, Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act), http://data.europa.eu/eli/reg/2024/2847/oj
