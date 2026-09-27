---
type: Guidance
title: CISA Software Bill of Materials Sharing Considerations
description: Federal guidance outlining operational models, transport mechanisms,
  and access control strategies for SBOM exchange.
category: guidance
tags:
- guidance
- cisa
- sbom
- sharing
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: cisa-sbom-sharing
  resource: https://www.cisa.gov/sbom
  title: Software Bill of Materials Sharing Considerations
  author: Cybersecurity and Infrastructure Security Agency (CISA)
  last_modified: '2023-04-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: US
  authority_level: guidance
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

Published by CISA's SBOM Community Workgroup, **Software Bill of Materials Sharing Considerations** explores the practical mechanisms software producers and consumers can use to exchange SBOMs securely[^cisa-sbom-sharing].

> [!NOTE]
> **Advisory Guidance**: This document offers operational frameworks for software exchange and does not impose regulatory mandates.

# Key Sharing Mechanisms
- **In-Band Discovery**: Placing SBOM files directly inside software packages, container images, or well-known URI endpoints (`/.well-known/sbom`).
- **Out-of-Band Portals**: Operating authenticated customer repositories for commercial software products.
- **Access Control & IP Protection**: Addressing intellectual property and sensitive architecture concerns through role-based access controls and nondisclosure agreements.

# Related concepts
- [CISA 2026 Minimum Elements](../../requirements/united-states/cisa-minimum-elements-2026.md)
- [SBOM Distribution and Access Control](../../procedures/sbom-distribution-and-access-control.md)

[^cisa-sbom-sharing]: Cybersecurity and Infrastructure Security Agency (CISA), Software Bill of Materials Sharing Considerations, https://www.cisa.gov/sbom
