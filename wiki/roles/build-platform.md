---
type: Role
title: "Role: Build Platform / CI Provider"
description: Infrastructure or hosted service executing software compilation, packaging,
  and issuing provenance attestations.
category: role
tags:
- supply-chain
- role
- ci-cd
- slsa
- provenance
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: slsa-framework
  resource: https://slsa.dev/
  title: Supply chain Levels for Software Artifacts (SLSA) Specification v1.0
  author: OpenSSF SLSA Working Group
  last_modified: '2023-04-18T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: guidance
  instrument_status: in_force
  provision: SLSA v1.0 / in-toto Framework
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

A **Build Platform** is the hosted infrastructure, orchestration service, or CI/CD runner environment (e.g., GitHub Actions, GitLab CI, Google Cloud Build, Tekton) responsible for transforming source code into distributable software artifacts[^slsa-framework].

In modern supply-chain frameworks such as SLSA (Supply-chain Levels for Software Artifacts), the build platform is the central trust boundary for generating verifiable provenance.

# Key Security Properties & Requirements

Under SLSA v1.0, an authorized build platform must satisfy rigorous isolation and verification guarantees:
- **Build Isolation**: Builds must execute in isolated, ephemeral environments to prevent lateral tampering between tenants or sequential jobs.
- **Hermeticity & Reproducibility**: High-assurance build platforms support network-isolated (hermetic) builds where all inputs are declared and immutable.
- **Non-Forgeable Provenance**: The platform itself—not the build script or developer—cryptographically signs the provenance payload using platform-managed keys (e.g. via Sigstore Fulcio and OpenID Connect tokens).

# Related concepts
- [SLSA v1.0 Framework](../standards/attestation-and-provenance/slsa-1-0.md)
- [Sigstore Ecosystem](../standards/attestation-and-provenance/sigstore.md)
- [Automated SBOM Generation at Build Time](../procedures/sbom-generation-at-build.md)

[^slsa-framework]: OpenSSF SLSA Working Group, Supply chain Levels for Software Artifacts (SLSA) Specification v1.0, https://slsa.dev/
