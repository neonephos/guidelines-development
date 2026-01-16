# NeoNephos Project Onboarding Guidelines

## Normative Language

The key words **MUST**, **MUST NOT**, **REQUIRED**, **SHALL**, **SHALL NOT**, **SHOULD**, **SHOULD NOT**, **RECOMMENDED**, **MAY**, and **OPTIONAL** in this document are to be interpreted as described in [RFC 2119](https://www.rfc-editor.org/rfc/rfc2119.html) and [RFC 8174](https://www.rfc-editor.org/rfc/rfc8174.html).

## Purpose

The onboarding process ensures that new projects adopt baseline governance, technical, and operational practices before entering the NeoNephos lifecycle. Successful completion establishes trust with contributors, adopters, and the wider community.

---

## Onboarding Requirements

**Governance and Administration**

* **MUST** publish a project charter (canonical + Markdown).
* **MUST** adopt the Linux Foundation Code of Conduct.
* **MUST** provide `CONTRIBUTING.md` with DCO/CLA details.
* **MUST** document maintainers and TSC members publicly.
* **MUST** designate a Security Officer.

**Technical and Development Practices**

* **MUST** use LF-approved licenses (SPDX or REUSE).
* **MUST** enable CI for builds, tests, linting, and security scanning.
* **MUST** provide `SECURITY.md` with disclosure policy and contacts.
* **MUST** track third-party licenses.
* **SHOULD** tag and publish releases using Semantic Versioning.
* **SHOULD** generate SBOMs for released artifacts.

**Operations and Infrastructure**

* **MUST** transfer repositories to NeoNephos-administered GitHub/GitLab.
* **MUST** transfer domains via LF Project Control Center.
* **MUST** publish artifacts to NeoNephos-controlled registries.
* **MUST** enforce 2FA for all members.
* **MUST NOT** enable repository-level self-hosted GitHub Actions runners.
* **MUST** configure artifact and log retention (180 days private, 90 days public).

**Trademarks and Notices**

* **MUST** follow LF Europe trademark guidelines for names and logos.
* **MUST** reference NeoNephos in organizational `README.md`.
* **MUST** add LF-compliant footer to project websites.

**Community and Outreach**

* **MUST** provide user and developer documentation.
* **MUST** publish an initial roadmap with intention to graduate.
* **SHOULD** hold regular community calls.
* **SHOULD** report contributors, adoption, and releases.
* **MAY** provide mailing lists or chat channels.

**Security and Compliance**

* **MUST** appoint a Security Officer.
* **MUST** document any data collection with opt-out.
* **MUST** exclude PII from telemetry by default.
* **MUST** publish a Data Processing Notice if PII is collected (≤180 days).
* **SHOULD** sign release artifacts and provide provenance metadata.

**Funding and Acknowledgements**

* **MUST** obtain TAC approval for any external funding.
* **MUST** display funding acknowledgements when relevant.

---

## Completion

✅ Completion of onboarding requirements ensures that new projects are ready for sustained growth and alignment with NeoNephos governance, technical, and operational standards.