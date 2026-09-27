---
type: Procedure
title: 'Procedure: Reproducible Builds Verification'
description: Configuring deterministic compilation to ensure bit-for-bit identical
  outputs independently verifiable from source.
category: procedure
tags:
- supply-chain
- procedure
- reproducible-builds
- slsa
- determinism
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
  authority_level: guidance
  instrument_status: in_force
  provision: SLSA Build Track / Reproducible Builds Project
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Reproducible Builds** is a development and build practice providing mathematical proof that a distributed binary artifact was compiled faithfully from a specific source code commit without backdoors or uncommitted modifications[^slsa-framework].

By eliminating non-deterministic factors (timestamps, filesystem order, locale settings, compiler paths), multiple independent parties can compile the source code and obtain bit-for-bit identical cryptographic hashes.

# Technical Determinism Workflow

```
+------------------+       Deterministic Build       +------------------+
|   Source Code    | ==============================> | Compiled Binary  |
| Commit: 4a9f3b1  |    (Stripped timestamps,        | SHA-256: e3b0c44 |
+------------------+     fixed build path,           +------------------+
                         pinned compilers)                     ^
                                                               | Bit-for-bit
+------------------+       Independent Rebuild                 | match
|   Source Code    | ==============================> | Rebuilt Binary   |
| Commit: 4a9f3b1  |    (Executed on separate        | SHA-256: e3b0c44 |
+------------------+     clean-room builder)         +------------------+
```

### Key Engineering Steps
1. **Source Pinned Dependencies**: Pin exact cryptographic checksums of all compilers, build tools, and dependencies.
2. **Normalize Timestamps**: Set `SOURCE_DATE_EPOCH` to a fixed unix timestamp (e.g. the commit timestamp) across all archive and binary creation tools.
3. **Sort File Sequences**: Sort file inputs lexicographically before feeding them into linkers, tarballs, or ZIP packaging engines.
4. **Independent Attestation**: Rebuilders publish cryptographic attestations verifying that their independently compiled artifact matches the official release hash.

# Related concepts
- [SLSA v1.0 Framework](../standards/attestation-and-provenance/slsa-1-0.md)
- [Automated SBOM Generation at Build Time](sbom-generation-at-build.md)
- [Build Platform Role](../roles/build-platform.md)

[^slsa-framework]: OpenSSF SLSA Working Group, Supply chain Levels for Software Artifacts (SLSA) Specification v1.0, https://slsa.dev/spec/v1.0/
