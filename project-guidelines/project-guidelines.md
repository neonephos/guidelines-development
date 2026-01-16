# Project Guidelines — NeoNephos Foundation

<!-- TOC -->
* [Project Guidelines — NeoNephos Foundation](#project-guidelines--neonephos-foundation)
  * [1. Introduction](#1-introduction)
  * [2. Normative Language](#2-normative-language)
  * [3. Conformance Model](#3-conformance-model)
    * [Conformance Priorities](#conformance-priorities)
    * [Resolution Timeframes for mandatory Guidelines](#resolution-timeframes-for-mandatory-guidelines)
  * [4. Administration](#4-administration)
    * [Technical Charters](#technical-charters)
    * [Meetings](#meetings)
    * [Meeting Minutes](#meeting-minutes)
    * [Documentation of TSC Members](#documentation-of-tsc-members)
  * [5. Governance and Process](#5-governance-and-process)
    * [5.1 Contribution Authentication](#51-contribution-authentication)
  * [6. Technical and Development Practices](#6-technical-and-development-practices)
  * [7. Trademarks and Notices](#7-trademarks-and-notices)
    * [REUSE TOML](#reuse-toml)
    * [Website Notices](#website-notices)
    * [NeoNephos Mention](#neonephos-mention)
    * [End-User APIs](#end-user-apis)
  * [8. Community and Outreach](#8-community-and-outreach)
  * [9. Neutrality](#9-neutrality)
  * [10. Operations and Infrastructure](#10-operations-and-infrastructure)
  * [11. Security](#11-security)
  * [12. Funding Acknowledgements](#12-funding-acknowledgements)
  * [13. Transition-Specific Guidance](#13-transition-specific-guidance)
  * [13a. Enforcement and Remediation](#13a-enforcement-and-remediation)
    * [13a.1 Scope of Enforcement](#13a1-scope-of-enforcement)
    * [13a.2 Monitoring and Reporting](#13a2-monitoring-and-reporting)
    * [13a.3 Non-Compliance Process](#13a3-non-compliance-process)
    * [13a.4 Sanctions](#13a4-sanctions)
    * [13a.5 Appeals](#13a5-appeals)
    * [13a.6 Exceptions](#13a6-exceptions)
  * [14. Project Lifecycle and Graduation Criteria](#14-project-lifecycle-and-graduation-criteria)
  * [15. Operational Guarantees](#15-operational-guarantees)
    * [15.1 Infrastructure Guarantees](#151-infrastructure-guarantees)
    * [15.2 Availability Targets](#152-availability-targets)
    * [15.3 Security and Compliance](#153-security-and-compliance)
      * [15.3.1 Mandatory Compliance Requirements](#1531-mandatory-compliance-requirements)
      * [15.3.2 Supplemental Compliance](#1532-supplemental-compliance)
    * [15.4 Escalation and Support](#154-escalation-and-support)
    * [15.5 Service Review](#155-service-review)
  * [16. Project Onboarding](#16-project-onboarding)
<!-- TOC -->

## 1. Introduction

This document defines the current guidelines for projects goverened by the **NeoNephos Foundation**, a subfoundation of the Linux Foundation. All guidelines contained herein have been approved by the governing body and are binding unless otherwise stated.

The following terms are used throughout this document:

* **Technical Advisory Council (TAC)**
  The body overseeing project compliance, technical direction, and lifecycle reviews within the NeoNephos Foundation.

* **Technical Steering Committee (TSC)**
  The governing body of an individual project, responsible for day-to-day project management, decision-making, and technical direction.

* **Governing Board (GB)**
  The highest decision-making body of the NeoNephos Foundation, responsible for budget, resource allocation, and final appeals.

* **Project Charter**
  The formal document defining a project’s scope, governance structure, and policies. [The NeoNephos Foundation charter is available through a CDN](https://cdn.platform.linuxfoundation.org/agreements/neonephos-foundation.pdf).


Related sections: [2 — Normative Language](#2-normative-language); [3 — Conformance Model](#3-conformance-model); [14 — Project Lifecycle and Graduation Criteria](#14-project-lifecycle-and-graduation-criteria); [13 — Transition-Specific Guidance](#13-transition-specific-guidance).

---

## 2. Normative Language

The key words **MUST**, **MUST NOT**, **REQUIRED**, **SHALL**, **SHALL NOT**, **SHOULD**, **SHOULD NOT**, **RECOMMENDED**, **MAY**, and **OPTIONAL** in this document are to be interpreted as described in [RFC 2119](https://www.rfc-editor.org/rfc/rfc2119.html) and [RFC 8174](https://www.rfc-editor.org/rfc/rfc8174.html).

Related sections: [3 — Conformance Model](#3-conformance-model); [13a — Enforcement and Remediation](#13a-enforcement-and-remediation).

---

## 3. Conformance Model

Each guideline carries a *conformance priority statement* and a *resolution timeframe*.

Related sections: [13a — Enforcement and Remediation](#13a-enforcement-and-remediation); [14 — Project Lifecycle and Graduation Criteria](#14-project-lifecycle-and-graduation-criteria).

### Conformance Priorities

| Statement                  | Meaning                                                       |
|----------------------------|---------------------------------------------------------------|
| **OPTIONAL**               | Conformance is nice to have if applicable to the project.     |
| **SHOULD**                 | Recommended, but not strictly binding.                        |
| **MUST**                   | Binding requirement.                                          |
| **Contingent {statement}** | Requirement applies under the specified contingent condition. |

### Resolution Timeframes for mandatory Guidelines

The following timelines for resolution may be defined in this document:

| Timeframe label             | Meaning                                 |
|-----------------------------|-----------------------------------------|
| **ASAP (≤30 days)**         | Complete within 30 days.                |
| **By next minor release**   | Complete before the next minor release. |
| **By \<date> (YYYY-MM-DD)** | Complete by the specified date.         |
| **Open**                    | No fixed timeframe.                     |

---

## 4. Administration

### Technical Charters

| Priority   | Resolution            | Owner |
|------------|-----------------------|-------|
| **SHOULD** | By next minor release | TSC   |

Each project **SHOULD** make its project charter publicly available (website or repository). If converted to Markdown, the Markdown version **MUST** remain synchronized with the canonical source.

### Meetings

| Priority   | Resolution      | Owner |
|------------|-----------------|-------|
| **SHOULD** | ASAP (≤30 days) | TSC   |

The TSC **SHOULD** schedule meetings using the LFX Project Control Center.

### Meeting Minutes

| Priority   | Resolution      | Owner |
|------------|-----------------|-------|
| **SHOULD** | ASAP (≤30 days) | TSC   |

The TSC **SHOULD** record minutes for every meeting in a publicly accessible location that does not require foundation membership. Meeting minutes **MAY** be published via GitHub. A template is available [here](../templates/meeting_minutes.md).

### Documentation of TSC Members

| Priority   | Resolution      | Owner |
|------------|-----------------|-------|
| **SHOULD** | ASAP (≤30 days) | TSC   |

All TSC members and their roles **MUST** be listed publicly (e.g., website or repository). A template is available [here](../templates/owners.md).

---

## 5. Governance and Process

* **Code of Conduct**: Projects **MUST** adopt the [NeoNephos Code of Conduct](https://github.com/neonephos/.github/blob/main/CODE_OF_CONDUCT.md) and link it in all repositories.
* **Contribution Guidelines**: Projects **MUST** provide a `CONTRIBUTING.md` including CLA/DCO details.
* **Voting and Decision-Making**: The TSC **MUST** document its voting model (consensus, majority, or lazy consensus).
* **Ownership Documentation**: `OWNERS.md` or equivalent **MUST** define maintainers and approvers.

### 5.1 Contribution Authentication

* Projects **MUST** enforce a DCO (preferred).
* The chosen mechanism **MUST** be enforced via automated checks on all pull requests.
* Corporate contributions via bots or service accounts **SHOULD** map to a human approver.

Related sections: [4 — Administration](#4-administration); [6 — Technical and Development Practices](#6-technical-and-development-practices); [12 — Funding Acknowledgements](#12-funding-acknowledgements); [14 — Project Lifecycle and Graduation Criteria](#14-project-lifecycle-and-graduation-criteria).

---

## 6. Technical and Development Practices

* **Licensing**:

    * Projects **MUST** only use licenses approved through their Project Charter.
    * Projects **MUST** declare license via SPDX identifiers or REUSE TOML.

* **Continuous Integration**:

    * Projects **MUST** enable CI for builds, tests, and linting.
    * Projects **MUST** integrate static security scanning tools.

* **Release Management**:

    * Projects **SHOULD** adopt Semantic Versioning for releases of any build artifact produced and published.
    * Projects **SHOULD** tag releases and publish artifacts.

* **Dependency Management**:

    * Projects **MUST** track third-party licenses.
    * Projects **MAY** generate SBOMs for generated artifacts.

* **Security Disclosure**:

    * Projects **MUST** provide a [`SECURITY.md`](https://docs.github.com/en/code-security/getting-started/adding-a-security-policy-to-your-repository) defining their security policy.
    * Projects **MUST** define disclosure contacts (see Security Officer above).
    * Projects **MUST** Configure GitHub to allow [reporting vulnerabilities privately](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability)
    * Projects **SHOULD** provide an alternative method (e.g. email) to allow private disclosure of vulnerabilities

Related sections: [11 — Security](#11-security); [15 — Operational Guarantees](#15-operational-guarantees); [10 — Operations and Infrastructure](#10-operations-and-infrastructure).

---

## 7. Trademarks and Notices

* Word marks and logos are owned by Linux Foundation Europe for NeoNephos projects.
* Projects **MUST** follow LF trademark guidelines for name and logo usage.
* New logos or names **MUST** be approved by the TAC before public use.
* Vendor-neutral naming: packages, groups, images, and domains **MUST** avoid vendor prefixes.

### REUSE TOML

| Priority   | Resolution      | Owner |
|------------|-----------------|-------|
| **SHOULD** | ASAP (≤30 days) | TSC   |

If REUSE TOML is used:

```
Copyright <ProjectName> contributors.
```

> Note: REUSE dep5 is deprecated ([spec 3.3](https://reuse.software/spec-3.3/#dep5-deprecated)).

### Website Notices

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Websites **MUST** use a footer consistent with Linux Foundation Europe:

```
Copyright © Linux Foundation Europe. <ProjectName> is a project of NeoNephos Foundation. For applicable policies including privacy policy, terms of use and trademark usage guidelines, please see https://linuxfoundation.eu. Linux is a registered trademark of Linus Torvalds.
```

### NeoNephos Mention

| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

The organizational `README.md` **MUST** reference NeoNephos.

### End-User APIs

| Priority   | Resolution            | Owner |
|------------|-----------------------|-------|
| **SHOULD** | By next minor release | TSC   |

Projects exposing vendor-specific APIs **SHOULD** consult the TAC on neutral naming.

Related sections: [10 — Operations and Infrastructure](#10-operations-and-infrastructure); [1 — Introduction](#1-introduction).

---

## 8. Community and Outreach

* **Communication Channels**:
    * Projects **MAY** maintain a mailing list under their LFX project.
    * Projects **MAY** maintain a communication channel under Zulip.
      If a Project decides to maintain a communication channel under Zulip, it **MUST** follow the guidelines under [Zulip](../services/zulip.md)
* **Community Calls**: Projects **SHOULD** hold regular open calls to discuss project status and community requests.
* **Documentation**: Projects **MUST** provide user and developer guides.
* **Roadmap**: Projects **SHOULD** publish and update a roadmap.
* **Community Metrics**: Projects **SHOULD** report contributors, releases, and adoption.

    * Projects **MAY** use LFX Insights for community metrics.

Related sections: [14 — Project Lifecycle and Graduation Criteria](#14-project-lifecycle-and-graduation-criteria); [5 — Governance and Process](#5-governance-and-process); [12 — Funding Acknowledgements](#12-funding-acknowledgements);

---

## 9. Neutrality

* **Neutral Branding**: Projects **MUST** avoid vendor-prefixed namespaces, domains, and image tags.
* **Artifact Ownership**: Projects **MUST** transfer registries, packages, and docs hosting to NeoNephos.

Related sections: [7 — Trademarks and Notices](#7-trademarks-and-notices); [10 — Operations and Infrastructure](#10-operations-and-infrastructure); [15.3 — Security and Compliance](#153-security-and-compliance).

---

## 10. Operations and Infrastructure

* **Repository Ownership**: Projects **MUST** transfer GitHub/GitLab organizations to NeoNephos-administered accounts. **Resolution**: ASAP (≤30 days). **Owner**: TSC.
* **Domain Transfer**: Projects **MUST** transfer domains via the LFX Project Control Center. **Resolution**: ASAP (≤30 days). **Owner**: TSC.
* **Archival Policy**: Inactive repositories **SHOULD** be archived with TSC approval. **Resolution**: By next minor release. **Owner**: TSC.

Related sections: [15 — Operational Guarantees](#15-operational-guarantees); [4 — Administration](#4-administration).

---

## 11. Security


| Priority | Resolution      | Owner |
|----------|-----------------|-------|
| **MUST** | ASAP (≤30 days) | TSC   |

Projects **MUST** follow the guidelines defined within the [NeoNephos Security Guidelines](../security-guidelines/security-guidelines.md)

---

## 12. Funding Acknowledgements

* Projects **MUST** receive approval from the TAC for funding from outside the foundation.
* Projects **MUST** display external funding notices when receiving funding from outside the foundation.

Related sections: [5 — Governance and Process](#5-governance-and-process); [14 — Project Lifecycle and Graduation Criteria](#14-project-lifecycle-and-graduation-criteria).

---

## 13. Transition-Specific Guidance

* **Migration Playbook**: Checklist for transferring governance, repositories, infrastructure, and domains.
* **Change Management**: Plan for communicating user-facing changes (e.g., APIs, registries).
* **Grandfathering Exceptions**: The TAC **MAY** grant exceptions for delayed compliance.

Related sections: [10 — Operations and Infrastructure](#10-operations-and-infrastructure); [4 — Administration](#4-administration); [14 — Project Lifecycle and Graduation Criteria](#14-project-lifecycle-and-graduation-criteria).

## 13a. Enforcement and Remediation

This section defines how the **NeoNephos Foundation** enforces compliance with these guidelines.

### 13a.1 Scope of Enforcement

* Enforcement applies to all requirements marked as **MUST** or **MUST NOT** throughout this document.
* Requirements marked as **SHOULD** or **OPTIONAL** are advisory and are not subject to enforcement, unless elevated by the TAC.

### 13a.2 Monitoring and Reporting

* The TAC **MUST** review project compliance at least annually during a lifecycle review meeting.
* Any community member **MAY** raise a compliance concern by filing an issue or contacting the TAC via designated channels.
* The TAC **MUST** review these issues and provide public reports on compliance status and remediation plans.
* Projects **MUST** provide evidence of compliance upon request by the TAC.

### 13a.3 Non-Compliance Process

When a project is found to be non-compliant with a **MUST** requirement:

1. **Notification**: The TAC **MUST** notify the project’s TSC in writing, describing the non-compliance.
2. **Remediation Plan**: The TSC **MUST** submit a remediation plan within 30 days, unless otherwise specified by the TAC.
3. **Grace Period**: The TAC **MAY** grant a grace period for remediation, normally not exceeding 90 days.
4. **Verification**: The TAC **MUST** verify compliance after the remediation period.

### 13a.4 Sanctions

If a project fails to remediate within the defined period, the TAC **MAY** impose one or more of the following sanctions:

* Downgrading the project’s lifecycle stage (e.g., from *Graduated* to *Incubating*).
* Suspension of access to foundation-provided resources (e.g., CI/CD, artifact hosting).
* Public notice of non-compliance on the project’s foundation page.
* Archival of the project if non-compliance is persistent and unremediated.

### 13a.5 Appeals

* The project TSC **MAY** appeal TAC enforcement decisions to the GB within 30 days of notification.
* The GB’s decision on the appeal **MUST** be final.

### 13a.6 Exceptions

* The TAC **MAY** grant temporary or permanent exceptions to specific **MUST** requirements if justified by technical or organizational constraints.
* All granted exceptions **MUST** be documented publicly with a rationale and review date.

Related sections: [3 — Conformance Model](#3-conformance-model); [11 — Security](#11-security); [14 — Project Lifecycle and Graduation Criteria](#14-project-lifecycle-and-graduation-criteria).

---

## 14. Project Lifecycle and Graduation Criteria

Projects within the **NeoNephos Foundation** follow a staged lifecycle. The lifecycle provides transparency to contributors, adopters, and governing bodies about a project’s maturity, governance, and sustainability. Each stage has defined entry and graduation criteria.

The project lifecycle phases are defined in the [NeoNephos Foundation Project Lifecycle Policy](../lifecycle-policy/project-lifecycle-policy.md)

---

## 15. Operational Guarantees

The **NeoNephos Foundation** provides baseline operational guarantees for hosted projects. These guarantees ensure projects can rely on stable infrastructure, consistent processes, and responsive support.

---

### 15.1 Infrastructure Guarantees

* **Repository Hosting**:

    * All projects **MUST** be hosted under a NeoNephos-administered GitHub/GitLab organization.
    * Foundation staff **MUST** provide administrative support for access management.

* **Artifact Hosting**:

    * Projects **MUST** publish release artifacts to foundation-controlled registries, package repositories, or distribution systems.
    * Projects **SHOULD** sign release artifacts and provide provenance metadata (see [11 — Security](#11-security)).

* **Domains and DNS**:

    * All project domains **MUST** be managed through the Linux Foundation Project Control Center.

* **Continuous Integration**:

    * The foundation **SHOULD** provide minimal CI/CD infrastructure capable of supporting builds, tests, and security scans, up to a target budget approved by the GB and TAC.
    * The TAC **MUST** define and approve a CI/CD budget for projects, reviewed annually.
    * The TAC **MAY** approve access to additional CI/CD resources for projects, subject to availability targets and lifecycle stage priority.
    * Projects **MAY** bring additional CI/CD resources, provided they comply with NeoNephos security and neutrality requirements.

---

### 15.2 Availability Targets

* **Core Services** (repository hosting, artifact distribution, domains):

    * **MUST** have documented disaster recovery processes.

* **Communication Channels** (mailing lists, chat systems, community portals):

    * **MAY** rely on best-effort service levels when provided by third-party platforms (e.g., Zulip, Slack).

---

### 15.3 Security and Compliance

#### 15.3.1 Mandatory Compliance Requirements

All projects seeking to become part of NeoNephos **MUST** comply with the following enterprise-wide security and operational requirements.

**Security Policies**

* **Authentication**

    * **MUST** enforce Two-Factor Authentication (2FA) for all organization members.
    * **SSH Deploy Keys**: No global policy enforced. Projects **SHOULD** disable deploy keys at the organization level. Deploy keys pose security risks; personal or machine accounts with MFA are preferred.

* **GitHub Actions Security**

    * **Self-hosted Runners**

        * **Repository-level**: **MUST NOT** be enabled.
        * **Organization-level**: **SHOULD NOT** be enabled unless necessary, and **MUST** be approved by GitHub Enterprise Cloud account administrators who record decisions via TAC vote.
        * Rationale: GitHub-hosted runners are preferred; self-hosted runners require careful setup to avoid exploitation.
    * **Fork Pull Request Workflows**

        * **MUST** require approval for first-time contributors.
        * Purpose: Prevents unauthorized code execution from external contributors.
    * **Workflow Permissions**

        * Default **MUST** be set to “Read repository contents and packages.”
        * Write access **MUST** be explicitly requested via the `permissions` key in workflow files.
        * Rationale: Minimizes risk by preventing workflows from gaining unnecessary write access.

**Operational Policies**

* **Data Retention**

    * **Private Repositories**: Artifact and log retention **MUST** be configured to 180 days.
    * **Public Repositories**: Retention defaults to 90 days (GitHub limitation).

#### 15.3.2 Supplemental Compliance

Any project **SHOULD** abide by following additional guidelines:

**Minimize Overarching Permissions of Maintainers:**

- Only necessary permissions should be provided.
- Limit GitHub Owner access to a few admin accounts
- Limit the number of maintainers with admin permissions
- Ensure settings and permissions changes are made by trusted admins
- Use pull requests for repository changes
- Conduct package releases via CI/CD pipelines (recommend GitHub Actions)
- Have an up-to-date overview of maintainer permissions across different platforms
- Consider preventing maintainers from direct write access, requiring pull request merges from forks.
- Maintainer candidates have a history of contributions for at least 6 months
- Maintainer candidates are known to an existing maintainer
- Maintainer candidates provide a real identity to an existing maintainer in an in person event

**CI/GitHub Actions Hardening:**

- Use GitHub Actions for CI
- Avoid self-hosted runners wherever possible
- Use workload identities/OIDC or short-lived GitHub Access tokens for external interactions
- Utilize fine-grained access tokens if workload identity is unsupported
- Use attestation/signing of packages
- Limit GITHUB_TOKEN permissions to read-only by default
- For other CI systems, consult experts
- Temporary creating access tokens to perform a local batch job can be accepted in exceptional circumstances,
  but must they must be deleted afterwards (e.g. max lifetime ~6h)

**Other**

- Use automation (e.g., Dependabot, Renovate) for dependency updates
- Use automation (e.g., CodeQL, SonarQube) for finding code flaws and vulnerabilities
- Implement automatic tests for code validation

---

### 15.4 Escalation and Support

* Projects **MUST** have an escalation path to the NeoNephos GitHub Account Administration team for infrastructure issues.
* Escalation contacts **MUST** be published in the NeoNephos project handbook, and the GitHub Account Administration team **MUST** be publicly listed.
* Foundation contacts **SHOULD** provide a response within 48 hours for non-critical issues and within 24 hours for critical outages.

---

### 15.5 Service Review

* Operational guarantees **MUST** be reviewed annually by the TAC to ensure adequacy.
* Projects **MAY** request additional guarantees, subject to TAC approval and available resources.

---

## 16. Project Onboarding

Projects **MUST** follow the [NeoNephos Project Onboarding Guidelines](../onboarding/onboarding-guidelines.md)