---
type: Standard
title: SLSA v1.2 & Source Track Extensions
description: Advanced supply-chain integrity specification defining the SLSA Source Track, two-person code reviews, hermetic build environments, and reproducible verification.
category: standard
tags:
  - supply-chain
  - slsa
  - source-track
  - provenance
  - hermetic-builds
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
  - id: slsa-framework
    resource: https://slsa.dev/spec/v1.0/
    title: Supply chain Levels for Software Artifacts (SLSA) Specification v1.0
    author: OpenSSF SLSA Working Group
    last_modified: '2023-04-18T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  provision: SLSA v1.2 (Draft Specification & Source Track)
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**SLSA v1.2** represents the expansion of the Supply-chain Levels for Software Artifacts framework beyond the standalone Build Track into a unified multi-track verification model[^slsa-framework]. While SLSA v1.0 focused specifically on build platforms and provenance generation, SLSA v1.2 introduces formal specifications for the **Source Track**, criteria for hermetic builds, verification of package distribution channels, and standards for bit-for-bit reproducibility.

SLSA v1.2 directly supports the highest tier of secure software engineering mandated by global standards, such as NIST SP 800-218 (tasks PW.1.1, PW.2.1) and European cybersecurity product certification schemes.

```
+-------------------------------------------------------------+
|               SLSA v1.2 Comprehensive Framework             |
+-------------------------------------------------------------+
               |                               |
               v                               v
+-----------------------------+ +-----------------------------+
|        Source Track         | |         Build Track         |
|-----------------------------| |-----------------------------|
| Source L1: Version Control  | | Build L1: Provenance exists |
| Source L2: Verified History | | Build L2: Hosted platform   |
| Source L3: Two-Party Review | | Build L3: Hardened &        |
|            & Signed Commits | |           Hermetic Execution|
+-----------------------------+ +-----------------------------+
               |                               |
               +---------------+---------------+
                               |
                               v
+-------------------------------------------------------------+
|             Reproducible Builds & Package Track             |
|  - Bit-for-bit independent verification (Diffoscope)        |
|  - Immutable package registry distribution                  |
+-------------------------------------------------------------+
```

# Technical Scope / Normative Requirements

### 1. The SLSA Source Track

The Source Track addresses threats targeting source code repositories (unauthorized direct commits, account compromises, stealthy backdoors, and history rewrites):

| Level | Name | Technical Requirements |
| :--- | :--- | :--- |
| **Source L1** | **Version Controlled** | Every change is tracked in a version control system (e.g. Git) with revision history and commit timestamps retained indefinitely. |
| **Source L2** | **Verified History** | The source repository enforces immutable revision history; force-pushes are blocked. Every change is attributed to an authenticated identity, and cryptographic commit signing is encouraged. |
| **Source L3** | **Two-Person Review & Strong Authentication** | Every modification must be reviewed and approved by at least two distinct authenticated principals (author + independent reviewer). Branch protection enforces automated status checks; direct pushes to main branches are technically impossible. Mandatory phishing-resistant MFA (FIDO2/WebAuthn) for all contributors. |

### 2. Hermetic and Reproducible Build Criteria

SLSA v1.2 refines the criteria for top-tier build integrity:
- **Hermetic Execution**: Build tasks run in network-isolated sandboxes with zero internet egress during compilation. All dependencies, compilers, and tools are declared up-front as cryptographic hashes.
- **Reproducible Verification**: Multiple independent organizations can re-execute the build definition and obtain bit-for-bit identical binary outputs, proving the absence of compiler backdoors.

### Source Provenance Attestation Predicate

SLSA v1.2 formalizes source attestations describing repository policies and review proofs:

```json
{
  "_type": "https://in-toto.io/Statement/v1",
  "subject": [
    {
      "name": "git+https://github.com/acme/kernel-core",
      "digest": {
        "gitCommit": "e5c4a3b2a19876543210fedcba0987654321cafe"
      }
    }
  ],
  "predicateType": "https://slsa.dev/source/v1",
  "predicate": {
    "source": {
      "repository": "https://github.com/acme/kernel-core",
      "revision": "e5c4a3b2a19876543210fedcba0987654321cafe",
      "ruleset": "strict-enterprise-protection"
    },
    "review": {
      "twoPersonReview": true,
      "reviewers": [
        "https://github.com/alice-maintainer",
        "https://github.com/bob-security-lead"
      ],
      "approvedAt": "2026-09-27T08:15:00Z"
    }
  }
}
```

# Applicability & Operational Impact

- **Critical Infrastructure & High-Assurance Systems**: Applied to kernel modules, cryptographic libraries, hypervisors, and cloud control planes where developer workstation compromise is a major threat vector.
- **Enterprise Engineering Policies**: Requires integration with source control platform governance (GitHub branch protection rules, GitLab push rules, Gerrit change verification).
- **Audit and Attestation**: Supplies concrete, machine-verifiable evidence for SOC 2 Type II, ISO 27001, and federal self-attestation mandates.

# Practical Implementation

### Implementing Source L3 on GitHub

To satisfy Source L3 programmatically via GitHub Repository RuleSets:

```json
{
  "name": "SLSA Source L3 Protected Main",
  "target": "branch",
  "enforcement": "active",
  "conditions": {
    "ref_name": {
      "include": ["refs/heads/main"]
    }
  },
  "rules": [
    {
      "type": "pull_request",
      "parameters": {
        "required_approving_review_count": 2,
        "dismiss_stale_reviews_on_push": true,
        "require_code_owner_review": true,
        "require_last_push_approval": true
      }
    },
    {
      "type": "required_signatures"
    },
    {
      "type": "non_fast_forward"
    },
    {
      "type": "deletion"
    }
  ]
}
```

### Reproducible Rebuild Verification

```bash
# Execute independent rebuild in isolated container
docker run --rm --network none -v $(pwd):/workspace -w /workspace \
  -e SOURCE_DATE_EPOCH=1700000000 \
  repro-builder:1.0 make build

# Compare artifact against production build
diffoscope release-binary local-rebuild-binary
```

# Dates and Transitions

- **2023**: Launch of SLSA v1.0 with the Build Track.
- **2024–2025**: Publication of draft Source Track specifications and community pilot implementations.
- **2026**: Broad adoption of SLSA v1.2 multi-track verification across critical infrastructure and open-source foundations.

# Related concepts

- [SLSA v1.0 Specification](slsa-1-0.md)
- [in-toto Attestation Framework](in-toto.md)
- [Reproducible Builds Procedure](../../procedures/reproducible-builds.md)
- [Dependency Due Diligence](../../procedures/dependency-due-diligence.md)
- [Software Producer Role](../../roles/software-producer.md)

[^slsa-framework]: OpenSSF SLSA Working Group, Supply chain Levels for Software Artifacts (SLSA) Specification v1.0, https://slsa.dev/spec/v1.0/
