---
type: Standard
title: Common Security Advisory Framework (CSAF) 2.0 VEX Profile
description: Profile 5 of the OASIS CSAF 2.0 standard for machine-readable vulnerability
  status communication.
category: standard
tags:
- standard
- vex
- csaf
- format
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: oasis-csaf-2-0
  resource: https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html
  title: Common Security Advisory Framework Version 2.0 (CSAF v2.0)
  author: OASIS Common Security Advisory Framework TC
  last_modified: '2022-11-18T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**CSAF 2.0 Profile 5 (Vulnerability Exploitability eXchange — VEX)** is a specialized profile of the Common Security Advisory Framework ratified as an OASIS Standard on November 18, 2022[^oasis-csaf-2-0].

# VEX Statuses and Justifications
CSAF VEX communicates whether an organization's products are affected by disclosed vulnerabilities:
1. **`not_affected`**: The component is present, but the vulnerability is not exploitable in the product context. Must include a justification:
   - `component_not_present`
   - `vulnerable_code_not_present`
   - `vulnerable_code_cannot_be_controlled_by_adversary`
   - `vulnerable_code_not_in_execute_path`
   - `inline_mitigations_already_exist`
2. **`affected`**: The vulnerability can be exploited or is known to affect the product.
3. **`fixed`**: Remediation is available in a security update.
4. **`under_investigation`**: The vendor is actively analyzing product exploitability.

# Intellectual Property and Licensing
OASIS CSAF 2.0 is published under the OASIS Open IPR Mode (Royalty Free on Limited Terms).

# Related concepts
- [CycloneDX VEX](cyclonedx-vex.md)
- [OpenVEX](openvex.md)
- [CVD Knowledge Base](https://github.com/JonasLundin/CVD-knowledge-base)

[^oasis-csaf-2-0]: OASIS Common Security Advisory Framework TC, Common Security Advisory Framework Version 2.0 (CSAF v2.0), https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html
