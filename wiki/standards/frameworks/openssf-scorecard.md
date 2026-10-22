---
type: Standard
title: OpenSSF Scorecard Framework
description: Automated security tool assessing open-source projects against risk-reduction
  security practices.
category: standard
tags:
- standard
- framework
- openssf
- scorecard
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: openssf-scorecard-spec
  resource: https://scorecard.dev/
  title: 'OpenSSF Scorecard: Automated Security Metric for Open Source Software'
  author: Open Source Security Foundation (OpenSSF)
  last_modified: '2024-04-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**OpenSSF Scorecard** is an automated analysis framework evaluating open-source code repositories for adherence to critical supply chain security practices[^openssf-scorecard-spec].

# Evaluated Security Checks
- **Code Review**: Verifies pull requests require independent review before merging.
- **Branch Protection**: Confirms master branches reject direct force pushes.
- **Dependency Update Tooling**: Checks for automated dependency maintenance (e.g., Dependabot, Renovate).
- **Cryptographic Signing**: Detects cryptographic commit signing and release artifact signing.
- **SAST and Fuzzing**: Assesses integration of automated static analysis and dynamic fuzzing tools.

# Related concepts
- [S2C2F](s2c2f.md)
- [Scorecard and Best Practices Guidance](../../guidance/openssf/scorecard-and-best-practices.md)

[^openssf-scorecard-spec]: Open Source Security Foundation (OpenSSF), OpenSSF Scorecard: Automated Security Metric for Open Source Software, https://scorecard.dev/
