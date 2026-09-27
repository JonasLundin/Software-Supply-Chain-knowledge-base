# Procedures

Generating SBOMs at build, depth and completeness, distribution and access control, signing and attestation, verification, vulnerability matching, VEX exchange, reproducible builds, provenance verification, dependency due diligence, upstream fix sharing.

## Concepts

- [Procedure: Dependency Due Diligence and Governance](dependency-due-diligence.md) — Continuous auditing of open source components for license compliance, malicious code injection, and abandoned maintenance.
- [Procedure: Reproducible Builds Verification](reproducible-builds.md) — Configuring deterministic compilation to ensure bit-for-bit identical outputs independently verifiable from source.
- [Automated SBOM Generation in Build Pipelines](sbom-generation-at-build.md) — Comprehensive engineering procedure for integrating automated, high-fidelity Software Bill of Materials generation into CI/CD build environments.
- [Cryptographic Signing and Integrity Verification of SBOMs](sbom-verification-and-signing.md) — Operational procedure for cryptographically binding Software Bills of Materials to release artifacts and verifying attestation signatures prior to deployment.
- [Procedure: Vulnerability Correlation and VEX Authoring](vulnerability-matching-and-vex.md) — Ingesting SBOMs, matching package URLs (purl) against CVE feeds, and emitting authoritative VEX statements.
