---
type: Role
title: "Role: Software Producer"
description: Primary entity designing, compiling, assembling, and distributing commercial
  or proprietary software products.
category: role
tags:
- supply-chain
- role
- producer
- cra
- ssdf
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: eu-cra-regulation
  resource: http://data.europa.eu/eli/reg/2024/2847/oj
  title: Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products
    with digital elements (Cyber Resilience Act)
  author: European Parliament and Council of the European Union
  last_modified: '2024-11-20T00:00:00Z'
- id: ntia-sbom-elements
  resource: https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
  title: The Minimum Elements For a Software Bill of Materials (SBOM)
  author: National Telecommunications and Information Administration (NTIA)
  last_modified: '2021-07-12T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: guidance
  instrument_status: in_force
  provision: CRA Article 3(14), NIST SSDF
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

A **Software Producer** (or manufacturer under the EU Cyber Resilience Act) is any natural or legal person who develops, manufactures, or has developed products with digital elements, or has a product with digital elements designed or manufactured, and markets them under their name or trademark[^eu-cra-regulation].

In the context of modern software supply-chain integrity, producers bear primary responsibility for build integrity, automated SBOM generation, component vulnerability tracking, and security attestation[^ntia-sbom-elements].

# Statutory & Normative Obligations

### 1. Cyber Resilience Act (CRA) Core Duties
Under Article 13 and Annex I Section 2 of Regulation (EU) 2024/2847:
- **Component Due Diligence**: Due diligence must be exercised when integrating third-party and open-source components into products.
- **Mandatory Component Inventory**: Must systematically identify and document components and vulnerabilities, maintaining an internal machine-readable SBOM.
- **Vulnerability Handling**: Must address discovered vulnerabilities without delay and deliver automated security updates throughout the declared support period.

### 2. US Federal Supply Chain Procurement (EO 14028 & CISA Attestation)
Producers supplying US federal agencies must submit signed self-attestations confirming compliance with the NIST SP 800-218 Secure Software Development Framework (SSDF).

# Operational Capabilities & Tooling

Software producers must establish automated capabilities integrated directly into their DevSecOps pipelines:
- **Continuous SBOM Generation**: Invoking tools such as `syft`, `trivy`, or `cdxgen` during every production build.
- **Cryptographic Provenance Signing**: Generating verifiable SLSA build provenance attestations using Sigstore (`cosign`) or in-toto.
- **VEX Publishing**: Emitting authoritative CSAF or OpenVEX statements indicating whether upstream CVEs affect the compiled runtime binary.

# Related concepts
- [Software Consumer](software-consumer.md)
- [Open-Source Steward](open-source-steward.md)
- [CRA Component Inventory & Vulnerability Identification](../requirements/european-union/cra-sbom-mandate.md)
- [CISA Secure Software Development Attestation](../requirements/united-states/cisa-self-attestation.md)

[^eu-cra-regulation]: European Parliament and Council of the European Union, Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act), http://data.europa.eu/eli/reg/2024/2847/oj
[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
