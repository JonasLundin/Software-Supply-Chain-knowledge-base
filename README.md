# Software Supply Chain Knowledge Base

An English-language [Open Knowledge Format (OKF)](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md) bundle covering software supply-chain integrity: SBOM formats, attestation and provenance frameworks, VEX forms, product identifiers, secure development frameworks, and the regulatory expectations from the EU, Germany, the United States, and international bodies that reference them.

The bundle contains concise original summaries with provision-level citations to primary sources. It does not reproduce full legal instruments, rules, guidance documents, or standards.

Current release: **0.1.0** (`VERSION` 0.1.0)

> **General orientation only:** do not rely on this knowledge base for decisions that determine, demonstrate, or materially affect legal or regulatory compliance. Verify the current primary sources and obtain qualified professional advice before making SBOM-scope, attestation, vulnerability-disposition, procurement, or other compliance-impacting decisions.

## Use With Meerkat

[Meerkat](https://github.com/zegit-zoo/meerkat) can serve the bundle as CLI, MCP, or HTTP without conversion:

```sh
mk --kb-dir . search "SBOM minimum elements"
mk --kb-dir . show standards/sbom-formats/spdx-3-0
mk --kb-dir . list --category standard
mk --kb-dir . mcp serve
mk --kb-dir . http serve --port 4004
```

Run these commands from the repository root. The knowledge bundle itself is under `wiki/`; Meerkat's `--kb-dir` reads that content-repository layout.

The Markdown remains fully usable directly or with any standard Markdown tool.

## Coverage

The corpus includes:

- **SBOM Formats**: SPDX 2.3, SPDX 3.0, ISO/IEC 5962:2021 (SPDX 2.2.1), CycloneDX 1.7 (ECMA-424 2nd ed), CycloneDX 1.6, CycloneDX 1.5, SWID tags, and CoSWID (RFC 9393);
- **Attestation & Provenance**: SLSA v1.2, SLSA v1.0, in-toto (CNCF Graduated), Sigstore, DSSE, and SCITT (IETF);
- **VEX Formats**: CSAF VEX (OASIS Profile 5), OpenVEX, and CycloneDX VEX;
- **Package & Artifact Identifiers**: Package URL (purl), Common Platform Enumeration (CPE), Software Heritage Persistent ID (SWHID), and OmniBOR (GitOID);
- **Frameworks**: NIST SSDF (SP 800-218), NIST SP 800-161r1, OpenSSF Scorecard, S2C2F, and OWASP SCVS;
- **Requirements & Law**: CRA SBOM mandate (Annex I Part II(1)) and supply chain obligations (Art 13(6), Art 24(3)), NIS2 Article 21(2)(d), prEN 40000-1-3, BSI TR-03183 Parts 1–3, CISA 2026 Minimum Elements, NTIA 2021, OMB M-22-18 / M-23-16, and EO 14028;
- **Procedures, Roles, Guidance, Jurisdictions, and Timeline**: Full lifecycle operational procedures, market roles, agency guidance, jurisdictional frameworks, and chronological milestones.

Coverage is measured in `coverage.yaml`. Each gate names a glob over `wiki/`, the expected number of concepts, and the count actually present.

## Structure

`kb.yaml` declares the bundle's slug, extension key (`x-software-supply-chain`), categories, and sections. Every section has an `index.md` indexing the concepts within.

| Section | Contents |
|---|---|
| [`standards/`](wiki/standards/index.md) | Technical specifications and frameworks across SBOM formats, attestations, VEX, identifiers, and security frameworks. |
| [`requirements/`](wiki/requirements/index.md) | Concrete regulatory and public procurement expectations across the EU, Germany, and the United States. |
| [`procedures/`](wiki/procedures/index.md) | Operational engineering practices for build integration, signing, verification, VEX authoring, and upstream fix sharing. |
| [`roles/`](wiki/roles/index.md) | Economic and supply chain roles: producer, consumer, distributor, open-source steward, build platform, package registry, and tool vendor. |
| [`law/`](wiki/law/index.md) | Statutory instruments summarised for their supply-chain provisions (CRA, NIS2, US Executive Orders). |
| [`guidance/`](wiki/guidance/index.md) | Official agency and community guidance (BSI, CISA, ENISA, NCSC, NTIA, OpenSSF). |
| [`jurisdictions/`](wiki/jurisdictions/index.md) | Jurisdictional supply chain policy profiles for EU, Germany, United States, United Kingdom, and Japan. |
| [`timeline/`](wiki/timeline/index.md) | Chronology of major specification ratifications, executive orders, and regulatory enforcement dates. |
| [`glossary/`](wiki/glossary/index.md) | Statutory and technical definitions including CRA Article 3 terms. |

## Source And Publication Policy

- Every concept cites primary, authoritative sources (official journals, standard bodies, government publications).
- Presumption of conformity is claimed only when an explicit reference is cited in the Official Journal of the European Union (OJEU).
- All files are validated against the bundle schema using `tools/validate.py`.
