# Security Guidelines — NeoNephos Foundation

<!-- TOC -->
* [Security Guidelines — NeoNephos Foundation](#security-guidelines--neonephos-foundation)
  * [1. Introduction](#1-introduction)
  * [2. Normative Language](#2-normative-language)
  * [3. Scope](#3-scope)
  * [4. Quick-Start Checklist](#4-quick-start-checklist)
  * [5. Security Contact per Project](#5-security-contact-per-project)
    * [5.1 Private Vulnerability Intake Channel](#51-private-vulnerability-intake-channel)
    * [5.2 SECURITY.md](#52-securitymd)
  * [6. Vulnerability Response Process](#6-vulnerability-response-process)
    * [6.1 Initial Response](#61-initial-response)
    * [6.2 Triage and Severity Assessment](#62-triage-and-severity-assessment)
    * [6.3 Fix Coordination](#63-fix-coordination)
    * [6.4 CVE Assignment](#64-cve-assignment)
    * [6.5 Coordinated Disclosure](#65-coordinated-disclosure)
    * [6.6 Post-Disclosure](#66-post-disclosure)
  * [7. Severity Classification and Response Targets](#7-severity-classification-and-response-targets)
  * [8. Supply Chain Security](#8-supply-chain-security)
    * [8.1 Artifact Signing](#81-artifact-signing)
    * [8.2 Build Provenance (SLSA)](#82-build-provenance-slsa)
    * [8.3 Software Bill of Materials (SBOM)](#83-software-bill-of-materials-sbom)
    * [8.4 Software Composition Analysis (SCA)](#84-software-composition-analysis-sca)
  * [9. Operational Security Controls](#9-operational-security-controls)
    * [9.1 Authentication](#91-authentication)
    * [9.2 CI/CD Security](#92-cicd-security)
    * [9.3 Branch Protection](#93-branch-protection)
    * [9.4 Secret Scanning](#94-secret-scanning)
    * [9.5 Access Governance](#95-access-governance)
    * [9.6 Code Quality and Scanning](#96-code-quality-and-scanning)
    * [9.7 Security Assessment and Posture Verification](#97-security-assessment-and-posture-verification)
  * [10. Conformance Matrix](#10-conformance-matrix)
  * [11. Acknowledgements](#11-acknowledgements)
<!-- TOC -->

## 1. Introduction

This document defines the security guidelines for projects governed by the **NeoNephos Foundation**. It establishes requirements for vulnerability disclosure, incident response, supply chain security, and operational security controls that all NeoNephos projects must follow.

These guidelines complement the [NeoNephos Project Guidelines](../project-guidelines/project-guidelines.md), which reference this document in [Section 11 — Security](../project-guidelines/project-guidelines.md#11-security). They build on the [OpenSSF Security Baseline](https://baseline.openssf.org/), [SLSA](https://slsa.dev/), and the [OpenSSF Best Practices Badge](https://www.bestpractices.dev/), adding NeoNephos-specific requirements only where generic standards do not provide concrete guidance.

Each requirement carries a conformance priority (**MUST**/**SHOULD** per RFC 2119) and a resolution timeframe; see the [Conformance Matrix](#10-conformance-matrix). Enforcement follows [Project Guidelines §13a](../project-guidelines/project-guidelines.md#13a-enforcement-and-remediation).

---

## 2. Normative Language

The key words **MUST**, **MUST NOT**, **REQUIRED**, **SHALL**, **SHALL NOT**, **SHOULD**, **SHOULD NOT**, **RECOMMENDED**, **MAY**, and **OPTIONAL** in this document are to be interpreted as described in [RFC 2119](https://www.rfc-editor.org/rfc/rfc2119.html) and [RFC 8174](https://www.rfc-editor.org/rfc/rfc8174.html).

---

## 3. Scope

This document covers:

- **Vulnerability disclosure and response**: How projects receive, handle, and disclose security vulnerabilities.
- **Supply chain security**: Requirements for signing, provenance, SBOMs, and dependency management of released artifacts.
- **Operational security controls**: Authentication, CI/CD security, access governance, and code scanning requirements.

This document covers security controls applied during the **development, build, and release lifecycle** of NeoNephos projects. Runtime security of services deployed by consumers of these projects is out of scope.

For the purposes of this document, a repository contains **publishable code or artifacts** if it produces software that is distributed to users or other systems — including libraries, binaries, container images, Helm charts, CLI tools, SDKs, or any package published to a registry. Repositories that contain only documentation, governance files, or meeting notes are excluded.

---

## 4. Quick-Start Checklist

Every project with publishable code or artifacts **MUST** complete these items. Details in linked sections.

1. Designate security contacts and document in SECURITY.md ([Section 5.2](#52-securitymd), [Section 6](#6-vulnerability-response-process))
2. Enable private vulnerability reporting ([Section 5.1](#51-private-vulnerability-intake-channel))
3. Publish a SECURITY.md in every repository ([Section 5.2](#52-securitymd))
4. Respond to vulnerability reports within 14 calendar days ([Section 6.1](#61-initial-response))
5. Follow coordinated disclosure with 90-day embargo ceiling ([Section 6.5](#65-coordinated-disclosure))
6. Classify vulnerabilities using CVSS v3.1+ ([Section 7](#7-severity-classification-and-response-targets))
7. Scan dependencies for known vulnerabilities ([Section 8.4](#84-software-composition-analysis-sca))
8. Enforce 2FA for all organization members ([Section 9.1](#91-authentication))
9. Enable branch protection on primary branch ([Section 9.3](#93-branch-protection))
10. Enable secret scanning and push protection ([Section 9.4](#94-secret-scanning))
11. Require approval for first-time contributor CI workflows ([Section 9.2](#92-cicd-security))
12. Set default CI/CD token to read-only ([Section 9.2](#92-cicd-security))

---

## 5. Security Contact per Project

### 5.1 Private Vulnerability Intake Channel

Projects **MUST** provide a private channel through which external reporters can submit vulnerability reports confidentially. The channel **MUST** ensure that:

1. Reports are visible only to designated security contacts and **MUST NOT** be publicly accessible.
2. The channel is documented in the project's `SECURITY.md` (see [Section 5.2](#52-securitymd)).
3. Reporters receive a confirmation that their report has been received.

Projects **SHOULD** additionally provide an email address or alternative private channel as a fallback for reporters who do not have an account on the project's hosting platform. See the [SECURITY.md template](../templates/SECURITY.md) for platform-specific setup.

### 5.2 SECURITY.md

Projects **MUST** provide a `SECURITY.md` file in every repository that contains publishable code or artifacts. The `SECURITY.md` **MUST** include at minimum:

1. Instructions for reporting a vulnerability via the project's private intake channel (see [Section 5.1](#51-private-vulnerability-intake-channel)), including a direct link where applicable.
2. A version support policy stating which releases receive security updates.
3. The expected response timeline (referencing [Section 6](#6-vulnerability-response-process) of this document).

A template is available at [`../templates/SECURITY.md`](../templates/SECURITY.md).

---

## 6. Vulnerability Response Process

Each project's TSC **MUST** designate security contacts responsible for handling vulnerability reports. These contacts **MUST** be documented in the project's `SECURITY.md`.

### 6.1 Initial Response

Projects **MUST** provide an initial response to a vulnerability report within **14 calendar days** of receiving it. Projects **SHOULD** acknowledge receipt within **2 business days** where maintainer availability permits.

> **Timeline anchor:** All timelines in this document are measured from **report receipt** (Day 0) — the date the project receives the vulnerability report. This follows [Google Project Zero's practice](https://googleprojectzero.blogspot.com/2021/04/policy-and-disclosure-2021-edition.html) of starting the clock at vendor notification.

### 6.2 Triage and Severity Assessment

The initial response **SHOULD** include — or be followed promptly by — a triage that covers:

1. Validation: confirming whether the report describes a genuine vulnerability.
2. Severity assessment using [CVSS v3.1](https://www.first.org/cvss/v3.1/specification-document) or later.
3. Assignment of a severity level per [Section 7](#7-severity-classification-and-response-targets).

The reporter **SHOULD** be informed of the triage outcome and the planned remediation timeline.

### 6.3 Fix Coordination

Fix development **SHOULD** happen in a non-public workspace. The fix **MUST** be reviewed by at least one additional maintainer before merging.

If the vulnerability affects multiple NeoNephos projects, the reporting project's TSC **SHOULD** coordinate with the affected projects' TSCs before disclosure. The TAC **MAY** facilitate cross-project coordination.

### 6.4 CVE Assignment

Projects **SHOULD** request a CVE identifier for confirmed vulnerabilities with a CVSS score ≥ 4.0 (Medium or higher).

Vulnerabilities scoring below 4.0 (Low) **MAY** be tracked informally and do not require a CVE or public advisory.

### 6.5 Coordinated Disclosure

Projects **MUST** follow a coordinated disclosure process:

1. **Embargo period**: The maximum embargo duration is **90 calendar days** from report receipt (Day 0), consistent with the [Google Project Zero disclosure policy](https://googleprojectzero.blogspot.com/2021/04/policy-and-disclosure-2021-edition.html). During this period, details of the vulnerability **MUST NOT** be disclosed publicly.
2. **Disclosure**: Once a fix is available (or the embargo expires), the project **MUST** publish a security advisory containing:
   - A description of the vulnerability.
   - Affected versions.
   - The CVSS score and vector.
   - The CVE identifier (if assigned).
   - Remediation steps or patched versions.
3. **Advisory publication**: Projects **MUST** publish advisories for all confirmed vulnerabilities with a CVSS score ≥ 4.0 via the platform's advisory mechanism.
4. **Release notes**: Projects **MUST** reference advisory links in the release notes of patched versions. When a CVE has been assigned (see [Section 6.4](#64-cve-assignment)), the CVE identifier **MUST** also be referenced.
5. **Changelogs**: Release changelogs **SHOULD** explicitly flag security-relevant modifications (fixes, dependency updates addressing CVEs, configuration changes with security impact).
6. **Advisory history**: Projects **SHOULD** maintain a public record of past security advisories accessible from the project's `SECURITY.md`.
7. **Early disclosure**: If active exploitation is detected in the wild, the TSC **MAY** shorten the embargo period and disclose early with whatever fix or mitigation is available.

### 6.6 Post-Disclosure

The fix **MUST** be released in a patch version for all supported release branches. The advisory **MUST** be referenced in the release notes of the patched version. The CVE identifier **SHOULD** also be referenced when assigned (see [Section 6.4](#64-cve-assignment)).

---

## 7. Severity Classification and Response Targets

Projects **MUST** classify vulnerabilities using [CVSS v3.1](https://www.first.org/cvss/v3.1/specification-document) or later. Maintainers **MAY** adjust the assigned severity (up or down) when the CVSS base score does not reflect real-world impact — for example, mitigating default configurations or evidence of active exploitation. Any deviation **MUST** be documented in the published advisory together with the original CVSS score and rationale.

Projects **MUST** publish a security advisory within the 90-day disclosure ceiling defined in [Section 6.5](#65-coordinated-disclosure). Within that ceiling, projects **SHOULD** aim for the following response targets (measured from report receipt, Day 0):

| Severity     | CVSS Score | Fix Target             | Disclosure Target      |
|--------------|------------|------------------------|------------------------|
| **Critical** | 9.0 – 10.0 | ≤ 14 calendar days    | ≤ 30 calendar days     |
| **High**     | 7.0 – 8.9  | ≤ 30 calendar days    | ≤ 60 calendar days     |
| **Medium**   | 4.0 – 6.9  | ≤ 90 calendar days    | ≤ 90 calendar days     |
| **Low**      | 0.1 – 3.9  | Best effort            | Best effort            |

- **Fix Target**: Time from report receipt to a fix being merged.
- **Disclosure Target**: Time from report receipt to publishing a security advisory. The disclosure **MUST NOT** exceed the 90-day embargo defined in [Section 6.5](#65-coordinated-disclosure).

If a project cannot meet a fix target, the TSC **SHOULD** communicate an updated timeline to the reporter and publish a mitigation or workaround advisory.

The 90-day ceiling aligns with the [Google Project Zero disclosure policy](https://googleprojectzero.blogspot.com/2021/04/policy-and-disclosure-2021-edition.html) and the [OpenSSF Vulnerability Disclosure Guide](https://github.com/ossf/oss-vulnerability-guide/blob/main/maintainer-guide.md). All timelines start from report receipt (Day 0), following Project Zero's practice of measuring from vendor notification. Severity-based fix targets are **SHOULD**-level goals — volunteer-maintained projects cannot guarantee timelines the way commercial vendors can.

---

## 8. Supply Chain Security

### 8.1 Artifact Signing

Projects **SHOULD** sign all published release artifacts (container images, binaries, packages) using [Sigstore](https://docs.sigstore.dev/) or an equivalent signing mechanism. Signing **SHOULD** be integrated into the CI/CD pipeline.

### 8.2 Build Provenance (SLSA)

Projects **SHOULD** generate [SLSA](https://slsa.dev/) provenance attestations for published artifacts, targeting at minimum [SLSA Build Level 2](https://slsa.dev/spec/v1.0/levels).

### 8.3 Software Bill of Materials (SBOM)

Projects **SHOULD** generate a Software Bill of Materials (SBOM) for each published release artifact. When an SBOM is published, it **MUST** use either [SPDX](https://spdx.dev/) or [CycloneDX](https://cyclonedx.org/) format.

### 8.4 Software Composition Analysis (SCA)

- Projects **MUST** scan direct and transitive dependencies for known vulnerabilities on every change to the codebase or its dependency manifests, against a documented severity threshold, and **MUST** block changes that violate the threshold (per [OpenSSF Baseline](https://baseline.openssf.org/) `OSPS-VM-05.01`, `OSPS-VM-05.03`).
- Scan results **SHOULD** be visible via the platform's standard mechanism (e.g., GitHub Dependabot alerts, GitLab Security dashboard) so that conformance is externally verifiable.
- Projects **SHOULD** configure automated dependency update pull requests to reduce time-to-remediation.
- Projects **SHOULD** remediate known vulnerabilities of medium or higher severity within 60 calendar days of public disclosure, per [OpenSSF Best Practices](https://www.bestpractices.dev/).
- Projects that publish container images **SHOULD** scan all images for known vulnerabilities before pushing them to a registry.
- Projects **SHOULD** automate license scanning of all dependencies and define an allowlist of acceptable licenses. The allowlist is defined by the project's TSC and **MUST** be compatible with the project's own license and the [foundation licensing policy](../project-guidelines/project-guidelines.md#6-licensing).

See [OpenSSF Security Baseline](https://baseline.openssf.org/) controls `OSPS-VM-05.01` through `OSPS-VM-05.03` and `OSPS-LE-02.01`, `OSPS-LE-02.02`.

---

## 9. Operational Security Controls

This section defines security-relevant operational controls for NeoNephos projects. These requirements complement the supply chain security practices in [Section 8](#8-supply-chain-security) and the infrastructure guarantees in the [Project Guidelines §15](../project-guidelines/project-guidelines.md#15-operational-guarantees).

### 9.1 Authentication

Projects **MUST** enforce Two-Factor Authentication (2FA) for all members of the project's source-control, CI/CD, and artifact-publishing accounts (e.g., the project's GitHub or GitLab organization, container and package registries).

Projects **SHOULD** disable SSH deploy keys at the source-control organization level (e.g., the GitHub or GitLab organization owning the project's repositories). Deploy keys lack per-user accountability; personal or machine accounts with MFA are preferred.

### 9.2 CI/CD Security

- Projects **MUST** require approval for first-time contributors before CI/CD workflows execute on fork pull requests.
- The default CI/CD token permission **MUST** be set to read-only (repository contents and packages). On GitHub, this means the `GITHUB_TOKEN` default; on GitLab, configure [protected CI/CD variables](https://docs.gitlab.com/ee/ci/variables/#protect-a-cicd-variable) with minimal scope.
- Write access **SHOULD** be explicitly requested per job or workflow. On GitHub, use the `permissions` key in workflow files. On GitLab, use protected environments and approval gates.
- Projects **SHOULD** use workload identities (OIDC) or short-lived access tokens for interactions with external services.
- Third-party CI/CD actions or templates **SHOULD** be pinned to a specific commit SHA or immutable digest rather than a mutable tag. On GitHub, pin actions by SHA (e.g., `actions/checkout@<sha>`). On GitLab, pin included templates by ref. [Dependabot](https://docs.github.com/en/code-security/dependabot/working-with-dependabot/keeping-your-actions-up-to-date-with-dependabot) and [Renovate](https://docs.renovatebot.com/configuration-options/#pindigests) both update SHA-pinned dependencies automatically.
- Workflows **SHOULD** treat all externally supplied metadata as untrusted input and sanitize it before use in shell commands.
- Workflows triggered by events from untrusted sources (e.g., on GitHub: `pull_request_target`, `issue_comment`; on GitLab: merge request pipelines from forks) **SHOULD NOT** execute untrusted code in a context with access to repository secrets.
- Projects **SHOULD** conduct package releases via CI/CD pipelines rather than from local machines.
- Repository-level self-hosted runners **SHOULD NOT** be enabled unless approved by platform administrators.

See [OpenSSF Security Baseline](https://baseline.openssf.org/) controls `OSPS-AC-04.01`, `OSPS-AC-04.02`, `OSPS-BR-01.01`.

### 9.3 Branch Protection

Projects **MUST** enable branch protection rules on the primary branch (e.g., `main`) of every repository containing publishable code. At minimum:

1. Direct commits to the primary branch **MUST** be prevented; all changes **MUST** go through a pull request.
2. Force-pushes to the primary branch **MUST** be disabled.
3. Deletion of the primary branch **MUST** be prevented.
4. At least one approving review from a non-author maintainer **MUST** be required before merge.
5. Required status checks (CI build, tests, security scans) **SHOULD** pass before merge.

### 9.4 Secret Scanning

Projects **MUST** enable automated secret scanning on all repositories to detect accidentally committed credentials, API keys, and tokens.

Projects **MUST** enable push protection to block commits containing detected secrets before they enter the repository history.

### 9.5 Access Governance

Projects **SHOULD** follow the principle of least privilege for all access grants:

- Limit organization owner / global admin accounts to the minimum needed for continuity in the absence of one or two individuals (typically **2–5**). Owner accounts **MUST** be human, named accounts (no shared accounts) with 2FA enforced.
- Grant repository **admin** permissions only to maintainers who need them for repository configuration (branch protection, secrets, releases). Routine review and merge work **SHOULD** use the lower **maintain** or **write** role.
- Use pull requests for all repository changes.
- Maintain an up-to-date inventory of maintainer permissions across all platforms used by the project.

Before granting commit or release access to a new maintainer, projects **SHOULD** verify that the candidate:

1. has a sustained history of substantive contributions to the project,
2. is vouched for by at least one existing maintainer, and
3. has had their real identity verified by an existing maintainer (preferably in person, or via an equivalent channel such as a video call against a previously verified identity).

Vetting contributors before granting commit or release access mitigates supply chain risks from compromised or malicious accounts (cf. the [xz-utils incident](https://en.wikipedia.org/wiki/XZ_Utils_backdoor)).

### 9.6 Code Quality and Scanning

Projects **SHOULD** enable static application security testing (SAST) to detect code-level vulnerabilities.

Projects **SHOULD** define a severity threshold and gate the CI pipeline on it.

### 9.7 Security Assessment and Posture Verification

Projects **SHOULD** perform an initial security assessment when entering the Growth or Graduated lifecycle stage, covering trust boundaries, a lightweight threat model (e.g., [STRIDE](https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats), the [OWASP Threat Modeling Process](https://owasp.org/www-community/Threat_Modeling_Process), or [CNCF Cloud Native Security Whitepaper §6](https://github.com/cncf/tag-security/blob/main/security-whitepaper/v2/cloud-native-security-whitepaper.md)), and documentation of known security assumptions and residual risks. The [OpenSSF Security Reviews repository](https://github.com/ossf/security-reviews) collects example reviews from other open-source projects.

Projects **SHOULD** enable the [OpenSSF Scorecard](https://github.com/ossf/scorecard) on all repositories containing publishable code. Scorecard provides automated checks for many of the requirements in this document, including branch protection, dependency scanning, CI permissions, and vulnerability disclosure.

---

## 10. Conformance Matrix

Each requirement carries a conformance priority and a resolution timeframe. The TSC of each project is the responsible owner for all requirements.

The **Resolution** column is measured from the date a requirement first applies to a project — the latest of: the requirement's effective date, the project's onboarding date, or the lifecycle stage at which the requirement applies. Effective dates for new or amended requirements are set by the TAC.

| Section | Requirement | Priority | Resolution | Owner |
|---------|-------------|----------|------------|-------|
| Section 5 | Private vulnerability intake channel | **MUST** | ≤30 days | TSC |
| Section 5 | SECURITY.md in every publishable repository | **MUST** | ≤30 days | TSC |
| Section 6 | Designated security contacts | **MUST** | ≤30 days | TSC |
| Section 6 | Initial response within 14 days | **MUST** | ≤30 days | TSC |
| Section 6 | Coordinated disclosure, 90-day embargo ceiling | **MUST** | ≤30 days | TSC |
| Section 6 | CVE assignment for CVSS ≥ 4.0 | **SHOULD** | ≤30 days | TSC |
| Section 7 | Severity classification using CVSS v3.1+ | **MUST** | ≤30 days | TSC |
| Section 8 | Dependency vulnerability scanning | **MUST** | ≤30 days | TSC |
| Section 8 | Artifact signing, SLSA provenance, SBOM | **SHOULD** | When publishing | TSC |
| Section 9 | 2FA for all organization members | **MUST** | ≤30 days | TSC |
| Section 9 | Branch protection on primary branch | **MUST** | ≤30 days | TSC |
| Section 9 | Secret scanning | **MUST** | ≤30 days | TSC |
| Section 9 | Push protection | **SHOULD** | ≤30 days | TSC |
| Section 9 | First-time contributor CI approval | **MUST** | ≤30 days | TSC |
| Section 9 | Default CI/CD token read-only | **MUST** | ≤30 days | TSC |
| Section 9 | OIDC/short-lived tokens, action pinning, input sanitization | **SHOULD** | ≤90 days | TSC |
| Section 9 | Access governance and maintainer vetting | **SHOULD** | ≤90 days | TSC |
| Section 9 | SAST scanning | **SHOULD** | ≤90 days | TSC |
| Section 9 | Security assessment and Scorecard | **SHOULD** | ≤90 days | TSC |

---

## 11. Acknowledgements

Projects **SHOULD** credit security researchers who responsibly report vulnerabilities, unless the reporter requests anonymity.
