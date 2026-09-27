---
type: Jurisdiction
title: 'Jurisdiction: United States'
description: United States federal framework driving SBOM adoption, secure software
  development attestation, and federal procurement standards.
category: jurisdiction
tags:
- supply-chain
- jurisdiction
- us
- eo-14028
- cisa
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: ntia-sbom-elements
  resource: https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
  title: The Minimum Elements For a Software Bill of Materials (SBOM)
  author: National Telecommunications and Information Administration (NTIA)
  last_modified: '2021-07-12T00:00:00Z'
x-software-supply-chain:
  jurisdiction: United States
  authority_level: guidance
  instrument_status: in_force
  provision: Executive Order 14028, OMB M-22-18 / M-23-16
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **United States** has pioneered global supply-chain cybersecurity policy through presidential directives, federal procurement regulations, and authoritative technical guidance issued by CISA, NIST, and NTIA[^ntia-sbom-elements].

# Key Policy Instruments

### 1. Executive Order 14028 (May 2021)
President Biden's Executive Order 14028 on *Improving the Nation's Cybersecurity* established the modern concept of Software Bills of Materials (SBOM) and directed the Department of Commerce (NTIA) to publish the baseline definition of minimum elements.

### 2. OMB Memoranda M-22-18 & M-23-16
Mandated that federal agencies may only use software developed in accordance with the NIST Secure Software Development Framework (SP 800-218).

### 3. CISA Common Self-Attestation Form
Enforces mandatory self-attestation for all software producers selling to federal departments, requiring executive certification of build environment security, vulnerability disclosure programs, and third-party dependency tracking.

# Related concepts
- [NTIA Minimum Elements for an SBOM](../requirements/ntia-minimum-elements.md)
- [CISA Secure Software Development Attestation](../requirements/cisa-self-attestation.md)
- [NIST Secure Software Development Framework (SSDF)](../requirements/ssdf-nist-sp-800-218.md)
- [CISA SBOM Sharing and Distribution Guidance](../guidance/cisa-sbom-sharing-guidance.md)

[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
