# Security Guidelines — NeoNephos Foundation

<!-- TOC -->
* [Security Guidelines — NeoNephos Foundation](#security-guidelines--neonephos-foundation)
  * [1. Introduction](#1-introduction)
  * [2. Normative Language](#2-normative-language)
  * [3. Conformance Model](#3-conformance-model)
  * [4. Scope](#4-scope)
  * [5. Security Contact per Project](#5-security-contact-per-project)
    * [5.1 Private Vulnerability Intake Channel](#51-private-vulnerability-intake-channel)
      * [5.1.1 GitHub](#511-github)
      * [5.1.2 GitLab](#512-gitlab)
      * [5.1.3 Other Platforms and Self-Hosted Setups](#513-other-platforms-and-self-hosted-setups)
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
    * [8.5 Container Image Scanning](#85-container-image-scanning)
    * [8.6 License Compliance Scanning](#86-license-compliance-scanning)
  * [9. Security Transparency](#9-security-transparency)
  * [10. Operational Security Controls](#10-operational-security-controls)
    * [10.1 Authentication](#101-authentication)
    * [10.2 CI/CD Security](#102-cicd-security)
    * [10.3 Branch Protection](#103-branch-protection)
    * [10.4 Secret Scanning and Prevention](#104-secret-scanning-and-prevention)
    * [10.5 Access Governance](#105-access-governance)
    * [10.6 Code Quality and Scanning](#106-code-quality-and-scanning)
    * [10.7 Data Retention](#107-data-retention)
    * [10.8 Security Assessment](#108-security-assessment)
    * [10.9 Automated Security Posture Verification](#109-automated-security-posture-verification)
  * [11. Acknowledgements](#11-acknowledgements)
<!-- TOC -->

## 1. Introduction

This document defines the security guidelines for projects governed by the **NeoNephos Foundation**. It establishes requirements for vulnerability disclosure, incident response, supply chain security, and operational security controls that all NeoNephos projects must follow.

These guidelines complement the [NeoNephos Project Guidelines](../project-guidelines/project-guidelines.md), which reference this document in [Section 11 — Security](../project-guidelines/project-guidelines.md#11-security). Some operational security controls defined here overlap with [Section 15.3 — Security and Compliance](../project-guidelines/project-guidelines.md#153-security-and-compliance) of the Project Guidelines; this document provides the normative requirements while the Project Guidelines retain the operational context.

These guidelines build on established open source security standards — in particular the [OpenSSF Security Baseline](https://baseline.openssf.org/), [SLSA](https://slsa.dev/), and the [OpenSSF Best Practices Badge](https://www.bestpractices.dev/). Rather than duplicating those standards, this document defines NeoNephos-specific requirements (such as response SLAs and conformance tiers) and provides platform-specific guidance that generic standards cannot offer. Where a topic is fully covered by an external standard, this document states the requirement and references the authoritative source.

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
- **Operational security controls**: Authentication, CI/CD security, access governance, code scanning, and data retention requirements.

This document does **not** cover:

- OpenSSF Best Practices Badge requirements — see [Project Lifecycle Policy](../lifecycle-policy/project-lifecycle-policy.md).
- Governance, maintainer access, and operational policies — see [Project Guidelines](../project-guidelines/project-guidelines.md).

Where applicable, individual sections reference the corresponding controls from the [OpenSSF Security Baseline (OSPS)](https://baseline.openssf.org/) to help projects map these guidelines to the broader open source security ecosystem.

---

## 5. Security Contact per Project

### 5.1 Private Vulnerability Intake Channel

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Projects **MUST** provide a private channel through which external reporters can submit vulnerability reports confidentially. The specific mechanism depends on the hosting platform, but **MUST** ensure that:

1. Reports are visible only to designated security contacts (see [Section 6](#6-vulnerability-response-process)) and **MUST NOT** be publicly accessible.
2. The channel is documented in the project's `SECURITY.md` (see [Section 5.2](#52-securitymd)).
3. Reporters receive a confirmation that their report has been received.

The following subsections define platform-specific requirements.

#### 5.1.1 GitHub

Projects hosted on **GitHub** **MUST** enable [GitHub Private Vulnerability Reporting](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability) on all repositories that contain publishable code or artifacts. This is the preferred intake channel for GitHub-hosted projects.

Projects **SHOULD** enable Private Vulnerability Reporting at the organization level to ensure newly created repositories inherit this setting.

#### 5.1.2 GitLab

Projects hosted on **GitLab** **MUST** accept vulnerability reports via [confidential issues](https://docs.gitlab.com/ee/user/project/issues/confidential_issues.html). The `SECURITY.md` **MUST** instruct reporters to mark issues as confidential when submitting vulnerability reports.

Projects **SHOULD** configure an [issue template](https://docs.gitlab.com/ee/user/project/description_templates.html) named "Security Vulnerability" that pre-selects the confidentiality checkbox and provides a structured reporting form.

#### 5.1.3 Other Platforms and Self-Hosted Setups

Projects that are **not** hosted on GitHub or GitLab (e.g., self-hosted Gitea, Forgejo, Bitbucket, or other platforms) **MUST** provide at least one of the following private intake channels:

1. **Encrypted email**: A dedicated security contact email address published in `SECURITY.md` and in a [`security.txt`](https://securitytxt.org/) file following [RFC 9116](https://www.rfc-editor.org/rfc/rfc9116). The project **SHOULD** publish a PGP/GPG public key to enable encrypted communication.
2. **Platform-native private reporting**: If the hosting platform offers a built-in confidential issue or vulnerability reporting mechanism, the project **MUST** enable and use it.

Projects **SHOULD** additionally publish a `/.well-known/security.txt` file on any project website, conforming to [RFC 9116](https://www.rfc-editor.org/rfc/rfc9116), with at minimum the `Contact` and `Expires` fields.

> **Practical note:** Regardless of platform, projects **SHOULD** provide an email address or alternative private channel in `SECURITY.md` as a fallback for reporters who do not have an account on the project's hosting platform.

### 5.2 SECURITY.md

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Projects **MUST** provide a `SECURITY.md` file in every repository that contains publishable code or artifacts. The `SECURITY.md` **MUST** include at minimum:

1. Instructions for reporting a vulnerability via the project's private intake channel (see [Section 5.1](#51-private-vulnerability-intake-channel)), including a direct link where applicable.
2. A version support policy stating which releases receive security updates (e.g., "the latest two minor releases" or a version table).
3. The expected response timeline (referencing [Section 6](#6-vulnerability-response-process) of this document).

Projects **SHOULD** additionally provide an email address or alternative private channel for reporters who do not have an account on the project's hosting platform.

A template is available at [`../templates/SECURITY.md`](../templates/SECURITY.md).

> **Exemplary implementation:** [Gardener's SECURITY.md](https://github.com/gardener/.github/blob/main/SECURITY.md) includes named security contacts, a detailed disclosure process, and severity-based handling.

Related sections: [6 — Vulnerability Response Process](#6-vulnerability-response-process); [7 — Severity Classification and Response SLAs](#7-severity-classification-and-response-slas).

---

## 6. Vulnerability Response Process

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Each project's TSC **MUST** designate at least two maintainers as security contacts responsible for handling vulnerability reports. These contacts **MUST** be documented in the project's `SECURITY.md`.

### 6.1 Acknowledgement

Projects **MUST** acknowledge receipt of a vulnerability report within **3 business days**. The acknowledgement **MUST** be sent via the same channel the report was received on (e.g., GitHub Security Advisory, GitLab confidential issue, or encrypted email).

### 6.2 Triage and Severity Assessment

Projects **MUST** perform an initial triage within **7 calendar days** of receiving a report. Triage **MUST** include:

1. Validation: confirming whether the report describes a genuine vulnerability.
2. Severity assessment using [CVSS v3.1](https://www.first.org/cvss/v3.1/specification-document) or later.
3. Assignment of a severity level per [Section 7](#7-severity-classification-and-response-slas).

The reporter **SHOULD** be informed of the triage outcome and the planned remediation timeline.

### 6.3 Fix Coordination

Fix development **SHOULD** happen in a private fork, draft advisory, or other non-public workspace to prevent premature disclosure. The fix **MUST** be reviewed by at least one additional maintainer before merging.

> **Platform-specific guidance:** On GitHub, use a [temporary private fork within a Security Advisory](https://docs.github.com/en/code-security/security-advisories/working-with-repository-security-advisories/collaborating-in-a-temporary-private-fork-to-resolve-a-repository-security-vulnerability). On GitLab, use a [confidential merge request](https://docs.gitlab.com/ee/user/project/merge_requests/confidential.html). On other platforms, use a private branch or out-of-band patch review.

If the vulnerability affects multiple NeoNephos projects, the reporting project's TSC **SHOULD** coordinate with the affected projects' TSCs before disclosure. The TAC **MAY** facilitate cross-project coordination.

### 6.4 CVE Assignment

| Priority   | Resolution      | Owner |
|------------|-----------------|-------|
| **SHOULD** | ASAP (≤30 days) | TSC   |

Projects **SHOULD** request a CVE identifier for confirmed vulnerabilities with a CVSS score ≥ 4.0 (Medium or higher). Projects hosted on GitHub **SHOULD** obtain CVE identifiers via [GitHub's CNA program](https://docs.github.com/en/code-security/security-advisories/working-with-repository-security-advisories/publishing-a-repository-security-advisory#requesting-a-cve-identification-number). Projects on other platforms **MAY** request CVEs through [MITRE's CVE Request form](https://cveform.mitre.org/) or another authorized CNA.

> **Practical note:** CVE assignment adds credibility and traceability but involves administrative overhead. Early-stage projects or projects with a small user base **MAY** defer CVE assignment until a stable release has been published and external adoption is established. A platform security advisory alone already provides adequate transparency for most cases.

### 6.5 Coordinated Disclosure

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Projects **MUST** follow a coordinated disclosure process:

1. **Embargo period**: The maximum embargo duration is **90 calendar days** from the date the report is acknowledged. During this period, details of the vulnerability **MUST NOT** be disclosed publicly.
2. **Disclosure**: Once a fix is available (or the embargo expires), the project **MUST** publish a security advisory containing:
   - A description of the vulnerability.
   - Affected versions.
   - The CVSS score and vector.
   - The CVE identifier (if assigned).
   - Remediation steps or patched versions.

   On GitHub, use [GitHub Security Advisories](https://docs.github.com/en/code-security/security-advisories/working-with-repository-security-advisories/publishing-a-repository-security-advisory). On GitLab, use a [project-level vulnerability record](https://docs.gitlab.com/ee/user/application_security/vulnerabilities/). On other platforms, publish the advisory on the project website or mailing list and link to it from `SECURITY.md`.
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
- **Disclosure SLA**: Time from triage completion to publishing a security advisory (see [Section 6.5](#65-coordinated-disclosure)). The disclosure SLA **MUST NOT** exceed the 90-day embargo defined in [Section 6.5](#65-coordinated-disclosure).

If a project cannot meet a Fix SLA, the TSC **MUST** communicate an updated timeline to the reporter and publish a mitigation or workaround advisory. Transparent communication about delays is always preferable to silently missing a deadline.

> **Rationale:** These SLAs are aligned with industry practice. The 90-day embargo follows the [OpenSSF Model Outbound Vulnerability Disclosure Policy](https://github.com/ossf/oss-vulnerability-guide/blob/main/maintainer-guide.md) and is consistent with CNCF projects such as Envoy. The severity-based fix timelines are comparable to those used by GitLab and Chainguard, adjusted from "patch availability" to "triage completion" to reflect the realities of volunteer-maintained open source projects.

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

For implementation guidance and tooling options, see the [SLSA specification](https://slsa.dev/spec/v1.0/) and [OpenSSF Security Baseline](https://baseline.openssf.org/) controls `OSPS-DO-03.01` and `OSPS-DO-03.02` (Level 3).

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

### 8.5 Container Image Scanning

| Priority   | Resolution                                   | Owner |
|------------|----------------------------------------------|-------|
| **SHOULD** | When publishing container images              | TSC   |

Projects that publish container images **SHOULD** scan all images for known vulnerabilities before pushing them to a registry. Image scanning **SHOULD** be integrated into the CI/CD pipeline so that every built image is evaluated before publication.

Projects **SHOULD** fail the pipeline (or at minimum generate a warning) when vulnerabilities at or above a project-defined severity threshold are detected. Projects **SHOULD** define this threshold explicitly (e.g., "Critical and High").

Examples of acceptable tools include [Trivy](https://github.com/aquasecurity/trivy), [Grype](https://github.com/anchore/grype), or [OSV-Scanner](https://google.github.io/osv-scanner/). See [OpenSSF Security Baseline](https://baseline.openssf.org/) controls `OSPS-VM-05.01` through `OSPS-VM-05.03` (Level 3) for additional guidance on SCA thresholds and policy evaluation.

Related sections: [8.3 — Software Bill of Materials (SBOM)](#83-software-bill-of-materials-sbom); [8.4 — Dependency Scanning](#84-dependency-scanning).

### 8.6 License Compliance Scanning

| Priority   | Resolution      | Owner |
|------------|-----------------|-------|
| **SHOULD** | ASAP (≤90 days) | TSC   |

Projects **SHOULD** automate license scanning of all direct and transitive dependencies to detect incompatible, unknown, or unlicensed components. License scanning **SHOULD** be integrated into the CI/CD pipeline.

Projects **SHOULD** define an allowlist of acceptable licenses (e.g., OSI-approved permissive licenses such as MIT, Apache-2.0, BSD-2-Clause, BSD-3-Clause) and flag any dependency whose license is not on the allowlist. Dependencies with incompatible or unknown licenses **SHOULD** be resolved before release.

Examples of acceptable tools include [Trivy](https://github.com/aquasecurity/trivy), [REUSE](https://reuse.software/), or equivalent. See [OpenSSF Security Baseline](https://baseline.openssf.org/) controls `OSPS-LE-02.01`, `OSPS-LE-02.02` (Level 1) and `OSPS-VM-05.01`, `OSPS-VM-05.02` (Level 3) for alignment with broader license compliance requirements.

Related sections: [8.4 — Dependency Scanning](#84-dependency-scanning); [8.5 — Container Image Scanning](#85-container-image-scanning).

---

## 9. Security Transparency

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Projects **MUST** publish security advisories for all confirmed vulnerabilities with a CVSS score ≥ 4.0 via the platform's advisory mechanism. On GitHub, use [GitHub Security Advisories](https://docs.github.com/en/code-security/security-advisories/working-with-repository-security-advisories/about-repository-security-advisories). On GitLab, use [project-level vulnerability records](https://docs.gitlab.com/ee/user/application_security/vulnerabilities/). On other platforms, publish advisories on the project website or mailing list and link to them from `SECURITY.md`.

Projects **MUST** reference CVE identifiers and advisory links in the release notes of patched versions.

Release changelogs **SHOULD** explicitly flag security-relevant modifications (fixes, dependency updates addressing CVEs, configuration changes with security impact). See [OpenSSF Security Baseline](https://baseline.openssf.org/) control `OSPS-BR-04.01` (Level 2).

Projects **SHOULD** maintain a public record of past security advisories accessible from the project's `SECURITY.md`.

Related sections: [6.6 — Post-Disclosure](#66-post-disclosure); [5.2 — SECURITY.md](#52-securitymd).

---

## 10. Operational Security Controls

This section defines security-relevant operational controls for NeoNephos projects. These requirements complement the supply chain security practices in [Section 8](#8-supply-chain-security) and the infrastructure guarantees in the [Project Guidelines §15](../project-guidelines/project-guidelines.md#15-operational-guarantees).

### 10.1 Authentication

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Projects **MUST** enforce Two-Factor Authentication (2FA) for all organization members.

Projects **SHOULD** disable SSH deploy keys at the organization level. Deploy keys lack per-user accountability; personal or machine accounts with MFA are preferred.

### 10.2 CI/CD Security

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

**Self-hosted runners**

- Repository-level self-hosted runners **MUST NOT** be enabled.
- Organization-level self-hosted runners **SHOULD NOT** be enabled unless necessary, and **MUST** be approved by GitHub Enterprise Cloud account administrators who record the decision via a TAC vote.
- *Rationale*: GitHub-hosted runners are preferred; self-hosted runners require careful hardening to prevent exploitation.

**Fork pull-request workflows**

- Projects **MUST** require approval for first-time contributors before workflows execute on fork pull requests.
- *Rationale*: Prevents unauthorized code execution from external contributors.

**Workflow permissions**

- The default `GITHUB_TOKEN` permission **MUST** be set to "Read repository contents and packages."
- Write access **MUST** be explicitly requested via the `permissions` key in workflow files.
- *Rationale*: Limits blast radius by preventing workflows from gaining unnecessary write access.

**Credential handling**

| Priority   | Resolution      | Owner |
|------------|-----------------|-------|
| **SHOULD** | ASAP (≤90 days) | TSC   |

- Projects **SHOULD** use workload identities (OIDC) or short-lived GitHub access tokens for interactions with external services.
- Where workload identity is not supported, projects **SHOULD** use fine-grained personal access tokens with the minimum required scopes.
- Temporary access tokens created for exceptional local batch jobs **MUST** be deleted immediately after use and **MUST NOT** exceed a lifetime of 6 hours.
- Projects **SHOULD** conduct package releases via CI/CD pipelines (GitHub Actions recommended) rather than from local machines. See also [Section 8.1 — Artifact Signing](#81-artifact-signing) and [Section 8.2 — Build Provenance](#82-build-provenance-slsa).

**Pipeline input sanitization**

| Priority   | Resolution      | Owner |
|------------|-----------------|-------|
| **SHOULD** | ASAP (≤90 days) | TSC   |

- Workflows **SHOULD** treat all externally supplied metadata (issue titles, PR bodies, branch names, commit messages) as untrusted input and sanitize it before use in shell commands, environment variables, or script interpolation.
- Workflows triggered by events from untrusted sources (e.g., `pull_request_target`, `issue_comment`) **SHOULD NOT** check out or execute code from the untrusted source in a context that has access to repository secrets.
- *Rationale*: Prevents script injection and privilege escalation via CI/CD pipelines. See [OpenSSF Security Baseline](https://baseline.openssf.org/) `OSPS-BR-01.01` (Level 1) and the [OpenSSF SCM Best Practices](https://best.openssf.org/SCM-BestPractices/).

**Workflow dependency pinning and action provenance**

| Priority   | Resolution      | Owner |
|------------|-----------------|-------|
| **SHOULD** | ASAP (≤90 days) | TSC   |

- Third-party GitHub Actions **SHOULD** be pinned to a specific commit SHA rather than a mutable tag (e.g., `actions/checkout@<sha>` instead of `actions/checkout@v4`).
- Projects **SHOULD** restrict allowed GitHub Actions to actions created by GitHub and verified creators, or to an explicit allowlist maintained by the project. See the [OpenSSF Scorecard `Pinned-Dependencies` check](https://github.com/ossf/scorecard/blob/main/docs/checks.md#pinned-dependencies).

> **Exemplary implementation:** The [Open Component Model CI workflows](https://github.com/open-component-model/open-component-model/tree/main/.github/workflows) demonstrate SHA-pinned actions, minimal `GITHUB_TOKEN` permissions with per-job escalation, and safe `pull_request_target` handling.

### 10.3 Branch Protection

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Projects **MUST** enable branch protection rules on the primary branch (e.g., `main`) of every repository containing publishable code. At minimum:

1. Direct commits to the primary branch **MUST** be prevented; all changes **MUST** go through a pull request or merge request.
2. Force-pushes to the primary branch **MUST** be disabled.
3. Deletion of the primary branch **MUST** be prevented.
4. At least one approving review from a non-author maintainer **MUST** be required before merge.
5. Required status checks (CI build, tests, security scans) **SHOULD** pass before merge.

> **OpenSSF alignment:** [OpenSSF Security Baseline](https://baseline.openssf.org/) controls `OSPS-AC-03.01` and `OSPS-AC-03.02` (Level 1) require preventing unauthorized commits and deletion of the primary branch. Control `OSPS-QA-07.01` (Level 3) requires non-author approval before merge. See also the [OpenSSF SCM Best Practices](https://best.openssf.org/SCM-BestPractices/) for platform-specific configuration guidance.

### 10.4 Secret Scanning and Prevention

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Projects **MUST** enable automated secret scanning on all repositories to detect accidentally committed credentials, API keys, and tokens. On GitHub, enable [Secret Scanning](https://docs.github.com/en/code-security/secret-scanning/introduction/about-secret-scanning) and [Push Protection](https://docs.github.com/en/code-security/secret-scanning/introduction/about-push-protection). On GitLab, enable [Secret Detection](https://docs.gitlab.com/ee/user/application_security/secret_detection/). On other platforms, integrate a tool such as [Gitleaks](https://github.com/gitleaks/gitleaks) or [TruffleHog](https://github.com/trufflesecurity/trufflehog) into the CI pipeline.

Projects **SHOULD** enable push protection to block commits containing detected secrets before they enter the repository history.

> **OpenSSF alignment:** [OpenSSF Security Baseline](https://baseline.openssf.org/) control `OSPS-BR-07.01` (Level 1) requires that the project's version control system **MUST** prevent secrets from being included in a commit. The [OpenSSF Concise Guide for Developing More Secure Software](https://best.openssf.org/Concise-Guide-for-Developing-More-Secure-Software) (Recommendation #9) reinforces this requirement.

### 10.5 Access Governance

| Priority   | Resolution      | Owner |
|------------|-----------------|-------|
| **SHOULD** | ASAP (≤90 days) | TSC   |

Projects **SHOULD** follow the principle of least privilege for all access grants:

- Limit GitHub Organization Owner access to a small number of administrative accounts.
- Limit the number of maintainers with repository admin permissions.
- Ensure settings and permissions changes are made only by trusted administrators.
- Use pull requests for all repository changes; consider preventing direct push access by requiring pull-request merges from forks.
- Maintain an up-to-date inventory of maintainer permissions across all platforms used by the project.

**Maintainer vetting**

Projects **SHOULD** require that maintainer candidates:

1. Have a demonstrated history of contributions for at least 6 months.
2. Are vouched for by an existing maintainer.
3. Have verified their real identity with an existing maintainer, preferably in person.

*Rationale*: Vetting contributors before granting commit or release access mitigates supply chain risks from compromised or malicious accounts (cf. the [xz-utils incident](https://en.wikipedia.org/wiki/XZ_Utils_backdoor)). For the broader contributor promotion process, see the [Project Lifecycle Policy](../lifecycle-policy/project-lifecycle-policy.md).

### 10.6 Code Quality and Scanning

| Priority   | Resolution      | Owner |
|------------|-----------------|-------|
| **SHOULD** | ASAP (≤90 days) | TSC   |

Projects **SHOULD** enable static application security testing (SAST) — such as [CodeQL](https://codeql.github.com/) or [SonarQube](https://www.sonarsource.com/products/sonarqube/) — to detect code-level vulnerabilities. Projects **SHOULD** define a severity threshold (e.g., "Critical and High") and gate the CI pipeline on it. See [OpenSSF Security Baseline](https://baseline.openssf.org/) controls `OSPS-VM-06.01` and `OSPS-VM-06.02` (Level 3).

For dependency-level vulnerability scanning, see [Section 8.4 — Dependency Scanning](#84-dependency-scanning).

### 10.7 Data Retention

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

- **Private repositories**: Artifact and log retention **MUST** be configured to 180 days.
- **Public repositories**: Retention defaults to 90 days (GitHub platform limitation).

### 10.8 Security Assessment

| Priority   | Resolution      | Owner |
|------------|-----------------|-------|
| **SHOULD** | ASAP (≤90 days) | TSC   |

Projects **SHOULD** perform an initial security assessment when entering the Growth or Graduated lifecycle stage. The assessment **SHOULD** include:

1. Identification of the project's trust boundaries and external interfaces.
2. A lightweight threat model covering the project's primary attack surfaces (e.g., using [STRIDE](https://en.wikipedia.org/wiki/STRIDE_%28security%29) or equivalent).
3. Documentation of known security assumptions and residual risks.

The assessment does not need to be formal; a section in the project's documentation or a dedicated `SECURITY_ASSESSMENT.md` is sufficient. Projects **SHOULD** review and update the assessment when significant architectural changes occur.

> **OpenSSF alignment:** [OpenSSF Security Baseline](https://baseline.openssf.org/) controls `OSPS-SA-03.01` (Level 2) and `OSPS-SA-03.02` (Level 3) require security assessment, threat modeling, and attack surface analysis for mature projects.

### 10.9 Automated Security Posture Verification

| Priority   | Resolution      | Owner |
|------------|-----------------|-------|
| **SHOULD** | ASAP (≤90 days) | TSC   |

Projects **SHOULD** enable the [OpenSSF Scorecard](https://github.com/ossf/scorecard) on all repositories containing publishable code. Scorecard provides automated checks for many of the requirements in this document and the [Project Guidelines](../project-guidelines/project-guidelines.md), including branch protection, dependency scanning, CI permissions, and vulnerability disclosure.

Projects **MAY** integrate Scorecard into their CI pipeline via the [Scorecard GitHub Action](https://github.com/ossf/scorecard-action) to receive continuous feedback on security posture.

> **Exemplary implementation:** The [Open Component Model Scorecard workflow](https://github.com/open-component-model/open-component-model/blob/main/.github/workflows/openssf-scorecard.yml) runs Scorecard with SARIF upload to the code-scanning dashboard.

Related sections: [8 — Supply Chain Security](#8-supply-chain-security); [8.4 — Dependency Scanning](#84-dependency-scanning); [10.2 — CI/CD Security](#102-cicd-security).

---

## 11. Acknowledgements

| Priority   | Resolution      | Owner |
|------------|-----------------|-------|
| **SHOULD** | ASAP (≤30 days) | TSC   |

Projects **SHOULD** credit security researchers who responsibly report vulnerabilities, unless the reporter requests anonymity. Acknowledgement **SHOULD** be included in the published security advisory and **MAY** also be included in release notes.

Related sections: [6.5 — Coordinated Disclosure](#65-coordinated-disclosure); [9 — Security Transparency](#9-security-transparency).
