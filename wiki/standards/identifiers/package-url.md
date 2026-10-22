---
type: Standard
title: Package URL (purl) Specification
description: Standardized URI specification to identify and locate software packages
  across package managers and programming languages.
category: standard
tags:
- standard
- identifier
- purl
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
sources:
- id: package-url-spec
  resource: https://github.com/package-url/purl-spec
  title: Package URL (purl) Specification
  author: Package URL Community
  last_modified: '2024-01-01T00:00:00Z'
x-software-supply-chain:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

A **Package URL (purl)** is a standardized string format used to reliably identify and locate software packages across programming languages, package managers, and operating system distributions[^package-url-spec].

# Syntax Structure
`pkg:type/namespace/name@version?qualifiers#subpath`
- **`type`**: The package manager or ecosystem (e.g., `maven`, `npm`, `pypi`, `cargo`, `golang`, `deb`, `rpm`).
- **`namespace`**: Optional vendor, organization, or group prefix (e.g., `@angular`, `org.apache.commons`).
- **`name`**: The canonical package name.
- **`version`**: The package version string or commit.
- **`qualifiers`**: Optional key-value query parameters (e.g., repository URL, architecture).
- **`subpath`**: Optional relative path within the package.

# Operational Value
- Enables deterministic vulnerability matching across CVE, OSV, and vulnerability databases.
- Serves as the primary standardized component identifier across CycloneDX, SPDX 2.3, and SPDX 3.0.

# Intellectual Property and Licensing
The Package URL specification is an open specification published under the MIT License.

# Related concepts
- [Common Platform Enumeration (CPE)](cpe.md)
- [Software Heritage ID (SWHID)](swhid.md)

[^package-url-spec]: Package URL Community, Package URL (purl) Specification, https://github.com/package-url/purl-spec
