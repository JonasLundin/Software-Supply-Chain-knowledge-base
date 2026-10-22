---
type: Standard
title: OpenVEX Specification
description: Lightweight, embeddable VEX specification designed for minimal overhead
  in container, package, and SBOM ecosystems.
category: standard
tags:
- standard
- vex
- openvex
- format
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: openvex-spec
  resource: https://github.com/openvex/spec
  title: OpenVEX Specification Version 0.2.0
  author: OpenVEX Project
  last_modified: '2023-08-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**OpenVEX** is an open, lightweight format for exchanging vulnerability assertions, developed by the independent OpenVEX open-source project and designed in alignment with CISA minimum VEX requirements[^openvex-spec].

> [!NOTE]
> **Governance Notice**: OpenVEX is hosted under the `openvex` GitHub organization (originally initiated by Chainguard in collaboration with community partners), not under the OpenSSF. Tooling such as `vexctl` is maintained by the OpenVEX community.

# Core Document Structure
OpenVEX documents use JSON-LD to declare concise exploitability assessments:
- **`@context` and `@id`**: Establishes schema semantics and unique statement URI.
- **`author` and `timestamp`**: Documents the entity asserting exploitability status.
- **`statements`**: Array of assertions linking specific CVE identifiers to product packages (via purl) with status values (`not_affected`, `affected`, `fixed`, `under_investigation`).

# Intellectual Property and Licensing
OpenVEX is an open-source specification and tool suite licensed under the Apache License 2.0.

# Related concepts
- [CSAF VEX](csaf-vex.md)
- [CycloneDX VEX](cyclonedx-vex.md)
- [CVD Knowledge Base](https://github.com/JonasLundin/CVD-knowledge-base)

[^openvex-spec]: OpenVEX Project, OpenVEX Specification Version 0.2.0, https://github.com/openvex/spec
