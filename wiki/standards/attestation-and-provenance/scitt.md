---
type: Standard
title: Supply Chain Integrity, Transparency, and Trust (SCITT)
description: IETF standard establishing verifiable transparency logs and notarization
  receipts for supply chain artifacts.
category: standard
tags:
- standard
- attestation
- scitt
- transparency
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: scitt-ietf
  resource: https://datatracker.ietf.org/wg/scitt/about/
  title: Supply Chain Integrity, Transparency, and Trust (SCITT) Working Group
  author: Internet Engineering Task Force (IETF)
  last_modified: '2024-03-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **Supply Chain Integrity, Transparency, and Trust (SCITT)** architecture is an IETF standardization initiative defining verifiable, immutable transparency services for software and physical supply chain claims[^scitt-ietf].

# Technical Mechanics
- **Signed Statements**: Entities submit signed assertions (such as SBOM attestations or security evaluations) encapsulated in COSE structures.
- **Transparency Notarization**: SCITT Transparency Services validate signatures and emit verifiable inclusion proofs (Receipts) rooted in verifiable ledger trees.
- **Independent Verification**: Consumers verify receipts without establishing direct synchronous trust relationships with upstream suppliers.

# Intellectual Property and Licensing
IETF documents are published under the IETF Trust legal rules.

# Related concepts
- [Sigstore](sigstore.md)
- [in-toto Attestation](in-toto.md)

[^scitt-ietf]: Internet Engineering Task Force (IETF), Supply Chain Integrity, Transparency, and Trust (SCITT) Working Group, https://datatracker.ietf.org/wg/scitt/about/
