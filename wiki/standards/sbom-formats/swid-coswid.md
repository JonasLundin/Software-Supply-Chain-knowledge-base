---
type: Standard
title: SWID Tags and CoSWID (ISO/IEC 19770-2 / RFC 9393)
description: Software Identification (SWID) tags and Concise SWID (CoSWID) providing
  structured software lifecycle inventory.
category: standard
tags:
- standard
- sbom
- swid
- coswid
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: iso-iec-19770-2
  resource: https://www.iso.org/standard/65666.html
  title: 'ISO/IEC 19770-2:2015 Information technology - Software asset management
    - Part 2: Software identification tag'
  author: International Organization for Standardization (ISO) / IEC
  last_modified: '2015-10-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Software Identification (SWID) Tags (ISO/IEC 19770-2:2015)** and **Concise SWID (RFC 9393 CoSWID)** provide machine-readable metadata records installed alongside software packages to identify installed components, versions, patches, and publishers[^iso-iec-19770-2].

# XML and CBOR Formats
- **ISO/IEC 19770-2 XML Tags**: Standard XML tags installed into designated file system directories documenting product edition, tag creator, and payload file digests.
- **RFC 9393 CoSWID**: Binary Concise Binary Object Representation (CBOR) encoding optimized for constrained devices, IoT devices, and firmware environments.
- **Federal Baseline Recognition**: Formally recognized as an acceptable SBOM format under NTIA 2021 and CISA 2026 minimum elements.

# Intellectual Property and Licensing
ISO/IEC 19770-2 is an international standard published by ISO/IEC. RFC 9393 is published by the IETF under the IETF Trust provisions.

# Related concepts
- [SPDX 2.3](spdx-2-3.md)
- [CISA 2026 Minimum Elements](../../requirements/united-states/cisa-minimum-elements-2026.md)

[^iso-iec-19770-2]: International Organization for Standardization (ISO) / IEC, ISO/IEC 19770-2:2015 Information technology - Software asset management - Part 2: Software identification tag, https://www.iso.org/standard/65666.html
