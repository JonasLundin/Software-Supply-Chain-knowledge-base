---
type: Requirement
title: "NIST SP 800-218: Secure Software Development Framework (SSDF)"
description: Foundational NIST cybersecurity standard establishing four practice groups (PO, PS, PW, RV) to mitigate vulnerabilities and prevent software supply chain tampering.
category: requirement
tags:
  - nist
  - ssdf
  - sp-800-218
  - secure-development
  - requirement
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
  jurisdiction: United States
  authority_level: statutory
  instrument_status: in_force
  provision: NIST Special Publication 800-218 Version 1.1
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**NIST Special Publication 800-218 (Secure Software Development Framework - SSDF Version 1.1)** is the definitive United States federal standard for integrating security throughout the software development life cycle (SDLC)[^ntia-sbom-elements]. Published by the National Institute of Standards and Technology (NIST) in February 2022 pursuant to Section 4(e) of Executive Order 14028, the SSDF consolidates high-level secure development practices from OWASP, BSA, SAFECode, and Microsoft SDL into a unified, outcome-based framework.

Under White House Office of Management and Budget (OMB) Memoranda M-22-18 and M-23-16, compliance with NIST SP 800-218 is mandatory for all commercial software producers selling software, firmware, or software-as-a-service to the United States Federal Government.

```
+-----------------------------------------------------------------------------------------+
|                  NIST SP 800-218 Secure Software Development Framework                  |
+-----------------------------------------------------------------------------------------+
               |                               |                               |
               v                               v                               v
+-----------------------------+ +-----------------------------+ +-----------------------------+
|  Prepare the Organization   | |    Protect the Software     | | Produce Well-Secured S/W    |
|            (PO)             | |            (PS)             | |            (PW)             |
|-----------------------------| |-----------------------------| |-----------------------------|
| - PO.1 Security Req.        | | - PS.1 Code protection      | | - PW.1 Secure design        |
| - PO.2 Roles & Training     | |   (MFA, branch protections) | | - PW.3 Component vetting    |
| - PO.3 Toolchains & SAST    | | - PS.2 Release integrity    | | - PW.4 Safe build options   |
| - PO.5 Secure environments  | |   (hashes, signatures, SLSA)| | - PW.5 Validate 3rd-party   |
|   (isolated build runners)  | | - PS.3 Release archiving    | | - PW.7 Code review & SAST   |
+-----------------------------+ +-----------------------------+ +-----------------------------+
                                               |
                                               v
                              +---------------------------------+
                              |   Respond to Vulnerabilities    |
                              |              (RV)               |
                              |---------------------------------|
                              | - RV.1 Gather reports (VDP)     |
                              | - RV.2 Remediate & patch timely |
                              | - RV.3 Root-cause analysis      |
                              +---------------------------------+
```

# Technical Scope / Normative Requirements

The SSDF is organized into four core Practice Groups, each comprised of specific Practices, Tasks, Implementation Examples, and References:

### 1. Prepare the Organization (PO)

Focuses on enterprise governance, security policies, toolchains, and environment hardening:
- **PO.1**: Define security requirements across software engineering projects.
- **PO.2**: Implement formal roles, accountability matrices, and developer security training.
- **PO.3**: Provision and maintain automated toolchains (linters, SCA, SAST, DAST, secrets detection).
- **PO.5**: Configure secure development and build environments. Ensure least-privilege access, network segmentation, and credential hygiene for continuous integration runners.

### 2. Protect the Software (PS)

Guards code, build pipelines, and release packages against tampering, unauthorized alteration, or malicious compromise:
- **PS.1 (Protect Code from Tampering)**: Enforce version control, multi-factor authentication, commit signing, and mandatory peer code reviews.
- **PS.2 (Verify Software Release Integrity)**: Generate verifiable release artifacts, including cryptographic checksums (SHA-256/512), digital signatures (Cosign/Sigstore), and build provenance (SLSA).
- **PS.3 (Archive Releases)**: Retain immutable copies of source revisions, build configuration files, compiler versions, dependencies, and SBOMs to facilitate post-incident forensics.

### 3. Produce Well-Secured Software (PW)

Addresses engineering controls, architecture, third-party component selection, and code review:
- **PW.1 & PW.2**: Model threats and design software with security by default.
- **PW.3 (Reuse Existing, Well-Secured Software)**: Evaluate third-party libraries for maintenance activity, known CVEs, and provenance.
- **PW.4 & PW.6**: Configure compilers with hardening flags (e.g. stack protection `-fstack-protector-strong`, ASLR, DEP/NX, FORTIFY_SOURCE).
- **PW.5**: Validate third-party code integrity before inclusion. Maintain a machine-readable SBOM to track direct and transitive dependencies.
- **PW.7 & PW.8**: Automate code reviews, static code analysis (SAST), software composition analysis (SCA), and dynamic application security testing (DAST).

### 4. Respond to Vulnerabilities (RV)

Establishes continuous post-release vulnerability handling and disclosure:
- **RV.1**: Operate a public Vulnerability Disclosure Program (VDP) or Coordinated Vulnerability Disclosure (CVD) process.
- **RV.2**: Rapidly triage, assess exploitability (using VEX), and release validated security patches.
- **RV.3**: Conduct post-mortem analyses to prevent recurrence across other software assets.

# Applicability & Operational Impact

- **Federal Procurement**: Mandatory under OMB M-22-18 and M-23-16. Software vendors must sign formal legal attestations confirming SSDF compliance before selling to US federal agencies.
- **Integration with CISA**: Forms the technical backbone of the CISA Secure Software Development Attestation Common Form.
- **Cross-Framework Harmonization**: Directly aligns with ISO/IEC 27034 (Application Security), OpenSSF Best Practices, and the European Cyber Resilience Act Annex I requirements.

# Practical Implementation

### Mapping SSDF Tasks to Automated GitHub Actions Checks

| SSDF Task | CI/CD Implementation Control | Automated Tool / Rule |
| :--- | :--- | :--- |
| **PO.3 / PW.7** | Static Application Security Testing | GitHub CodeQL / Semgrep in PR pipeline |
| **PS.1** | Two-person review and signed commits | GitHub Branch Protection RuleSet + GPG commit requirement |
| **PS.2** | Cryptographic provenance and signing | Sigstore Cosign + SLSA GitHub Generator |
| **PW.3 / PW.5** | Dependency vetting & SBOM generation | Anchore Syft / CycloneDX CLI + Trivy SCA |
| **PW.4** | Compiler hardening flags | GCC/Clang: `-Wall -Wextra -Werror -D_FORTIFY_SOURCE=2 -fstack-protector-strong -fPIE -pie` |
| **RV.1** | Coordinated vulnerability disclosure | Standardized `SECURITY.md` in repository root |

# Dates and Transitions

- **May 12, 2021**: Executive Order 14028 directs NIST to issue secure software development guidance.
- **February 2022**: NIST officially releases SP 800-218 Version 1.1.
- **September 14, 2022**: OMB issues Memorandum M-22-18 establishing federal compliance deadlines.
- **March 2024**: CISA launches the final Common Attestation Form and online repository (RSAA) operationalizing SSDF enforcement.

# Related concepts

- [CISA Self-Attestation Common Form](cisa-self-attestation.md)
- [NTIA Minimum Elements](ntia-minimum-elements.md)
- [SLSA v1.0 Specification](../standards/attestation-and-provenance/slsa-1-0.md)
- [United States Jurisdiction Overview](../jurisdictions/united-states.md)
- [Dependency Due Diligence Procedure](../procedures/dependency-due-diligence.md)

[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
