---
type: Guidance
title: OpenSSF Best Practices and Scorecard Implementation Guide
description: Practical recommendations from the OpenSSF for securing open-source development
  workflows and continuous integration pipelines.
category: guidance
tags:
- guidance
- openssf
- scorecard
- best-practices
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: openssf-best-practices
  resource: https://bestpractices.coreinfrastructure.org/
  title: OpenSSF Best Practices Badge Program
  author: Open Source Security Foundation (OpenSSF)
  last_modified: '2023-11-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: guidance
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **OpenSSF Best Practices Guide** provides practical guidelines for open-source maintainers and corporate development teams to enhance project security and automate supply chain protection[^openssf-best-practices].

> [!NOTE]
> **Community Guidance**: Voluntary industry recommendations published by the Open Source Security Foundation.

# Implementation Milestones
- **CI/CD Hardening**: Pinning GitHub Actions and pipeline dependencies by immutable full-length commit SHA rather than mutable tags.
- **Automated Scorecard Integration**: Running OpenSSF Scorecard in daily continuous integration to track regression in security controls.
- **Security Policy Publication**: Maintaining a clear `SECURITY.md` file establishing coordinated vulnerability reporting instructions.

# Related concepts
- [OpenSSF Scorecard Framework](../../standards/frameworks/openssf-scorecard.md)
- [S2C2F Framework](../../standards/frameworks/s2c2f.md)

[^openssf-best-practices]: Open Source Security Foundation (OpenSSF), OpenSSF Best Practices Badge Program, https://bestpractices.coreinfrastructure.org/
