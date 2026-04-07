# Security Guidelines — NeoNephos Foundation

<!-- TOC -->
* [Security Guidelines — NeoNephos Foundation](#security-guidelines--neonephos-foundation)
  * [1. Introduction](#1-introduction)
  * [2. Normative Language](#2-normative-language)
  * [3. Conformance Model](#3-conformance-model)
  * [4. Scope](#4-scope)
  * [5. Security Contact per Project](#5-security-contact-per-project)
    * [5.1 GitHub Private Vulnerability Reporting](#51-github-private-vulnerability-reporting)
    * [5.2 SECURITY.md](#52-securitymd)
  * [6. Vulnerability Response Process](#6-vulnerability-response-process)
    * [6.1 Acknowledgement](#61-acknowledgement)
    * [6.2 Triage and Severity Assessment](#62-triage-and-severity-assessment)
    * [6.3 Fix Coordination](#63-fix-coordination)
    * [6.4 CVE Assignment](#64-cve-assignment)
    * [6.5 Coordinated Disclosure](#65-coordinated-disclosure)
    * [6.6 Post-Disclosure](#66-post-disclosure)
  * [7. Severity Classification and Response SLAs](#7-severity-classification-and-response-slas)
  * [8. Supply Chain Security](#8-supply-chain-security)
    * [8.1 Artifact Signing](#81-artifact-signing)
    * [8.2 Build Provenance (SLSA)](#82-build-provenance-slsa)
    * [8.3 Software Bill of Materials (SBOM)](#83-software-bill-of-materials-sbom)
    * [8.4 Dependency Scanning](#84-dependency-scanning)
  * [9. Security Transparency](#9-security-transparency)
  * [10. Acknowledgements](#10-acknowledgements)
<!-- TOC -->

## 1. Introduction

This document defines the security guidelines for projects governed by the **NeoNephos Foundation**. It establishes requirements for vulnerability disclosure, incident response, and supply chain security that all NeoNephos projects must follow.

These guidelines complement the [NeoNephos Project Guidelines](../project-guidelines/project-guidelines.md), which reference this document in [Section 11 — Security](../project-guidelines/project-guidelines.md#11-security). Infrastructure-level security controls (2FA enforcement, GitHub Actions permissions, runner policies, and data retention) are defined in [Section 15.3 — Security and Compliance](../project-guidelines/project-guidelines.md#153-security-and-compliance) of the Project Guidelines and are not repeated here.

Related sections: [2 — Normative Language](#2-normative-language); [3 — Conformance Model](#3-conformance-model); [4 — Scope](#4-scope).

---

## 2. Normative Language

The key words **MUST**, **MUST NOT**, **REQUIRED**, **SHALL**, **SHALL NOT**, **SHOULD**, **SHOULD NOT**, **RECOMMENDED**, **MAY**, and **OPTIONAL** in this document are to be interpreted as described in [RFC 2119](https://www.rfc-editor.org/rfc/rfc2119.html) and [RFC 8174](https://www.rfc-editor.org/rfc/rfc8174.html).

Related sections: [3 — Conformance Model](#3-conformance-model).

---

## 3. Conformance Model

This document follows the same conformance model defined in the [NeoNephos Project Guidelines, Section 3](../project-guidelines/project-guidelines.md#3-conformance-model). Each guideline carries a *conformance priority statement* and a *resolution timeframe*. Enforcement follows the process described in [Section 13a — Enforcement and Remediation](../project-guidelines/project-guidelines.md#13a-enforcement-and-remediation) of the Project Guidelines.

---

## 4. Scope

This document covers:

- **Vulnerability disclosure and response**: How projects receive, handle, and disclose security vulnerabilities.
- **Supply chain security**: Requirements for signing, provenance, SBOMs, and dependency management of released artifacts.

This document does **not** cover:

- Infrastructure security controls (2FA, GitHub Actions, runners) — see [Project Guidelines §15.3](../project-guidelines/project-guidelines.md#153-security-and-compliance).
- OpenSSF Best Practices Badge requirements — see [Project Lifecycle Policy](../lifecycle-policy/project-lifecycle-policy.md).
- Governance, maintainer access, and operational policies — see [Project Guidelines](../project-guidelines/project-guidelines.md).

---

## 5. Security Contact per Project

### 5.1 GitHub Private Vulnerability Reporting

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Projects **MUST** enable [GitHub Private Vulnerability Reporting](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability) on all repositories that contain publishable code or artifacts. This is the primary channel for receiving vulnerability reports.

Projects **SHOULD** enable Private Vulnerability Reporting at the organization level to ensure newly created repositories inherit this setting.

### 5.2 SECURITY.md

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Projects **MUST** provide a `SECURITY.md` file in every repository that contains publishable code or artifacts. The `SECURITY.md` **MUST** include at minimum:

1. A link to the repository's GitHub Private Vulnerability Reporting page.
2. Supported versions: which release branches receive security updates.
3. The expected response timeline (referencing [Section 6](#6-vulnerability-response-process) of this document).

Projects **SHOULD** additionally provide an email address or alternative private channel for reporters who cannot use GitHub.

A template is available at [`../templates/SECURITY.md`](../templates/SECURITY.md).

Related sections: [6 — Vulnerability Response Process](#6-vulnerability-response-process); [7 — Severity Classification and Response SLAs](#7-severity-classification-and-response-slas).

---

## 6. Vulnerability Response Process

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Each project's TSC **MUST** designate at least two maintainers as security contacts responsible for handling vulnerability reports. These contacts **MUST** be documented in the project's `SECURITY.md`.

### 6.1 Acknowledgement

Projects **MUST** acknowledge receipt of a vulnerability report within **3 business days**. The acknowledgement **MUST** be sent via the same channel the report was received on (e.g., GitHub Security Advisory).

### 6.2 Triage and Severity Assessment

Projects **MUST** perform an initial triage within **7 calendar days** of receiving a report. Triage **MUST** include:

1. Validation: confirming whether the report describes a genuine vulnerability.
2. Severity assessment using [CVSS v3.1](https://www.first.org/cvss/v3.1/specification-document) or later.
3. Assignment of a severity level per [Section 7](#7-severity-classification-and-response-slas).

The reporter **SHOULD** be informed of the triage outcome and the planned remediation timeline.

### 6.3 Fix Coordination

Fix development **SHOULD** happen in a private fork or draft advisory within GitHub to prevent premature disclosure. The fix **MUST** be reviewed by at least one additional maintainer before merging.

If the vulnerability affects multiple NeoNephos projects, the reporting project's TSC **SHOULD** coordinate with the affected projects' TSCs before disclosure. The TAC **MAY** facilitate cross-project coordination.

### 6.4 CVE Assignment

| Priority   | Resolution      | Owner |
|------------|-----------------|-------|
| **SHOULD** | ASAP (≤30 days) | TSC   |

Projects **SHOULD** request a CVE identifier for confirmed vulnerabilities with a CVSS score ≥ 4.0 (Medium or higher). CVE identifiers **SHOULD** be obtained via [GitHub's CNA program](https://docs.github.com/en/code-security/security-advisories/working-with-repository-security-advisories/publishing-a-repository-security-advisory#requesting-a-cve-identification-number).

> **Practical note:** CVE assignment adds credibility and traceability but involves administrative overhead. Early-stage projects or projects with a small user base **MAY** defer CVE assignment until a stable release has been published and external adoption is established. The GitHub Security Advisory alone already provides adequate transparency for most cases.

### 6.5 Coordinated Disclosure

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Projects **MUST** follow a coordinated disclosure process:

1. **Embargo period**: The maximum embargo duration is **90 calendar days** from the date the report is acknowledged. During this period, details of the vulnerability **MUST NOT** be disclosed publicly.
2. **Disclosure**: Once a fix is available (or the embargo expires), the project **MUST** publish a [GitHub Security Advisory](https://docs.github.com/en/code-security/security-advisories/working-with-repository-security-advisories/publishing-a-repository-security-advisory) containing:
   - A description of the vulnerability.
   - Affected versions.
   - The CVSS score and vector.
   - The CVE identifier (if assigned).
   - Remediation steps or patched versions.
3. **Early disclosure**: If active exploitation is detected in the wild, the TSC **MAY** shorten the embargo period and disclose early with whatever fix or mitigation is available.

### 6.6 Post-Disclosure

After public disclosure:

- The fix **MUST** be released in a patch version for all supported release branches.
- The CVE and advisory **SHOULD** be referenced in the release notes of the patched version.
- Projects **SHOULD** conduct a retrospective for Critical and High severity vulnerabilities to identify process improvements.

Related sections: [5 — Security Contact per Project](#5-security-contact-per-project); [7 — Severity Classification and Response SLAs](#7-severity-classification-and-response-slas); [9 — Security Transparency](#9-security-transparency).

---

## 7. Severity Classification and Response SLAs

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Projects **MUST** classify vulnerabilities using [CVSS v3.1](https://www.first.org/cvss/v3.1/specification-document) or later and apply the following response SLAs:

| Severity     | CVSS Score | Fix SLA                | Disclosure SLA         |
|--------------|------------|------------------------|------------------------|
| **Critical** | 9.0 – 10.0 | ≤ 7 calendar days     | ≤ 14 calendar days     |
| **High**     | 7.0 – 8.9  | ≤ 30 calendar days    | ≤ 30 calendar days     |
| **Medium**   | 4.0 – 6.9  | ≤ 90 calendar days    | ≤ 90 calendar days     |
| **Low**      | 0.1 – 3.9  | Best effort            | Best effort            |

- **Fix SLA**: Time from triage completion to a fix being merged.
- **Disclosure SLA**: Time from triage completion to publishing a GitHub Security Advisory. The disclosure SLA **MUST NOT** exceed the 90-day embargo defined in [Section 6.5](#65-coordinated-disclosure).

If a project cannot meet a Fix SLA, the TSC **MUST** communicate an updated timeline to the reporter and publish a mitigation or workaround advisory. Transparent communication about delays is always preferable to silently missing a deadline.

Related sections: [6 — Vulnerability Response Process](#6-vulnerability-response-process); [6.5 — Coordinated Disclosure](#65-coordinated-disclosure).

---

## 8. Supply Chain Security

### 8.1 Artifact Signing

| Priority   | Resolution                                   | Owner |
|------------|----------------------------------------------|-------|
| **SHOULD** | When publishing artifacts to external consumers | TSC   |

Projects **SHOULD** sign all published release artifacts (container images, binaries, packages) using [Sigstore cosign](https://docs.sigstore.dev/cosign/signing/overview/) or an equivalent signing mechanism. Signing **SHOULD** be integrated into the CI/CD pipeline.

> **Practical note:** Artifact signing, build provenance, and SBOM generation (Sections 8.1–8.3) are intended to be adopted incrementally. Projects **SHOULD** prioritize dependency scanning ([Section 8.4](#84-dependency-scanning)) first, as it provides the highest security value with the least effort. The remaining supply chain practices can be introduced as the project matures and publishes artifacts to external consumers.

### 8.2 Build Provenance (SLSA)

| Priority   | Resolution                                   | Owner |
|------------|----------------------------------------------|-------|
| **SHOULD** | When publishing artifacts to external consumers | TSC   |

Projects **SHOULD** generate [SLSA](https://slsa.dev/) provenance attestations for published artifacts. The target level is at minimum [SLSA Build Level 2](https://slsa.dev/spec/v1.0/levels) (scripted build, hosted build platform).

Projects **MAY** use the [SLSA GitHub Generator](https://github.com/slsa-framework/slsa-github-generator) or equivalent tooling to generate and publish provenance attestations.

### 8.3 Software Bill of Materials (SBOM)

| Priority   | Resolution                                   | Owner |
|------------|----------------------------------------------|-------|
| **SHOULD** | When publishing artifacts to external consumers | TSC   |

Projects **SHOULD** generate a Software Bill of Materials (SBOM) for each published release artifact. SBOMs **MUST** use either [SPDX](https://spdx.dev/) or [CycloneDX](https://cyclonedx.org/) format.

SBOMs **SHOULD** be published alongside release artifacts (e.g., attached to GitHub releases or pushed to the OCI registry as a referrer).

### 8.4 Dependency Scanning

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Projects **MUST** enable automated dependency scanning to detect known vulnerabilities in direct and transitive dependencies for all repositories containing publishable code. Examples of acceptable tools include [Dependabot](https://docs.github.com/en/code-security/dependabot), [Renovate](https://docs.renovatebot.com/), or equivalent.

Projects **SHOULD** configure automated dependency update pull requests to reduce time-to-remediation.

Related sections: [Project Guidelines §15.3.2 — Supplemental Compliance](../project-guidelines/project-guidelines.md#1532-supplemental-compliance); [Project Guidelines §6 — Technical and Development Practices](../project-guidelines/project-guidelines.md#6-technical-and-development-practices).

---

## 9. Security Transparency

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Projects **MUST** publish security advisories for all confirmed vulnerabilities with a CVSS score ≥ 4.0 via [GitHub Security Advisories](https://docs.github.com/en/code-security/security-advisories/working-with-repository-security-advisories/about-repository-security-advisories).

Projects **MUST** reference CVE identifiers and advisory links in the release notes of patched versions.

Projects **SHOULD** maintain a public record of past security advisories accessible from the project's `SECURITY.md`.

Related sections: [6.6 — Post-Disclosure](#66-post-disclosure); [5.2 — SECURITY.md](#52-securitymd).

---

## 10. Acknowledgements

| Priority   | Resolution      | Owner |
|------------|-----------------|-------|
| **SHOULD** | ASAP (≤30 days) | TSC   |

Projects **SHOULD** credit security researchers who responsibly report vulnerabilities, unless the reporter requests anonymity. Acknowledgement **SHOULD** be included in the published GitHub Security Advisory and **MAY** also be included in release notes.

Related sections: [6.5 — Coordinated Disclosure](#65-coordinated-disclosure); [9 — Security Transparency](#9-security-transparency).
