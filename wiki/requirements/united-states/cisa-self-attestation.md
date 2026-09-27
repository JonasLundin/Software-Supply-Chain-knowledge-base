---
type: Requirement
title: CISA Secure Software Development Self-Attestation Form
description: Common attestation form for software producers selling software to US
  federal civilian executive branch agencies.
category: requirement
tags:
- requirement
- us
- cisa
- attestation
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: cisa-self-attestation-form
  resource: https://www.cisa.gov/resources-tools/resources/secure-software-development-attestation-form
  title: CISA Secure Software Development Self-Attestation Form
  author: Cybersecurity and Infrastructure Security Agency (CISA)
  last_modified: '2024-03-11T00:00:00Z'
x-software-supply-chain:
  jurisdiction: US
  authority_level: rule
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **CISA Secure Software Development Self-Attestation Form** is the standard procurement attestation mechanism established pursuant to OMB Memoranda M-22-18 and M-23-16[^cisa-self-attestation-form].

**Binding / contractual / guidance**: Contractual procurement prerequisite for selling software products to US Federal Civilian Executive Branch agencies.

# Attestation Mandates
Producers must attest under signature of a corporate officer that software was developed in accordance with NIST SP 800-218 practices:
- Software was developed in secure environments with isolated build pipelines.
- Multi-factor authentication, cryptographic artifact signing, and audit logging were enforced.
- Regular automated static and dynamic vulnerability scanning and software dependency reviews were conducted.
- Third-party components were tracked and evaluated for security risks.

# Related concepts
- [SSDF NIST SP 800-218](ssdf-nist-sp-800-218.md)
- [EO 14028](../../law/united-states/eo-14028.md)

[^cisa-self-attestation-form]: Cybersecurity and Infrastructure Security Agency (CISA), CISA Secure Software Development Self-Attestation Form, https://www.cisa.gov/resources-tools/resources/secure-software-development-attestation-form
