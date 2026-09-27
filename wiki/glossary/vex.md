---
type: Glossary
title: Vulnerability Exploitability eXchange (VEX)
description: A machine-readable assertion communicating whether a product is actually
  affected by a specific vulnerability.
category: glossary
tags:
- supply-chain
- glossary
- vex
status: draft
generated:
  by: agent:antigravity
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: ntia-sbom-elements
  resource: https://www.ntia.gov/files/ntia/publications/sbom_minimum_elements_report.pdf
  title: The Minimum Elements For a Software Bill of Materials (SBOM)
  author: National Telecommunications and Information Administration (NTIA)
  last_modified: '2021-07-12T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: guidance
  instrument_status: in_force
  provision: Vulnerability Exploitability eXchange (VEX)
  checked_at: '2026-09-27T00:00:00Z'
---

# Definition

**Vulnerability Exploitability eXchange (VEX)** is a machine-readable security advisory format that asserts the actual exploitability status of specific vulnerabilities within a software product or component[^ntia-sbom-elements].

# Role in Noise Reduction

While an SBOM reveals the presence of a third-party component, automated vulnerability scanners often flag components as vulnerable even when the vulnerable code path is never executed, uncalled, or mitigated by compiler flags. VEX solves this false-positive overload by allowing software producers to publish authoritative assertions—such as `not_affected`, `affected`, `fixed`, or `under_investigation`—allowing consumers to prioritize immediate threats and avoid investigating non-exploitable findings.

# Related concepts
- [Glossary Index](index.md)
- [OpenVEX Standard](../standards/vex/openvex.md)
- [CSAF VEX Standard](../standards/vex/csaf-vex.md)

[^ntia-sbom-elements]: OpenVEX Working Group, OpenVEX Specification, https://github.com/openvex/spec
