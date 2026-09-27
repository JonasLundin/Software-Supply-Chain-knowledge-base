---
type: Standard
title: OmniBOR (Omnibus Bill of Materials)
description: Cryptographic artifact dependency graph standard using Git Object IDs
  (GitOIDs) for bit-level artifact verification.
category: standard
tags:
- standard
- identifier
- omnibor
- gitoid
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: omnibor-spec
  resource: https://github.com/omnibor/spec
  title: OmniBOR Specification
  author: OmniBOR Community / Linux Foundation
  last_modified: '2023-04-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**OmniBOR** is an open standard under the Linux Foundation defining an intrinsic cryptographic identifier and input-dependency graph for software artifacts based on Git Object IDs (GitOIDs)[^omnibor-spec].

# Technical Capabilities
- **Compiler-Assisted Tracking**: Integrated into toolchains (such as Clang/LLVM) to emit artifact dependency trees during binary compilation.
- **Exact Provenance**: Traces compiled binary objects directly back to exact source file hashes without reliance on package names or version strings.

# Related concepts
- [Software Heritage ID (SWHID)](swhid.md)
- [Package URL](package-url.md)

[^omnibor-spec]: OmniBOR Community / Linux Foundation, OmniBOR Specification, https://github.com/omnibor/spec
