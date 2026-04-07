# Security Policy (Template)

*This is a template for a SECURITY.md file. Adjust the placeholders (marked with `<...>`) to match
your project. Remove this italic guidance text before publishing. For projects with multiple
repositories, each repository containing publishable code or artifacts MUST have its own SECURITY.md.
See the [NeoNephos Security Guidelines](../security-guidelines/security-guidelines.md) for the full
set of requirements.*

## Reporting a Vulnerability

If you discover a security vulnerability in **\<Project Name\>**, please report it responsibly
through one of the channels below. **Do not open a public issue for security vulnerabilities.**

### GitHub Private Vulnerability Reporting (Preferred)

Please use GitHub's built-in private vulnerability reporting:

1. Navigate to the **Security** tab of this repository.
2. Click **Report a vulnerability**.
3. Fill in the details and submit.

Direct link: [Report a vulnerability](https://github.com/<org>/<repo>/security/advisories/new)

*For more information, see [Privately reporting a security vulnerability](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability).*

### Alternative Contact

*If your project offers an alternative private reporting channel (e.g., email), list it here.
Otherwise, remove this section.*

You may also report vulnerabilities via email to **\<security contact email\>**.

## Security Contacts

The following maintainers are responsible for handling vulnerability reports:

| Name | GitHub Handle | Role |
|------|---------------|------|
| *\<Name\>* | [@\<handle\>](https://github.com/<handle>) | Security Officer |
| *\<Name\>* | [@\<handle\>](https://github.com/<handle>) | Maintainer |

## Supported Versions

*State clearly which versions receive security updates. Choose whichever format fits your project —
a table, a simple sentence, or a link to your release policy. Remove this guidance text before
publishing. Examples:*

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

- **Acknowledgement**: We will acknowledge your report within **3 business days**.
- **Triage**: We will assess the severity (using [CVSS v3.1](https://www.first.org/cvss/v3.1/specification-document)) within **7 calendar days**.
- **Embargo**: Vulnerability details will remain confidential for up to **90 days** while a fix is developed.
- **Disclosure**: Once a fix is available, we will publish a [GitHub Security Advisory](https://docs.github.com/en/code-security/security-advisories/working-with-repository-security-advisories/about-repository-security-advisories) with full details.

### Severity Response SLAs

| Severity | CVSS Score | Fix Target (calendar days) |
|----------|------------|----------------------------|
| Critical | 9.0 – 10.0 | ≤ 7 days |
| High | 7.0 – 8.9 | ≤ 30 days |
| Medium | 4.0 – 6.9 | ≤ 90 days |
| Low | 0.1 – 3.9 | Best effort |

*If your project cannot meet a target, communicate an updated timeline to the reporter and publish
a workaround or mitigation advisory. Transparency matters more than speed.*

## Disclosure Policy

We follow [coordinated disclosure](https://en.wikipedia.org/wiki/Coordinated_vulnerability_disclosure). We ask that you:

- Allow us reasonable time to investigate and address the vulnerability before public disclosure.
- Do not exploit the vulnerability beyond what is necessary to demonstrate the issue.
- Do not access or modify data belonging to other users.

We are committed to crediting reporters in our security advisories unless you prefer to remain anonymous.

## Past Security Advisories

*Optional — include this section only if your project has published advisories. Remove it entirely
for new projects.*

See [Published Security Advisories](https://github.com/<org>/<repo>/security/advisories?state=published).
