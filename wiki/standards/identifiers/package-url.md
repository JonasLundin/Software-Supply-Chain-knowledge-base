---
type: Concept
title: Package URL (purl) Specification
description: Standardized URI specification to identify and locate software packages
  across package managers and programming languages.
category: standard
tags:
- software-supply-chain
- standards
- identifiers
- purl
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: regulation-eu-2024-2847
  resource: http://data.europa.eu/eli/reg/2024/2847/oj
  title: Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products
    with digital elements (Cyber Resilience Act)
  author: European Parliament and Council of the European Union
  last_modified: '2024-11-20T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

A **Package URL (purl)** is a standardized string format used to reliably identify and locate software packages across ecosystems (e.g., maven, npm, pypi, cargo, deb, rpm)[^regulation-eu-2024-2847].

# Syntax Schema
`pkg:type/namespace/name@version?qualifiers#subpath`

# Operational Value
- Enables deterministic vulnerability matching against CVE, OSV, and GitHub advisory databases.
- Essential mandatory component identifier in CycloneDX and SPDX 3.0.

# Related concepts
- [Identifiers Index](index.md)
- [Package URL Glossary](../../glossary/package-url.md)

[^regulation-eu-2024-2847]: European Parliament and Council of the European Union, Regulation (EU) 2024/2847 on horizontal cybersecurity requirements for products with digital elements (Cyber Resilience Act), http://data.europa.eu/eli/reg/2024/2847/oj
