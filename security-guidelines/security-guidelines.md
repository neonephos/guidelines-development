# NeoNephos Security Policy

The NeoNephos Foundation takes the security of our software seriously, including all source code repositories managed through its GitHub organizations.

If you believe you have found a security vulnerability in any NeoNephos repository, please report it to us as described below.

## Reporting Security Issues

**Please do not report security vulnerabilities through public GitHub issues.**

Instead, please use one of the following channels:

  - **GitHub Security Advisories** — navigate to the **Security** tab of the affected repository and select **"Report a vulnerability"** to privately report an advisory.
  - **Email** — contact the security team of the affected organization (see table below).

| Organization | Security Contact |
|---|---|
| [platform-mesh](https://github.com/platform-mesh) | [platform-mesh-security@lists.neonephos.org](mailto:platform-mesh-security@lists.neonephos.org) |
| [openmfp](https://github.com/openmfp) | [openmfp-security@lists.neonephos.org](mailto:openmfp-security@lists.neonephos.org) |

Organizations not listed above should use the foundation-wide security contact: [security@lists.neonephos.org](mailto:security@lists.neonephos.org)

Please include the requested information listed below (as much as you can provide) to help us better understand the nature and scope of the possible issue:

  - The repository name or URL
  - Type of issue (buffer overflow, SQL injection, cross-site scripting, etc.)
  - Full paths of the source file(s) related to the manifestation of the issue
  - The location of the affected source code (tag/branch/commit or direct URL)
  - Any particular configuration required to reproduce the issue
  - Step-by-step instructions to reproduce the issue
  - Proof-of-concept or exploit code (if possible)
  - Impact of the issue, including how an attacker might exploit the issue

This information will help us triage your report more quickly.

## Preferred Languages

We prefer all communications to be in English.

## Disclosure Policy

We follow the principle of [Coordinated Vulnerability Disclosure](https://en.wikipedia.org/wiki/Coordinated_vulnerability_disclosure). We ask that you:

  - Allow us a reasonable time to investigate and address the issue before making any information public.
  - Make a good faith effort to avoid privacy violations, data destruction, and disruption of services.
  - Do not exploit the vulnerability beyond what is necessary to verify it.

We commit to:

  - Acknowledging receipt of your vulnerability report.
  - Providing an estimated timeline for a fix.
  - Notifying you when the vulnerability is resolved.

## Adopting This Policy

Each NeoNephos organization should place a `SECURITY.md` file in its `.github` repository (or in individual repositories) that references or adapts this policy. At a minimum, the file should specify the organization-specific security contact and link back to this guideline for the full disclosure process.