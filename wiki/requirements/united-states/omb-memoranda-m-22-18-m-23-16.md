---
type: Requirement
title: OMB Memoranda M-22-18 and M-23-16 (Secure Software Procurement)
description: White House directives establishing federal agency requirements for procuring
  software built according to NIST SSDF practices.
category: requirement
tags:
- requirement
- us
- omb
- procurement
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: whitehouse-omb-m2218
  resource: https://www.whitehouse.gov/wp-content/uploads/2022/09/M-22-18.pdf
  title: 'OMB Memorandum M-22-18: Enhancing the Security of the Software Supply Chain
    through Secure Software Development Practices'
  author: Office of Management and Budget (OMB)
  last_modified: '2022-09-14T00:00:00Z'
x-software-supply-chain:
  jurisdiction: US
  authority_level: rule
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**OMB Memorandum M-22-18** (issued September 14, 2022) and its companion guidance **OMB M-23-16** (issued June 9, 2023) direct federal executive agencies to require software producers to submit self-attestation forms confirming compliance with NIST SP 800-218 guidelines[^whitehouse-omb-m2218].

**Binding / contractual / guidance**: Legally binding on Federal Civilian Executive Branch agencies; mandatory contractual clause for software vendors selling to the federal government.

# Key Directives
- **Attestation Submission**: Mandatory submission via CISA's repository prior to agency deployment.
- **Third-Party Artifacts**: Agencies may request SBOMs and evidence of third-party dependency evaluations where elevated risk assessments warrant.

# Related concepts
- [CISA Self-Attestation](cisa-self-attestation.md)
- [EO 14028](../../law/united-states/eo-14028.md)

[^whitehouse-omb-m2218]: Office of Management and Budget (OMB), OMB Memorandum M-22-18: Enhancing the Security of the Software Supply Chain through Secure Software Development Practices, https://www.whitehouse.gov/wp-content/uploads/2022/09/M-22-18.pdf
