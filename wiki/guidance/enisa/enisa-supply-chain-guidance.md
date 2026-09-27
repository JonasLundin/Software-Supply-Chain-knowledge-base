---
type: Guidance
title: ENISA Guidelines for Securing the ICT Supply Chain
description: European Union good practice guidance for managing ICT supplier risk
  and assessing software supply chain integrity.
category: guidance
tags:
- guidance
- enisa
- supply-chain
- nis2
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: enisa-supply-chain-report
  resource: https://www.enisa.europa.eu/publications/threat-landscape-for-supply-chain-attacks
  title: ENISA Threat Landscape for Supply Chain Attacks
  author: European Union Agency for Cybersecurity (ENISA)
  last_modified: '2021-07-29T00:00:00Z'
x-software-supply-chain:
  jurisdiction: EU
  authority_level: guidance
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **ENISA Threat Landscape for Supply Chain Attacks** analyzes attack patterns targeting software suppliers and recommends defense strategies for European public and private entities[^enisa-supply-chain-report].

> [!NOTE]
> **Non-Binding EU Guidance**: Provides expert technical analysis to assist Member States and critical entities in implementing NIS2 Article 21 supply chain controls.

# Good Practice Recommendations
1. **Supplier Relationship Management**: Incorporate cybersecurity clauses, coordinated vulnerability disclosure commitments, and audit rights into procurement contracts.
2. **Component Integrity Verification**: Maintain inventory of open-source and third-party software components and track known vulnerabilities.
3. **Separation of Environments**: Isolate development, staging, and production environments to prevent compromised developer credentials from infecting release artifacts.

# Related concepts
- [NIS2 Supply Chain](../../law/eu/nis2-article-21-supply-chain.md)
- [NIS2 Knowledge Base](https://github.com/JonasLundin/NIS2-knowledge-base)

[^enisa-supply-chain-report]: European Union Agency for Cybersecurity (ENISA), ENISA Threat Landscape for Supply Chain Attacks, https://www.enisa.europa.eu/publications/threat-landscape-for-supply-chain-attacks
