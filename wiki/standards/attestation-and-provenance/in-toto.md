---
type: Standard
title: in-toto Supply Chain Attestation Framework
description: CNCF Graduated framework for providing cryptographic proof of software
  supply chain integrity from commit to deployment.
category: standard
tags:
- standard
- attestation
- in-toto
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: in-toto-spec
  resource: https://in-toto.io/
  title: in-toto Attestation Framework Specification
  author: Cloud Native Computing Foundation (CNCF)
  last_modified: '2025-02-10T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**in-toto** is a Cloud Native Computing Foundation (CNCF) Graduated project (graduated February 10, 2025) that provides a comprehensive framework to cryptographically verify the integrity of the software supply chain[^in-toto-spec].

# Architectural Mechanics
- **Layouts and Steps**: An authorized project owner defines a supply chain layout specifying expected pipeline steps, authorized functionary keys, and artifact flow rules.
- **Link Metadata**: Each build step records signed link metadata capturing recorded materials (input hashes) and products (output hashes).
- **in-toto Attestation Predicates**: Standardized attestation envelope wrapping custom predicates such as SLSA provenance, SPDX SBOMs, and vulnerability scan results.

# Intellectual Property and Licensing
in-toto is an open-source project hosted by CNCF and licensed under the Apache License 2.0.

# Related concepts
- [SLSA v1.2](slsa-1-2.md)
- [Sigstore](sigstore.md)

[^in-toto-spec]: Cloud Native Computing Foundation (CNCF), in-toto Attestation Framework Specification, https://in-toto.io/
