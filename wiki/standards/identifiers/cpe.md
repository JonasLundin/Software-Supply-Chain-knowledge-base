---
type: Standard
title: Common Platform Enumeration (CPE)
description: Structured naming scheme for information technology systems, software
  packages, and hardware platforms.
category: standard
tags:
- standard
- identifier
- cpe
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: nist-cpe-spec
  resource: https://nvd.nist.gov/products/cpe
  title: 'Common Platform Enumeration: Dictionary and Specifications (CPE 2.3)'
  author: National Institute of Standards and Technology (NIST)
  last_modified: '2023-01-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: US
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Common Platform Enumeration (CPE)** is a standardized method maintained by NIST for naming classes of applications, operating systems, and hardware devices present in an enterprise[^nist-cpe-spec].

# Syntax Structure (CPE 2.3 Formatted String)
`cpe:2.3:[part]:[vendor]:[product]:[version]:[update]:[edition]:[language]:[sw_edition]:[target_sw]:[target_hw]:[other]`
- **Part Indicator**: `a` for application, `o` for operating system, `h` for hardware.
- **Matching Role in SBOMs**: Used by scanners to query the National Vulnerability Database (NVD) for associated CVE records.

# Related concepts
- [Package URL](package-url.md)
- [Software Heritage ID (SWHID)](swhid.md)

[^nist-cpe-spec]: National Institute of Standards and Technology (NIST), Common Platform Enumeration: Dictionary and Specifications (CPE 2.3), https://nvd.nist.gov/products/cpe
