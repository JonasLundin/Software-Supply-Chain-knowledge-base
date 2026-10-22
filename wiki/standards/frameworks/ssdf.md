---
type: Standard
title: NIST Secure Software Development Framework (SSDF)
description: Architectural overview of NIST SP 800-218 secure development practices
  and maturity recommendations.
category: standard
tags:
- standard
- framework
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

The **NIST Secure Software Development Framework (SSDF)** synthesizes proven software security practices from BSA, OWASP, and SAFECode into a structured set of recommendations for software engineering organizations[^nist-sp-800-218].

# Relationship to Supply Chain Integrity
SSDF structures secure coding into four distinct practice groups (PO, PS, PW, RV), directly requiring development organizations to verify third-party libraries, generate SBOM metadata, and enforce code review before production release.

# Related concepts
- [SSDF Requirements](../../requirements/united-states/ssdf-nist-sp-800-218.md)
- [EO 14028](../../law/united-states/eo-14028.md)

[^nist-sp-800-218]: National Institute of Standards and Technology (NIST), NIST SP 800-218: Secure Software Development Framework (SSDF) Version 1.1, https://csrc.nist.gov/publications/detail/sp/800-218/final
