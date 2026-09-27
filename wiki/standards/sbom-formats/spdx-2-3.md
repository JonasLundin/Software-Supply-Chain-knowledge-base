---
type: Standard
title: Software Package Data Exchange (SPDX) 2.3
description: Specification for communicating software component identity, licensing,
  and security metadata.
category: standard
tags:
- standard
- sbom
- spdx
- format
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: spdx-2-3-spec
  resource: https://spdx.github.io/spdx-spec/v2.3/
  title: Software Package Data Exchange (SPDX) Specification Version 2.3
  author: Linux Foundation (SPDX Workgroup)
  last_modified: '2022-11-28T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**SPDX 2.3** is an open standard specification for exchanging software bill of materials (SBOM) data, published by the Linux Foundation's SPDX Workgroup[^spdx-2-3-spec].

> [!NOTE]
> **International Standard Baseline**: ISO/IEC 5962:2021 formally adopted SPDX version 2.2.1. Version 2.3 is a direct evolutionary release that maintains backward compatibility with ISO/IEC 5962:2021 while introducing dedicated fields for security information, external document references, and expanded file-tagging semantics.

# Structural Model
SPDX 2.3 organizes software supply chain metadata into core functional sections:
- **Document Creation Information**: Identifies the SPDX document namespace, version, creators, and creation timestamp.
- **Package Information**: Describes software units including component name, version, supplier, download location, and verification checksums.
- **File Information**: Conveys individual file paths, hashes, license information, and contributor notices.
- **Snippet Information**: Details sub-file code snippets integrated from third-party sources.
- **Relationships**: Expresses semantic relationships between components (such as `DEPENDS_ON`, `CONTAINS`, `DEPENDENCY_OF`, and `PATCH_APPLIED`).
- **External References**: Links packages to external systems such as package-url (purl), Common Platform Enumeration (CPE), and Security Advisory databases.

# Intellectual Property and Licensing
The SPDX Specification is published by the Linux Foundation under the Creative Commons Attribution 3.0 Unported (CC-BY-3.0) license.

# Related concepts
- [SPDX 3.0](spdx-3-0.md)
- [Package URL](../identifiers/package-url.md)
- [CISA 2026 Minimum Elements](../../requirements/united-states/cisa-minimum-elements-2026.md)

[^spdx-2-3-spec]: Linux Foundation (SPDX Workgroup), Software Package Data Exchange (SPDX) Specification Version 2.3, https://spdx.github.io/spdx-spec/v2.3/
