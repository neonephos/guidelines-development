# Security Policy

<!-- Template instructions:
     - Replace all placeholders marked with <...> to match your project.
     - Remove sections that don't apply to your hosting platform (keep only the
       relevant "Option" under "Reporting a Vulnerability").
     - Remove all HTML comments (like this one) before publishing.
     - On GitHub, a SECURITY.md in the organization's `.github` repository
       is automatically used by every repository without its own — this
       satisfies the per-repository requirement, except where a repository
       needs its own intake link or contacts (then commit a per-repository
       SECURITY.md that overrides the org default).
     - GitLab has no equivalent fall-through; each GitLab project needs
       its own SECURITY.md.
     - See the NeoNephos Security Guidelines for the full set of requirements:
       https://github.com/neonephos/guidelines-development/blob/main/security-guidelines/security-guidelines.md
-->

## Reporting a Vulnerability

If you discover a security vulnerability in **\<Project Name\>**, please report it responsibly
through one of the channels below. **Do not open a public issue for security vulnerabilities.**

### What to Include in Your Report

To help us assess and address the vulnerability efficiently, please include:

- **Affected component(s)** and version(s)
- **Steps to reproduce** the vulnerability
- **Impact assessment** — what an attacker could achieve
- Whether the vulnerability is **already publicly known**
- Any suggested fix or mitigation (optional)

### Option A: GitHub Private Vulnerability Reporting (Preferred for GitHub-hosted projects)

<!-- Before publishing: Ensure that Private Vulnerability Reporting is enabled
     on this repository (or at the organization level). See:
     https://docs.github.com/en/code-security/security-advisories/working-with-repository-security-advisories/configuring-private-vulnerability-reporting-for-a-repository -->

Please use GitHub's built-in private vulnerability reporting:

1. Navigate to the **Security** tab of this repository.
2. Click **Report a vulnerability**.
3. Fill in the details and submit.

Direct link: [Report a vulnerability](https://github.com/<org>/<repo>/security/advisories/new)

<!-- If this SECURITY.md is used as an organization-level file in a `.github`
     repository, remove the direct link above and keep only the step-by-step
     instructions, since the link cannot point to a specific repository. -->

*For more information, see [Privately reporting a security vulnerability](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability).*

### Option B: GitLab Confidential Issues (Preferred for GitLab-hosted projects)

Please report vulnerabilities as a **confidential issue**:

1. Navigate to **Issues** in this project.
2. Click **New issue**.
3. Check the **"This issue is confidential"** checkbox.
4. Provide a detailed description including steps to reproduce.
5. Submit the issue.

*For more information, see [Confidential issues](https://docs.gitlab.com/ee/user/project/issues/confidential_issues.html).*

### Option C: Email (For other platforms or as a fallback)

You may report vulnerabilities via email to **\<security contact email\>**.

<!-- If your project publishes a PGP/GPG key for encrypted communication,
     mention it here and provide a link to the public key or a fingerprint.
     Projects SHOULD also publish a security.txt file following RFC 9116:
     https://securitytxt.org/ -->

### Fallback Contact

<!-- If your project uses Option A or Option B above as the primary channel,
     add an email fallback here for reporters who do not have an account on
     the hosting platform. If you chose Option C as your primary channel,
     remove this section to avoid duplication. -->

You may also report vulnerabilities via email to **\<security contact email\>**.

## Security Contacts

<!-- The NeoNephos Security Guidelines (Section 6) require designated security
     contacts. Add more rows as needed. Adjust the profile links to match your
     hosting platform. -->

The following maintainers are responsible for handling vulnerability reports:

| Name | Handle | Role |
|------|--------|------|
| \<Name\> | [\<handle\>](<profile-url>) | Lead Security Contact |
| \<Name\> | [\<handle\>](<profile-url>) | Security Contact |

## Supported Versions

<!-- State which versions receive security updates — prefer a version support
     policy (e.g., "the latest two minor releases") over naming specific branches.
     Choose any format that fits your project.
     Remove this comment and pick one of the options below (or write your own). -->

**Option A — Single active branch (common for early-stage projects):**

> Only the latest release on the `main` branch is supported with security updates.

**Option B — Multiple supported releases:**

> | Version | Supported |
> |---------|-----------|
> | 2.x     | Yes       |
> | 1.x     | Yes (until YYYY-MM-DD) |
> | < 1.0   | No        |

## Response Process

This project follows the [NeoNephos Security Guidelines](https://github.com/neonephos/guidelines-development/blob/main/security-guidelines/security-guidelines.md) for vulnerability handling. In summary:

- **Initial response**: We will respond to your report within **14 calendar days** of receipt, in line with the [OpenSSF Best Practices](https://www.bestpractices.dev/) requirement.
- **Embargo**: Vulnerability details will remain confidential for up to **90 days** from report receipt while a fix is developed, consistent with the [Google Project Zero disclosure policy](https://googleprojectzero.blogspot.com/2021/04/policy-and-disclosure-2021-edition.html).
- **Disclosure**: Once a fix is available (or the embargo expires), we will publish a security advisory with full details.

### Severity Response Targets

| Severity | CVSS Score | Fix Target | Disclosure Target |
|----------|------------|------------|-------------------|
| Critical | 9.0 – 10.0 | ≤ 14 days | ≤ 30 days         |
| High | 7.0 – 8.9 | ≤ 30 days     | ≤ 60 days         |
| Medium | 4.0 – 6.9 | ≤ 90 days   | ≤ 90 days         |
| Low | 0.1 – 3.9 | Best effort    | Best effort       |

*These are **SHOULD**-level targets as defined by the [NeoNephos Security Guidelines](https://github.com/neonephos/guidelines-development/blob/main/security-guidelines/security-guidelines.md#7-severity-classification-and-response-targets). The 90-day embargo ceiling is a **MUST** aligned with Google Project Zero. All timelines are measured from report receipt (Day 0); fix and disclosure may occur simultaneously.*

## Disclosure Policy

We follow [coordinated disclosure](https://en.wikipedia.org/wiki/Coordinated_vulnerability_disclosure). We ask that you:

- Allow us reasonable time to investigate and address the vulnerability before public disclosure.
- Do not exploit the vulnerability beyond what is necessary to demonstrate the issue.
- Do not access or modify data belonging to other users.

We are committed to crediting reporters in our security advisories unless you prefer to remain anonymous.

## Past Security Advisories

<!-- Optional — include this section only if your project has published
     advisories. Remove it entirely for new projects. Adjust the link to
     match your hosting platform. -->

None yet. See [Published Security Advisories](https://github.com/<org>/<repo>/security/advisories?state=published) once advisories are available.
