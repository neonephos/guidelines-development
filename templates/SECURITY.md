# Security Policy (Template)

*This is a template for a SECURITY.md file. Adjust the placeholders (marked with `<...>`) to match
your project. Remove this italic guidance text before publishing. For projects with multiple
repositories, each repository containing publishable code or artifacts MUST have its own SECURITY.md.
On GitHub, a SECURITY.md placed in the organization's `.github` repository serves as the default for
all repositories that do not have their own — this satisfies the per-repository requirement, but
cannot include repository-specific direct links (see Option A below).
See the [NeoNephos Security Guidelines](../security-guidelines/security-guidelines.md) for the full
set of requirements.*

## Reporting a Vulnerability

If you discover a security vulnerability in **\<Project Name\>**, please report it responsibly
through one of the channels below. **Do not open a public issue for security vulnerabilities.**

*Choose the section that matches your hosting platform. Remove the other sections and this guidance
text before publishing.*

### Option A: GitHub Private Vulnerability Reporting (Preferred for GitHub-hosted projects)

Please use GitHub's built-in private vulnerability reporting:

1. Navigate to the **Security** tab of this repository.
2. Click **Report a vulnerability**.
3. Fill in the details and submit.

Direct link: [Report a vulnerability](https://github.com/<org>/<repo>/security/advisories/new)

*For more information, see [Privately reporting a security vulnerability](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability).*

*If this SECURITY.md is used as an organization-level file in a `.github` repository, remove the
direct link above and keep only the step-by-step instructions, since the link cannot point to a
specific repository.*

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

*If your project publishes a PGP/GPG key for encrypted communication, mention it here and provide
a link to the public key or a fingerprint. Projects SHOULD also publish a
[`security.txt`](https://securitytxt.org/) file following [RFC 9116](https://www.rfc-editor.org/rfc/rfc9116).*

### Fallback Contact

*If your project uses Option A or Option B above as the primary channel, add an email fallback here
for reporters who do not have an account on the hosting platform. If you chose Option C as your
primary channel, remove this section to avoid duplication.*

You may also report vulnerabilities via email to **\<security contact email\>**.

## Security Contacts

The following maintainers are responsible for handling vulnerability reports:

| Name | Handle | Role |
|------|--------|------|
| *\<Name\>* | [@\<handle\>](https://github.com/<handle>) | Lead Security Contact |
| *\<Name\>* | [@\<handle\>](https://github.com/<handle>) | Security Contact |

*The [NeoNephos Security Guidelines](../security-guidelines/security-guidelines.md#6-vulnerability-response-process)
require at least two security contacts. Add more rows as needed but do not reduce below two.
Adjust the profile links to match your hosting platform.*

## Supported Versions

*State clearly which versions receive security updates. This should express a version support policy
(e.g., "the latest two minor releases") rather than naming specific branches. Choose whichever format
fits your project — a table, a simple sentence, or a link to your release policy. Remove this guidance
text before publishing. Examples:*

**Option A — Single active branch (common for early-stage projects):**

> Only the latest release on the `main` branch is supported with security updates.

**Option B — Multiple supported releases:**

> | Version | Supported |
> |---------|-----------|
> | 2.x     | Yes       |
> | 1.x     | Yes (until YYYY-MM-DD) |
> | < 1.0   | No        |

## Response Process

This project follows the [NeoNephos Security Guidelines](../security-guidelines/security-guidelines.md) for vulnerability handling. In summary:

- **Initial response**: We will respond to your report within **14 calendar days**, in line with the [OpenSSF Best Practices](https://www.bestpractices.dev/) requirement.
- **Embargo**: Vulnerability details will remain confidential for up to **90 days** while a fix is developed. Fix timelines (see table below) are measured from triage completion.
- **Disclosure**: Once a fix is available, we will publish a security advisory with full details.

### Severity Response Targets

| Severity | CVSS Score | Fix Target | Disclosure Target |
|----------|------------|------------|-------------------|
| Critical | 9.0 – 10.0 | ≤ 14 days | ≤ 30 days         |
| High | 7.0 – 8.9 | ≤ 30 days     | ≤ 60 days         |
| Medium | 4.0 – 6.9 | ≤ 90 days   | ≤ 90 days         |
| Low | 0.1 – 3.9 | Best effort    | Best effort       |

*Timelines are in calendar days, measured from triage completion. For the full response target definitions, see the
[NeoNephos Security Guidelines, Section 7](../security-guidelines/security-guidelines.md#7-severity-classification-and-response-targets).*

## Disclosure Policy

We follow [coordinated disclosure](https://en.wikipedia.org/wiki/Coordinated_vulnerability_disclosure). We ask that you:

- Allow us reasonable time to investigate and address the vulnerability before public disclosure.
- Do not exploit the vulnerability beyond what is necessary to demonstrate the issue.
- Do not access or modify data belonging to other users.

We are committed to crediting reporters in our security advisories unless you prefer to remain anonymous.

## Past Security Advisories

*Optional — include this section only if your project has published advisories. Remove it entirely
for new projects. Adjust the link to match your hosting platform.*

See [Published Security Advisories](https://github.com/<org>/<repo>/security/advisories?state=published).
