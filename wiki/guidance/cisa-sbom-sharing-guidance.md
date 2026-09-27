---
type: Guidance
title: 'CISA Guidance: SBOM Sharing, Distribution, and Access Control'
description: Official CISA framework defining operational workflows and access controls
  for distributing machine-readable SBOMs.
category: guidance
tags:
- supply-chain
- guidance
- cisa
- sbom-sharing
- distribution
status: draft
generated:
  by: agent:kb-researcher-writer
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
  authority_level: guidance
  instrument_status: in_force
  provision: CISA SBOM Community Guidance (2023)
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **CISA Guidance on SBOM Sharing, Distribution, and Access Control** provides authoritative operational recommendations for software producers, buyers, and consumers on how to securely distribute, exchange, and control access to Software Bills of Materials[^ntia-sbom-elements].

# The Four SBOM Distribution Architecture Models

```
+-------------------------------------------------------------------+
|               CISA SBOM SHARING ARCHITECTURE MODELS               |
+-------------------------------------------------------------------+
| 1. POINT-TO-POINT DIRECT DELIVERY                                 |
|    - Bundled directly inside package / container archive          |
|    - Shipped alongside binary during customer release             |
+-------------------------------------------------------------------+
| 2. DISCOVERABLE REPOSITORIES & REGISTRIES                         |
|    - Attached as an OCI artifact using Sigstore / Cosign          |
|    - Stored adjacent to container image in registry               |
+-------------------------------------------------------------------+
| 3. ADVERTISE-AND-RETRIEVE WEB ENDPOINTS                           |
|    - Hosted on vendor customer portal with authenticated API      |
|    - Advertised via RFC 9116 / security.txt or RFC 9264 links    |
+-------------------------------------------------------------------+
| 4. CENTRALIZED BROKER & EXCHANGE PLATFORMS                        |
|    - Third-party SaaS trust platforms managing enterprise access  |
|    - Non-disclosure agreement (NDA) enforcement & versioning      |
+-------------------------------------------------------------------+
```

# Access Control & Confidentiality Considerations

Software producers often express concern that public SBOMs expose proprietary intellectual property or assist attackers in discovering unpatched components. CISA recommends:
- **Tiered Access Controls**: Providing public summaries of top-level open source licenses while reserving full transitive dependency trees for authenticated commercial licensees.
- **Contractual Non-Disclosure**: Utilizing standard commercial licensing terms to restrict downstream re-distribution of detailed architecture SBOMs.
- **Companion VEX Publishing**: Always pairing SBOM distribution with authoritative Vulnerability Exploitability eXchange (VEX) feeds to prevent consumers from misinterpreting unreachable vulnerabilities as active risks.

# Related concepts
- [NTIA Minimum Elements for an SBOM](../requirements/ntia-minimum-elements.md)
- [CSAF 2.0 VEX Profile](../standards/vex/csaf-vex.md)
- [Software Producer Role](../roles/software-producer.md)
- [Software Consumer Role](../roles/software-consumer.md)

[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
