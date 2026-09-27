---
type: Requirement
title: CISA Secure Software Development Attestation Common Form
description: Mandatory federal procurement form requiring executive legal attestation of adherence to NIST SP 800-218 across development environments, supply chains, and patching.
category: requirement
tags:
  - cisa
  - attestation
  - federal-procurement
  - omb-m-22-18
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
  provision: CISA Common Form / OMB M-22-18 & M-23-16
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **CISA Secure Software Development Attestation Common Form** is the official federal compliance instrument developed by the Cybersecurity and Infrastructure Security Agency (CISA) in coordination with the Office of Management and Budget (OMB)[^ntia-sbom-elements]. Mandated under OMB Memoranda M-22-18 and M-23-16, the Common Form operationalizes Section 4(e) of Executive Order 14028 by requiring commercial software producers selling software to US federal agencies to formally attest, under penalty of law, that their software was developed in accordance with NIST SP 800-218 (SSDF) practices.

The attestation form must be signed by the software producer's Chief Executive Officer (CEO) or an authorized corporate officer with legal authority to bind the entity, establishing direct executive accountability for software supply chain integrity.

```
+-----------------------------------------------------------------------------------------+
|                    CRA / CISA Federal Attestation Workflow (RSAA)                       |
+-----------------------------------------------------------------------------------------+
                                             |
                                             v
+-----------------------------------------------------------------------------------------+
|                              Software Producer Executive                                |
|  - Reviews engineering telemetry, build environment security, and dependency vetting    |
|  - Validates NIST SP 800-218 control coverage across 4 mandatory clauses                |
+-----------------------------------------------------------------------------------------+
                                             |
             +-------------------------------+-------------------------------+
             |                                                               |
             v                                                               v
+---------------------------------------+       +---------------------------------------+
|        Full Direct Attestation        |       | Plan of Action & Milestones (POA&M)   |
|---------------------------------------|       |---------------------------------------|
| - Affirms all 4 SSDF core clauses     |       | - Discloses specific non-compliant    |
| - Submits digitally signed form       |       |   controls                            |
| - Optionally attaches SBOM / Artifacts|       | - Commits to remediation timeline     |
|                                       |       | - Requires explicit agency approval   |
+---------------------------------------+       +---------------------------------------+
             |                                                               |
             +-------------------------------+-------------------------------+
                                             |
                                             v
+-----------------------------------------------------------------------------------------+
|                  CISA Repository for Software Attestations and Artifacts                |
|                                          (RSAA)                                         |
|  - Centralized federal repository accessible by all federal procurement officers        |
|  - Grants authority to operate (ATO) for civilian and defense agency procurement        |
+-----------------------------------------------------------------------------------------+
```

# Technical Scope / Normative Requirements

### 1. Mandatory Attestation Clauses

The CISA Common Form requires executive affirmation across four non-negotiable clauses grounded in NIST SP 800-218:

| Clause | SSDF Reference | Mandatory Obligation |
| :--- | :--- | :--- |
| **Clause 1: Secure Environment** | PO.5, PS.1 | The software was developed and built in secure environments where access controls, multi-factor authentication, network segmentation, and continuous monitoring are enforced across all build servers and repositories. |
| **Clause 2: Trusted Supply Chain** | PW.3, PW.4, PW.5 | The producer has made a good-faith effort to maintain trusted supply chains, including rigorous vetting of third-party and open-source components, dependency hash pinning, and maintenance of software component records (SBOM). |
| **Clause 3: Automated Vulnerability Testing** | PW.7, PW.8 | The producer employs automated testing tools (Static Application Security Testing - SAST, Software Composition Analysis - SCA, and dynamic testing) to identify and remediate vulnerabilities prior to release. |
| **Clause 4: Disclosure and Patching** | RV.1, RV.2, RV.3 | The producer operates a Coordinated Vulnerability Disclosure (CVD) program, accepts external vulnerability reports, and deploys timely security patches throughout the supported product life cycle. |

### 2. Signatory Hierarchy and Legal Liability

The Common Form cannot be signed by junior engineering leads or product managers. It strictly requires:
- **Chief Executive Officer (CEO)**, or
- **Designated Corporate Officer**: An executive formally authorized by corporate resolution to legally bind the company.
False statements on the Common Form expose the signing officer and the corporation to federal criminal penalties under the False Statements Act (18 U.S.C. § 1001) and civil liability under the False Claims Act.

### 3. Exception Mechanism: Plan of Action and Milestones (POA&M)

If a software producer cannot truthfully attest to one or more required practices:
- It must submit an attached **Plan of Action and Milestones (POA&M)** detailing the deficiency.
- The POA&M must specify mitigating compensating controls and an aggressive date-certain remediation milestone.
- Federal agencies must review and formally approve the POA&M before granting procurement waivers.

### 4. Third-Party Assessment (3PAO)

In lieu of an internal executive self-attestation, a software producer may submit an independent third-party assessment conducted by a FedRAMP-accredited Third Party Assessment Organization (3PAO) verifying SSDF compliance.

# Applicability & Operational Impact

- **Target Entities**: Any commercial organization providing software (including off-the-shelf software, on-premises applications, container images, and software-as-a-service with on-premise components) to US federal agencies.
- **Centralized Submission via RSAA**: Attestation packages are submitted through CISA's online portal—the Repository for Software Attestations and Artifacts (RSAA)—where they are indexed for civilian and defense procurement officers.
- **Customer Auditing**: Enterprises outside the federal government now routinely demand CISA Common Form compliance in standard B2B vendor security questionnaires.

# Practical Implementation

### Enterprise Compliance Verification Checklist

Before routing the CISA Common Form to the CEO for signature, security compliance teams execute a mandatory verification audit:

```
[ ] Clause 1 (Environment):
    - Are all GitHub/GitLab accounts enforced with hardware security keys (FIDO2)?
    - Are CI build runners isolated, ephemeral, and barred from untrusted outbound traffic?
[ ] Clause 2 (Supply Chain):
    - Is an automated CycloneDX or SPDX SBOM generated for each production release?
    - Are all npm/Maven/PyPI dependencies locked by cryptographic hash in lockfiles?
[ ] Clause 3 (Automated Testing):
    - Does CI block release merges on critical/high SAST findings (CodeQL, Semgrep)?
    - Are container base images scanned for known CVEs prior to deployment?
[ ] Clause 4 (VDP & Patching):
    - Is a public SECURITY.md published with a monitored PGP disclosure mailbox?
    - Is there an agreed SLA for deploying critical vulnerability fixes within 14 days?
```

# Dates and Transitions

- **September 2022**: OMB Memorandum M-22-18 issued, mandating agency collection of software attestations.
- **June 2023**: OMB Memorandum M-23-16 extends timelines and instructs CISA to finalize the Common Form.
- **March 2024**: CISA publishes the final approved Common Form and launches the online RSAA portal.
- **June 11, 2024**: Major milestone: Federal agencies begin strictly mandating submitted attestations for all critical software acquisitions.

# Related concepts

- [NIST SP 800-218 SSDF](ssdf-nist-sp-800-218.md)
- [NTIA Minimum Elements](ntia-minimum-elements.md)
- [United States Jurisdiction Overview](../jurisdictions/united-states.md)
- [Software Producer Role](../roles/software-producer.md)
- [Software Consumer Role](../roles/software-consumer.md)

[^ntia-sbom-elements]: National Telecommunications and Information Administration (NTIA), The Minimum Elements For a Software Bill of Materials (SBOM), https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
