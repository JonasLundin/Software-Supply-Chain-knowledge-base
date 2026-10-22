---
type: Requirement
title: 'NIST SP 800-218: Secure Software Development Framework (SSDF) Version 1.1'
description: Core recommendations and practice groups for securing the software development
  lifecycle across organizational and engineering activities.
category: requirement
tags:
- requirement
- us
- nist
- ssdf
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: nist-sp-800-218
  resource: https://csrc.nist.gov/publications/detail/sp/800-218/final
  title: 'NIST SP 800-218: Secure Software Development Framework (SSDF) Version 1.1'
  author: National Institute of Standards and Technology (NIST)
  last_modified: '2022-02-03T00:00:00Z'
x-software-supply-chain:
  jurisdiction: US
  authority_level: guidance
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

Published in February 2022, **NIST Special Publication 800-218 (SSDF v1.1)** provides high-level recommendations for integrating cybersecurity into every phase of software development[^nist-sp-800-218].

**Binding / contractual / guidance**: Federal guidance incorporated as mandatory contractual conditions for federal agency procurement via OMB Memoranda M-22-18 and M-23-16.

# Four Practice Groups
1. **Prepare the Organization (PO)**: Ensure people, processes, and technology are prepared to perform secure software development (e.g., PO.1 policies, PO.5 implement and maintain secure development environments).
2. **Protect Software (PS)**: Safeguard all software components from tampering and unauthorized access (e.g., PS.1 integrity protection, PS.2 provenance verification).
3. **Produce Well-Secured Software (PW)**: Produce software with minimal security defects (e.g., PW.1 architecture design, PW.8 automated testing, PW.9 configure software to have secure settings by default).
4. **Respond to Vulnerabilities (RV)**: Identify residual vulnerabilities and remediate them in a timely fashion (e.g., RV.1 vulnerability monitoring, RV.3 remediate vulnerabilities).

*(Note: NIST SP 800-218A supplements the framework with community profiles for government and open-source ecosystems).*

# Related concepts
- [CISA Self-Attestation](cisa-self-attestation.md)
- [EO 14028](../../law/united-states/eo-14028.md)

[^nist-sp-800-218]: National Institute of Standards and Technology (NIST), NIST SP 800-218: Secure Software Development Framework (SSDF) Version 1.1, https://csrc.nist.gov/publications/detail/sp/800-218/final
