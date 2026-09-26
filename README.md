# Software Supply Chain Knowledge Base

An English-language [Open Knowledge Format (OKF)](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md) bundle covering software supply-chain integrity: the SBOM formats, attestation and provenance frameworks, VEX forms, product identifiers and secure-development frameworks in use, and the regulatory expectations from the EU, Germany, the United States and others that reference them.

The bundle will contain concise original summaries with provision-level citations to primary sources. It does not reproduce full legal instruments, rules, guidance documents, or standards.

Current release: **none yet** (`VERSION` 0.0.0)

> **Scaffold:** the manifest, section structure, validator and registers are in place. No concepts have been ingested yet; every section index describes what will go there.

> **General orientation only:** once populated, do not rely on this knowledge base for decisions that determine, demonstrate, or materially affect legal or regulatory compliance. Verify the current primary sources and obtain qualified professional advice before making SBOM-scope, attestation, vulnerability-disposition, procurement, or other compliance-impacting decisions.

## Use With Meerkat

[Meerkat](https://github.com/zegit-zoo/meerkat) can serve the bundle as CLI, MCP, or HTTP without conversion:

```sh
mk --kb-dir . search "SBOM minimum elements"
mk --kb-dir . show standards/sbom-formats/spdx-3-0
mk --kb-dir . list --category law
mk --kb-dir . mcp serve
mk --kb-dir . http serve --port 4004
```

Run these commands from the repository root. The knowledge bundle itself is under `wiki/`; Meerkat's `--kb-dir` reads that content-repository layout. The paths above are the planned concept IDs and resolve once ingestion has reached them.

The Markdown remains usable without Meerkat or any other tool.

## Coverage

The intended corpus includes:

- SPDX, CycloneDX, SWID and CoSWID as SBOM formats;
- in-toto, SLSA, DSSE, Sigstore and SCITT for attestation and provenance;
- OpenVEX, CSAF VEX and CycloneDX VEX;
- package URL, CPE, SWHID and other identifiers;
- NIST SSDF, SP 800-161, OpenSSF Scorecard, S2C2F and OWASP SCVS;
- regulatory expectations from the CRA, prEN 40000-1-3, BSI TR-03183-2, NTIA and CISA minimum elements, US executive orders and memoranda;
- procedures, roles, guidance, jurisdictions and timeline.

Coverage is measured in `coverage.yaml`. Each gate names a glob over `wiki/`, the expected number of concepts where the corpus is finite, and the count actually present. A missing official source is recorded as a research gap rather than filled by inference.

## Structure

`kb.yaml` declares the bundle's slug, extension key (`x-software-supply-chain`), categories and sections. Every section has an `index.md` describing what belongs there.

| Section | Contents |
|---|---|
| [`standards/`](wiki/standards/index.md) | Specifications and frameworks, recorded as identifiers, versions, scope, relationships and links. |
| [`requirements/`](wiki/requirements/index.md) | What regulators and public buyers expect of SBOMs, attestations and dependency due diligence. |
| [`procedures/`](wiki/procedures/index.md) | Generating SBOMs at build, depth and completeness, distribution and access control, signing and attestation, verification, vulnerability matching, VEX exchange, reproducible builds, provenance verification, dependency due diligence, upstream fix sharing. |
| [`roles/`](wiki/roles/index.md) | Producer, consumer, distributor, open-source steward, build platform, package registry, tool vendor. |
| [`law/`](wiki/law/index.md) | Legal instruments summarised for their supply-chain provisions, with pointers to the sibling bundles for the rest. |
| [`guidance/`](wiki/guidance/index.md) | Official and community guidance. |
| [`jurisdictions/`](wiki/jurisdictions/index.md) | One page per jurisdiction with SBOM, attestation or provenance expectations, naming the instrument, the authority and the date. |
| [`timeline/`](wiki/timeline/index.md) | Executive Order 14028, NTIA 2021, SPDX as ISO/IEC 5962, CycloneDX as ECMA-424, SLSA 1.0 and 1.2, SPDX 3.0, CISA 2026 minimum elements, CRA dates. |
| [`glossary/`](wiki/glossary/index.md) | Terms as defined by the specifications and by CRA Article 3. |

## Source And Publication Policy

- Binding claims cite the publishing organisation's official specification site, an official government publication, or the OJEU or EUR-Lex for EU law.
- Official guidance is labelled non-binding.
- A standard provides presumption of conformity only when its reference is cited in the OJEU for the requirements concerned.
- Publicly accessible drafts are linked, not copied.
- Specification pages record version, publisher, licence pointer and scope; they never copy schema text.
- Regulatory requirement pages cite the exact provision or section and label whether it is binding, contractual or guidance.
- Agent-generated content stays `status: draft` until a human verifies it against the cited source.
- Superseded material is retained and marked rather than silently deleted.

This repository is not legal advice, is not a conformity assessment, does not certify any product or organisation, and must not be used as the basis for compliance-impacting decisions.

## Validate

```sh
python3 -m pip install -r requirements-dev.txt
python3 -m unittest tools/test_validate.py
python3 tools/validate.py wiki
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Corrections with exact primary-source citations are welcome. Do not submit copied standards text, private compliance evidence, or confidential information.

## Related Knowledge Bases

- [CRA-knowledge-base](https://github.com/JonasLundin/CRA-knowledge-base): Regulation (EU) 2024/2847, the Cyber Resilience Act
- [NIS2-knowledge-base](https://github.com/JonasLundin/NIS2-knowledge-base): Directive (EU) 2022/2555 and its national transpositions
- [CVD-knowledge-base](https://github.com/JonasLundin/CVD-knowledge-base): coordinated vulnerability disclosure, the CVE Program, CSAF, VEX and scoring
- [AI-Act-knowledge-base](https://github.com/JonasLundin/AI-Act-knowledge-base): Regulation (EU) 2024/1689 as amended
- [Conformity-Assessment-knowledge-base](https://github.com/JonasLundin/Conformity-Assessment-knowledge-base): the New Legislative Framework, modules, accreditation and notified bodies
- [NIST-CSF-knowledge-base](https://github.com/JonasLundin/NIST-CSF-knowledge-base): NIST Cybersecurity Framework 2.0
- [knowledge-base-template](https://github.com/JonasLundin/knowledge-base-template): the shared template every bundle in the series is built from

## Licence

Original summaries, structure, and metadata are licensed under [CC BY 4.0](LICENSE). Source documents, rules, specifications and standards retain their own terms; see [NOTICE](NOTICE).

This project is independent and is not affiliated with or endorsed by the Linux Foundation, SPDX, OpenSSF, OWASP, CycloneDX, Ecma International, OASIS, CISA, NTIA, NIST, BSI, ENISA, the European Commission, ISO, IEC, Google Cloud, or Meerkat. Repository: https://github.com/JonasLundin/Software-Supply-Chain-knowledge-base
