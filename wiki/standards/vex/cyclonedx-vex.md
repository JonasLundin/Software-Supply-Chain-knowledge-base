---
type: Format
title: CycloneDX Integrated VEX
description: Vulnerability Exploitability eXchange capability embedded directly within
  CycloneDX BOM documents.
category: format
tags:
- supply-chain
- vex
- format
- cyclonedx-vex
status: draft
generated:
  by: agent:antigravity
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: cyclonedx-specification
  resource: https://cyclonedx.org/specification/overview/
  title: OWASP CycloneDX Software Bill of Materials Standard (ECMA-424)
  author: OWASP Foundation / Ecma International
  last_modified: '2024-05-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  provision: CycloneDX Integrated VEX
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**CycloneDX Integrated VEX** format conveying actionable vulnerability status and mitigation guidance[^cyclonedx-specification].

Vulnerability Exploitability eXchange capability embedded directly within CycloneDX BOM documents.

# Actionable Status
Allows software vendors to declare whether listed CVEs are actually exploitable or not affected in the product runtime context.

# Related concepts
- [VEX Index](index.md)

[^cyclonedx-specification]: OWASP Foundation / Ecma International, OWASP CycloneDX Software Bill of Materials Standard (ECMA-424), https://cyclonedx.org/specification/overview/
