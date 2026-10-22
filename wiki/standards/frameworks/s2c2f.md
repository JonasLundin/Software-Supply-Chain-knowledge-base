---
type: Standard
title: Secure Supply Chain Consumption Framework (S2C2F)
description: OpenSSF framework and maturity model focusing on securely consuming and
  vetting open-source software dependencies.
category: standard
tags:
- standard
- framework
- s2c2f
- openssf
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: openssf-s2c2f-spec
  resource: https://github.com/ossf/s2c2f
  title: Secure Supply Chain Consumption Framework (S2C2F) Specification
  author: Open Source Security Foundation (OpenSSF)
  last_modified: '2023-05-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **Secure Supply Chain Consumption Framework (S2C2F)** is an OpenSSF-ratified maturity model designed to protect development environments against malicious third-party dependencies[^openssf-s2c2f-spec].

# Four Maturity Levels
- **Level 1 (Ingest Control)**: Enforce package manager lockfiles, automated dependency scanning, and centralized internal package caches.
- **Level 2 (Active Defense)**: Scan ingested packages for malicious code, typo-squatting, and sudden account takeovers.
- **Level 3 (Deterministic Ingestion)**: Rebuild open-source components internally from verified source repositories or enforce signed SLSA provenance proofs.
- **Level 4 (Hardened Containment)**: Perform isolated hermetic builds and active behavioral dynamic sandboxing of all ingested third-party binaries.

# Related concepts
- [OpenSSF Scorecard](openssf-scorecard.md)
- [Dependency Due Diligence](../../procedures/dependency-due-diligence.md)

[^openssf-s2c2f-spec]: Open Source Security Foundation (OpenSSF), Secure Supply Chain Consumption Framework (S2C2F) Specification, https://github.com/ossf/s2c2f
