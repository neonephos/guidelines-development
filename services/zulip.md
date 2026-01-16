# Zulip


## Normative Language

The key words **MUST**, **MUST NOT**, **REQUIRED**, **SHALL**, **SHALL NOT**, **SHOULD**, **SHOULD NOT**, **RECOMMENDED**, **MAY**, and **OPTIONAL** in this document are to be interpreted as described in [RFC 2119](https://www.rfc-editor.org/rfc/rfc2119.html) and [RFC 8174](https://www.rfc-editor.org/rfc/rfc8174.html).

## Summary

Zulip is the preferred chat service for NeoNephos Foundation projects.

Zulip channels can be requested in the [Project IT Services Support Portal](https://jira.linuxfoundation.org/plugins/servlet/desk/portal/2/create/1506).

## Guidelines

* Projects **MAY** maintain a communication channel under Zulip.
    * When deciding to maintain a communication channel under Zulip, the project **MUST** follow these guidelines.
    * When not maintaining a communication channel under Zulip, the project **SHOULD** have an alternative community channel medium accepted by the TAC
* **Zulip Server**: Projects **MUST** use the NeoNephos Zulip server at [linuxfoundation.zulipchat.com](https://linuxfoundation.zulipchat.com).
* **Zulip Channels**:
    * Projects **SHOULD** have a presence in the central [NeoNephos Zulip Channel](https://linuxfoundation.zulipchat.com/#channels/525732/neonephos-discusion/general) by having at least one TSC member join this channel.
    * Projects **MAY** have dedicated channels for project discussions. These can be requested [here](https://jira.linuxfoundation.org/plugins/servlet/desk/portal/2/create/1506)


## Default Setup / Naming Convention

If Projects decide to have a dedicated channels, these channels **SHOULD** follow the following naming convention

* The following channel names define `{project}` as a technical project name. It **MUST** be lowercase, and **MUST NOT** contain spaces.
* `{project}` **MUST** clearly identify the project and should be as close to the non-abbreviated name of the project as possible.


* `{project}` **MUST** be unique and equivalent across all channels for any given project.
* **General Discussions** - `neoneophos-{project}-discussion`  (**MUST** be a public channel)
* **Dedicated Support** - `neoneophos-{project}-support` (**MUST** be a public channel)
* **Public TSC Communication** - `neoneophos-{project}-tsc`  (**MUST** be a public channel)
* **Private TSC Communication** - `neoneophos-{project}-tsc-private`  (**MUST** private channel)
* Other channel names **SHOULD** be approved by the TAC in advance