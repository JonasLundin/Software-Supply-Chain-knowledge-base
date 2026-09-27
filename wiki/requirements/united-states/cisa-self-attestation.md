---
type: Requirement
title: CISA Secure Software Development Attestation Form
description: Mandatory federal attestation form requiring executive certification
  of compliance with NIST SP 800-218.
category: requirement
tags:
- supply-chain
- requirement
- cisa
- attestation
- federal-procurement
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
  authority_level: standard
  instrument_status: in_force
  provision: CISA Common Self-Attestation Form pursuant to OMB M-22-18
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **CISA Secure Software Development Common Self-Attestation Form** is a legally binding compliance document issued by the Cybersecurity and Infrastructure Security Agency (**CISA**)[^ntia-sbom-elements].

Pursuant to OMB Memoranda M-22-18 and M-23-16, any commercial software producer selling software to executive departments and agencies of the United States federal government must execute and submit this attestation before federal procurement can proceed.

# Four Critical Security Areas in the Form

Software producers must formally certify under penalty of perjury that their development practices satisfy four core security areas derived from NIST SP 800-218:

### 1. Secure Build Environments
- **Isolation**: Software was developed and compiled in separate, protected, and auditable build environments.
- **Access Control**: Enforcing least privilege, multi-factor authentication (MFA), and audit logging for all systems containing source code or build configuration.
- **Tamper Resistance**: Protecting build infrastructure against unauthorized modification and lateral intrusion.

### 2. Supply Chain Trust & Third-Party Code
- **Due Diligence**: Maintaining consistent processes to review and validate the security of third-party and open-source software components.
- **Automated Tracking**: Maintaining an internal inventory or Software Bill of Materials (SBOM) of all direct and transitive dependencies.
- **Continuous Monitoring**: Monitoring threat feeds for newly reported vulnerabilities affecting integrated components.

### 3. Automated Vulnerability Scanning & Testing
- **Automated Toolchains**: Employing automated tools (SAST, SCA, and DAST) to identify security flaws before release.
- **Remediation Workflows**: Documenting policies and SLAs for remediating identified critical and high vulnerabilities prior to deployment.

### 4. Coordinated Vulnerability Disclosure (CVD)
- **Vulnerability Program**: Operating a formal vulnerability disclosure program accepting reports from external security researchers.
- **Reporting Channels**: Maintaining a publicly accessible intake channel (e.g. `/.well-known/security.txt`) and committing to good-faith researcher safe harbor.

# Sign-off & Accountability
The attestation form must be signed by the **Chief Executive Officer (CEO)** of the software producer or an authorized corporate officer designated by the CEO. Alternatively, producers may submit a certified assessment from an accredited Third-Party Assessment Organization (3PAO) (such as a FedRAMP 3PAO).

# Related concepts
- [NIST Secure Software Development Framework (SSDF)](ssdf-nist-sp-800-218.md)
- [NTIA Minimum Elements for an SBOM](ntia-minimum-elements.md)
- [CISA SBOM Sharing Guidance](../../guidance/cisa/../../guidance/cisa/cisa-sbom-sharing-guidance.md)

[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
