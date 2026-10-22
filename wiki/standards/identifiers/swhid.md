---
type: Standard
title: Software Heritage Persistent Identifier (SWHID)
description: Cryptographic identifier standard for referencing immutable source code
  artifacts, files, and revision graphs.
category: standard
tags:
- standard
- identifier
- swhid
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: swhid-spec
  resource: https://www.swhid.org/specification/v1.1/
  title: Software Heritage Persistent Identifier (SWHID) Specification v1.1
  author: Software Heritage / SWHID Working Group
  last_modified: '2023-09-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**SWHID (Software Heritage Persistent Identifier)** is an intrinsic cryptographic identifier standard for pointing unambiguously to source code artifacts archived in the universal Software Heritage library[^swhid-spec].

# Syntax Structure
`swh:1:[object_type]:[hash]`
- **Object Types**: `cnt` (content/file), `dir` (directory), `rev` (revision/commit), `rel` (release tag), `snp` (snapshot).
- **Deterministic Hashing**: Computed using standard SHA-1 or SHA-256 Merkle DAG algorithms over file contents and directory trees.

# Related concepts
- [OmniBOR](omnibor.md)
- [Package URL](package-url.md)

[^swhid-spec]: Software Heritage / SWHID Working Group, Software Heritage Persistent Identifier (SWHID) Specification v1.1, https://www.swhid.org/specification/v1.1/
