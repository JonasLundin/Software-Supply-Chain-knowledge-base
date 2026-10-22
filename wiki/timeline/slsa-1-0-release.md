---
type: Timeline
title: Release of SLSA v1.0 Specification
description: Milestone event marking the official ratification of SLSA v1.0 by the
  OpenSSF on April 18, 2023.
category: timeline
tags:
- timeline
- slsa
- milestone
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: slsa-spec-v1-0
  resource: https://slsa.dev/spec/v1.0/
  title: Supply chain Levels for Software Artifacts (SLSA) Specification v1.0
  author: OpenSSF SLSA Working Group
  last_modified: '2023-04-18T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Milestone

On **April 18, 2023**, the Open Source Security Foundation (OpenSSF) officially published **SLSA v1.0**[^slsa-spec-v1-0].

# Significance
- Established the foundational multi-level Build Track for software artifact provenance.
- Introduced formal distinctions between author claims and verifiable builder platform attestations.

# Related concepts
- [SLSA v1.0 (Superseded)](../standards/attestation-and-provenance/slsa-1-0.md)
- [SLSA v1.2](../standards/attestation-and-provenance/slsa-1-2.md)

[^slsa-spec-v1-0]: OpenSSF SLSA Working Group, Supply chain Levels for Software Artifacts (SLSA) Specification v1.0, https://slsa.dev/spec/v1.0/# Summary

**18 April 2023**: OpenSSF officially releases **Supply-chain Levels for Software Artifacts (SLSA) Version 1.0**[^slsa-spec-v1-0], establishing the definitive security framework for build and provenance integrity.

# Structural Evolution of the Specification

SLSA 1.0 introduced a modular architecture dividing supply-chain security controls into dedicated tracks, prioritizing the Build track across three distinct operational levels (Build L1, Build L2, Build L3). The specification defines verifiable criteria ensuring that build platforms generate authenticated, non-forgeable in-toto provenance statements that document the complete source-to-binary compilation lifecycle, shielding artifacts from unauthorized tampering and injection attacks during build automation.

# Related concepts
- [Timeline Index](index.md)
- [SLSA 1.0 Specification](../standards/attestation-and-provenance/slsa-1-0.md)
- [SLSA 1.2 Specification](../standards/attestation-and-provenance/slsa-1-2.md)

[^slsa-spec-v1-0]: OpenSSF, Supply-chain Levels for Software Artifacts (SLSA) v1.0, https://slsa.dev/
