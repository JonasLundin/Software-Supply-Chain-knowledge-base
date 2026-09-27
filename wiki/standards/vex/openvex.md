---
type: Format
title: OpenVEX Specification
description: Minimal, lightweight, embeddable JSON-LD format designed specifically
  to convey whether a vulnerability impacts a product.
category: format
tags:
- supply-chain
- vex
- format
- openvex
status: draft
generated:
  by: agent:antigravity
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: ntia-sbom-elements
  resource: https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
  title: The Minimum Elements For a Software Bill of Materials (SBOM)
  author: National Telecommunications and Information Administration (NTIA)
  last_modified: '2021-07-12T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  provision: OpenVEX Specification
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**OpenVEX Specification** format conveying actionable vulnerability status and mitigation guidance[^ntia-sbom-elements].

Minimal, lightweight, embeddable JSON-LD format designed specifically to convey whether a vulnerability impacts a product.

# Actionable Status
Allows software vendors to declare whether listed CVEs are actually exploitable or not affected in the product runtime context.

# Related concepts
- [VEX Index](index.md)

[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
