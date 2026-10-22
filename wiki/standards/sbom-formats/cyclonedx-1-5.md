---
type: Standard
title: OWASP CycloneDX 1.5
description: Legacy release of the CycloneDX standard introducing formulations and
  commercial licensing models.
category: standard
tags:
- standard
- sbom
- cyclonedx
- format
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-06-30T00:00:00Z'
sources:
- id: cyclonedx-1-5-spec
  resource: https://cyclonedx.org/docs/1.5/
  title: OWASP CycloneDX Software Bill of Materials Specification v1.5
  author: OWASP Foundation
  last_modified: '2023-06-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: superseded
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**OWASP CycloneDX 1.5** was released in June 2023, expanding the standard beyond basic package inventory to encompass software formulations, commercial licensing transactions, and service definitions[^cyclonedx-1-5-spec].

> [!NOTE]
> **Superseded Standard**: CycloneDX 1.5 is superseded by [CycloneDX 1.7](cyclonedx-1-7.md) and [CycloneDX 1.6](cyclonedx-1-6.md).

# Structural Overview
- **Expanded Licensing**: Added support for commercial licenses, licensing agreements, and multi-license attribution.
- **Services and APIs**: Added metadata for remote SaaS and microservice endpoints interacting with components.
- **Formulation**: Early implementation of dependency build graphs and execution environments.

# Intellectual Property and Licensing
OWASP CycloneDX is licensed under the Apache License 2.0.

# Related concepts
- [CycloneDX 1.7](cyclonedx-1-7.md)
- [CycloneDX 1.6](cyclonedx-1-6.md)

[^cyclonedx-1-5-spec]: OWASP Foundation, OWASP CycloneDX Software Bill of Materials Specification v1.5, https://cyclonedx.org/docs/1.5/
