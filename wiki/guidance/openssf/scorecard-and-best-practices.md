---
type: Concept
title: OpenSSF Scorecard and Best Practices Guidelines
description: Open Source Security Foundation automated tooling and badge criteria
  for open-source package security health.
category: guidance
tags:
- software-supply-chain
- guidance
- openssf
- scorecard
- oss
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: regulation-eu-2024-2847
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

The **Open Source Security Foundation (OpenSSF)** provides automated security metrics and best practice badges to evaluate open-source dependency health[^regulation-eu-2024-2847].

# Automated Security Checks
- Verification of binary artifacts in source repositories.
- Code review, branch protection, and signed commit enforcement.
- Automated static code analysis and dependency pinning.

# Related concepts
- [OpenSSF Guidance Index](index.md)
- [Dependency Due Diligence](../../procedures/dependency-due-diligence.md)

[^regulation-eu-2024-2847]: European Parliament and Council of the European Union, Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act), http://data.europa.eu/eli/reg/2024/2847/oj
