---
type: Standard
title: OWASP CycloneDX VEX Profile
description: Native Vulnerability Exploitability eXchange capability embedded within
  the CycloneDX standard.
category: standard
tags:
- standard
- vex
- cyclonedx
- format
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: cyclonedx-1-7-spec
  resource: https://cyclonedx.org/specification/overview/
  title: OWASP CycloneDX Software Bill of Materials Specification v1.7 (ECMA-424 2nd
    Edition)
  author: OWASP Foundation / Ecma International
  last_modified: '2025-10-21T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**CycloneDX VEX** enables software producers to communicate vulnerability exploitability status directly within a CycloneDX SBOM document or as an independent companion VEX document[^cyclonedx-1-7-spec].

# Capabilities and Status Model
CycloneDX models vulnerability assessments inside the `vulnerabilities` element:
- **Vulnerability Identification**: Captures CVE, GHSA, or proprietary identifiers.
- **Analysis State**: Expresses status through standard values: `resolved`, `resolved_with_pedigree`, `exploitable`, `in_triage`, `false_positive`, and `not_affected`.
- **Justification**: For `not_affected` assessments, enumerates technical justifications including `code_not_present`, `code_not_reachable`, `requires_configuration`, `requires_dependency`, `requires_environment`, and `protected_by_mitigating_control`.

# Intellectual Property and Licensing
OWASP CycloneDX is licensed under the Apache License 2.0.

# Related concepts
- [CycloneDX 1.7](../sbom-formats/cyclonedx-1-7.md)
- [CSAF VEX](csaf-vex.md)
- [OpenVEX](openvex.md)

[^cyclonedx-1-7-spec]: OWASP Foundation / Ecma International, OWASP CycloneDX Software Bill of Materials Specification v1.7 (ECMA-424 2nd Edition), https://cyclonedx.org/specification/overview/
