---
type: Requirement
title: 'NIST SP 800-218: Secure Software Development Framework (SSDF)'
description: Authoritative set of fundamental, sound secure software development practices
  organized into four core categories.
category: requirement
tags:
- supply-chain
- requirement
- nist
- ssdf
- sp-800-218
- eo-14028
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
  provision: NIST Special Publication 800-218 Version 1.1
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**NIST Special Publication 800-218 (Secure Software Development Framework - SSDF Version 1.1)** is the definitive United States federal standard defining secure software development practices[^ntia-sbom-elements].

Mandated for federal agency procurement under OMB Memoranda M-22-18 and M-23-16, the SSDF establishes a common language for software producers and consumers to communicate and verify security practices throughout the software development lifecycle (SDLC).

# The Four SSDF Practice Groups

```
+-------------------------------------------------------------------+
|               NIST SP 800-218 PRACTICE GROUPS (SSDF v1.1)         |
+-------------------------------------------------------------------+
| 1. PREPARE THE ORGANIZATION (PO)                                  |
|    People, processes, and technology prepared to perform secure   |
|    software development at the organization level.                |
+-------------------------------------------------------------------+
| 2. PROTECT THE SOFTWARE (PS)                                      |
|    Protect all components of the software from tampering and      |
|    unauthorized access in each release.                           |
+-------------------------------------------------------------------+
| 3. PRODUCE WELL-SECURED SOFTWARE (PW)                             |
|    Produce well-secured software that has minimal vulnerabilities |
|    in its releases.                                               |
+-------------------------------------------------------------------+
| 4. RESPOND TO VULNERABILITIES (RV)                                |
|    Identify vulnerabilities in software releases and respond      |
|    appropriately to remediate and prevent recurrence.             |
+-------------------------------------------------------------------+
```

# Detailed Practice Matrix

### Group 1: Prepare the Organization (PO)
- `PO.1`: Define security requirements for software development.
- `PO.2`: Implement roles and responsibilities across engineering teams.
- `PO.3`: Implement supporting toolchains (SAST, DAST, SCA, linters) and automation.
- `PO.4`: Define and enforce software security criteria for third-party software components.

### Group 2: Protect the Software (PS)
- `PS.1`: Protect all forms of code from unauthorized access and tampering (version control protections, branch locking, MFA).
- `PS.2`: Provide a mechanism for verifying software release integrity (cryptographic signing, checksums, SLSA provenance).
- `PS.3`: Archive and protect each software release and its build metadata for traceability.

### Group 3: Produce Well-Secured Software (PW)
- `PW.1`: Design software to meet security requirements and mitigate threats (threat modeling, architecture reviews).
- `PW.2`: Review the software design against security requirements.
- `PW.4`: Reuse existing, well-secured software components rather than duplicating functionality.
- `PW.5`: Create and validate source code following secure coding standards.
- `PW.6`: Configure compilation, interpreter, and build processes to improve executable security (compiler hardening flags, stack canaries, ASLR).
- `PW.7`: Review and test code for vulnerabilities before release (automated static, dynamic, and penetration testing).

### Group 4: Respond to Vulnerabilities (RV)
- `RV.1`: Identify and confirm vulnerabilities on an ongoing basis (monitoring vulnerability databases, running continuous SCA).
- `RV.2`: Assess, prioritize, and remediate vulnerabilities (coordinated vulnerability disclosure, rapid patch engineering).
- `RV.3`: Analyze vulnerabilities to identify root causes and improve organizational development practices.

# Related concepts
- [CISA Secure Software Development Attestation](cisa-self-attestation.md)
- [NTIA Minimum Elements for an SBOM](ntia-minimum-elements.md)
- [SLSA v1.0 Framework](../../standards/attestation-and-provenance/slsa-1-0.md)

[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
