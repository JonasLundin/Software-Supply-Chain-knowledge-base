---
type: Guidance
title: BSI Recommendations for Software Bill of Materials (SBOM) Generation and Usage
description: Technical guidance from Germany's Federal Office for Information Security
  on SBOM lifecycle management.
category: guidance
tags:
- guidance
- bsi
- sbom
- germany
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: bsi-tr-03183
  resource: https://www.bsi.bund.de/dok/TR-03183-en
  title: 'BSI Technical Guideline TR-03183: Cyber Resilience Requirements'
  author: Federal Office for Information Security (BSI)
  last_modified: '2024-05-15T00:00:00Z'
x-software-supply-chain:
  jurisdiction: DE
  authority_level: guidance
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **BSI Guidelines for SBOMs** provide detailed engineering recommendations assisting organizations in implementing BSI TR-03183 Part 2 requirements across the software development lifecycle[^bsi-tr-03183].

> [!NOTE]
> **Non-Binding Guidance**: This publication provides advisory good practices to facilitate compliance with binding technical rules.

# Recommended Practices
1. **Automated Continuous Generation**: Generate SBOMs automatically within the CI/CD build pipeline rather than relying on retrospective manual scanning.
2. **Standard Format Utilization**: Mandates the use of standardized machine-readable formats, specifically SPDX 2.3/3.0 and CycloneDX 1.6/1.7.
3. **Completeness and Depth**: Advises organizations to catalog all direct and transitive runtime dependencies, recording cryptographic file digests and supplier origins.

# Related concepts
- [BSI TR-03183 Requirements](../../requirements/germany/bsi-tr-03183.md)
- [Jurisdiction Germany](../../jurisdictions/germany.md)

[^bsi-tr-03183]: Federal Office for Information Security (BSI), BSI Technical Guideline TR-03183: Cyber Resilience Requirements, https://www.bsi.bund.de/dok/TR-03183-en
