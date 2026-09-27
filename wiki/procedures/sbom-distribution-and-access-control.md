---
type: Procedure
title: SBOM Distribution and Access Control
description: Secure transmission, publishing, and authorization controls for sharing
  software bills of materials with customers and authorities.
category: procedure
tags:
- procedure
- sbom
- distribution
- access-control
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: cisa-sbom-sharing
  resource: https://www.cisa.gov/resources-tools/resources/software-bill-materials-sharing-considerations
  title: Software Bill of Materials Sharing Considerations
  author: Cybersecurity and Infrastructure Security Agency (CISA)
  last_modified: '2023-04-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: guidance
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**SBOM distribution and access control** defines the protocols and policies software producers implement to safely share component inventories with downstream buyers, asset managers, and regulatory authorities[^cisa-sbom-sharing].

# Distribution Models
- **In-Band Bundling**: Embedding the SBOM directly inside installation packages or container images (`/.well-known/sbom` or OCI layer artifacts).
- **Out-of-Band Portals**: Hosting authenticated customer portals where enterprise licensees access SBOMs tied to specific product releases.
- **Access Control & Sensitivity**: Balancing customer transparency with the protection of proprietary architectural details.

# Related concepts
- [SBOM Generation at Build](sbom-generation-at-build.md)
- [CISA SBOM Sharing Guidance](../guidance/cisa/cisa-sbom-sharing-guidance.md)

[^cisa-sbom-sharing]: Cybersecurity and Infrastructure Security Agency (CISA), Software Bill of Materials Sharing Considerations, https://www.cisa.gov/resources-tools/resources/software-bill-materials-sharing-considerations
