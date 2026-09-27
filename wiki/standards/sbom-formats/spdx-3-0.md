---
type: Standard
title: Software Package Data Exchange (SPDX) 3.0
description: Next-generation object-oriented software supply chain metadata model
  spanning software, AI, hardware, and security profiles.
category: standard
tags:
- standard
- sbom
- spdx
- format
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-06-30T00:00:00Z'
sources:
- id: spdx-3-0-spec
  resource: https://spdx.github.io/spdx-spec/v3.0.1/
  title: Software Package Data Exchange (SPDX) Specification Version 3.0.1
  author: Linux Foundation (SPDX Workgroup)
  last_modified: '2024-04-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**SPDX 3.0** (released in April 2024) transforms the SPDX standard into a modular, graph-based object model capable of describing software, security vulnerabilities, AI model training sets, and hardware supply chains[^spdx-3-0-spec].

# Profile-Based Architecture
Unlike legacy single-document models, SPDX 3.0 adopts an extensible profile architecture built on an ontological core:
- **Core Profile**: Defines universal elements including `Element`, `SpdxDocument`, `Agent`, `CreationInfo`, and `Relationship`.
- **Software Profile**: Houses traditional software packaging concepts (`Package`, `File`, `Snippet`) with dependency graphs.
- **Security Profile**: Integrates native vulnerability tracking (`Vulnerability`, `VulnAssessmentRelationship`, and VEX status assessments).
- **Licensing Profile**: Expresses license declarations, complex boolean license expressions, and exceptions.
- **Build / Provenance Profile**: Captures build lifecycle events, builder identities, source inputs, and configuration parameters compatible with SLSA attestations.
- **AI Profile**: Represents machine learning datasets, model parameters, fine-tuning artifacts, and training infrastructure.

# Intellectual Property and Licensing
The SPDX Specification is published by the Linux Foundation under the Creative Commons Attribution 3.0 Unported (CC-BY-3.0) license.

# Related concepts
- [SPDX 2.3](spdx-2-3.md)
- [CISA 2026 Minimum Elements](../../requirements/united-states/cisa-minimum-elements-2026.md)
- [CSAF VEX](../vex/csaf-vex.md)

[^spdx-3-0-spec]: Linux Foundation (SPDX Workgroup), Software Package Data Exchange (SPDX) Specification Version 3.0.1, https://spdx.github.io/spdx-spec/v3.0.1/
