---
type: Standard
title: Sigstore Ecosystem
description: Standard for signing, verifying, and protecting software components using
  short-lived certificates (Fulcio) and transparency logs (Rekor).
category: standard
tags:
- supply-chain
- provenance
- attestation
- sigstore
status: draft
generated:
  by: agent:antigravity
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
  provision: Sigstore Ecosystem
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Sigstore Ecosystem** framework for build provenance and supply-chain integrity[^slsa-framework].

Standard for signing, verifying, and protecting software components using short-lived certificates (Fulcio) and transparency logs (Rekor).

# Integrity Assurances
Prevents tampering, unauthorized dependency injections, and forged build outputs.

# Related concepts
- [Attestation Frameworks Index](index.md)

[^slsa-framework]: OpenSSF SLSA Working Group, Supply chain Levels for Software Artifacts (SLSA) Specification v1.0, https://slsa.dev/spec/v1.0/
