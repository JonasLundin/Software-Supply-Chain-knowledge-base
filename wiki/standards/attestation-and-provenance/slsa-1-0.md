---
type: Standard
title: Supply chain Levels for Software Artifacts (SLSA) v1.0
description: Baseline release of the SLSA specification establishing the single Build
  Track model.
category: standard
tags:
- standard
- attestation
- provenance
- slsa
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-06-30T00:00:00Z'
sources:
- id: slsa-spec-v1-0
  resource: https://slsa.dev/spec/v1.0/
  title: Supply chain Levels for Software Artifacts (SLSA) Specification v1.0
  author: OpenSSF SLSA Working Group
  last_modified: '2023-04-18T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: superseded
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**SLSA v1.0**, published in April 2023, established the foundational architecture for supply chain provenance by formalizing the Build Track into Levels 1 through 3[^slsa-spec-v1-0].

> [!NOTE]
> **Superseded Standard**: SLSA v1.0 is superseded by [SLSA v1.2](slsa-1-2.md), which adds the Source Track.

# Architectural Scope
SLSA v1.0 decoupled the original monolithic SLSA 0.1 draft into individual tracks, debuting with the Build Track:
- **Focus on Provenance**: Generating authentic metadata documenting how software artifacts were produced from source inputs.
- **Separation of Concerns**: Establishing boundaries between builder identity and source repository authentication.

# Intellectual Property and Licensing
SLSA is licensed under the Apache License 2.0.

# Related concepts
- [SLSA v1.2](slsa-1-2.md)
- [in-toto Attestation](in-toto.md)

[^slsa-spec-v1-0]: OpenSSF SLSA Working Group, Supply chain Levels for Software Artifacts (SLSA) Specification v1.0, https://slsa.dev/spec/v1.0/
