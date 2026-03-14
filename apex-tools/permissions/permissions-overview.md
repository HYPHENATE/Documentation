# Permissions Overview

## Overview

`ApexTools` does not include packaged permission sets, permission set groups, or profile-based access configurations.

This is intentional.

The package is designed as a reusable technical foundation, and the correct permission model will vary significantly between organisations. Different teams will use different parts of the package, apply different governance models, and have different expectations around who should be able to configure, run, or review package functionality.

Because of that, permissions should be implemented as part of each organisation's own security design rather than assumed by the package.

---

## Why the Package Does Not Include Permission Sets

There are several reasons for this approach:

- not every organisation will use every part of the package
- different teams may split administration and operational responsibilities differently
- some package features are developer-facing, while others are admin-facing or support-facing
- the right access model depends on the organisation's own data governance and support model

For example, one organisation may allow system administrators to manage all ApexTools metadata directly, while another may give operational support staff access only to Apex Logs and nothing else.

---

## Recommended Approach

The best approach is usually to create your own organisation-specific permission model around how you plan to use the package.

In most cases, this means:

1. deciding which package features you are actually using
2. deciding which user groups need access to those features
3. creating permission sets or permission set groups that match those responsibilities

This usually produces a cleaner and safer result than trying to create one universal permission model.

---

## Suggested Permission Design Patterns

Below are some common ways an organisation might approach permissions for ApexTools.

## 1. Admin Configuration Model

In this model, only system administrators or technical platform administrators can manage ApexTools configuration.

Typical access might include:

- custom metadata management
- object and field access for logging records
- access to setup and deployment processes
- access to sandbox and automation configuration

This is often the safest default for organisations that want tight control over framework behaviour.

Best suited for:

- smaller admin teams
- highly governed environments
- organisations where developers or platform leads own technical framework configuration

---

## 2. Operational Support Model

In this model, support or operations users are given access to review logs and troubleshoot issues without being able to change core framework configuration.

Typical access might include:

- read access to `Apex_Log__c`
- edit access to support-oriented fields such as investigation or resolution notes
- access to reports and list views based on logged issues

This is useful where support teams need visibility into Flow and Apex failures but should not be changing metadata-driven framework behaviour.

Best suited for:

- organisations with a dedicated support function
- managed service teams
- larger nonprofits with separate operations and platform responsibilities

---

## 3. Developer Utility Model

In this model, developers and release engineers are given access to the package's framework objects and metadata so they can extend and configure the package during implementation work.

Typical access might include:

- access to relevant custom metadata types
- ability to deploy or update framework configuration
- access to test-support features and package utility behaviour

This model is usually appropriate in sandbox and development environments, but should still be reviewed carefully for production.

Best suited for:

- implementation teams
- consultancy delivery teams
- internal platform engineering teams

---

## 4. Split Responsibility Model

In many organisations, the best answer is not one permission set but several smaller ones.

For example:

- one permission set for log access
- one permission set for trigger framework configuration
- one permission set for sharing framework configuration
- one permission set for sandbox data setup
- one permission set for email utility administration

This approach is often the most flexible because it allows organisations to grant only the access actually needed by each team.

Best suited for:

- medium and large organisations
- nonprofits with multiple admin or support roles
- organisations that want least-privilege access design

---

## Areas to Consider When Designing Permissions

When deciding how to manage access, it helps to think in terms of package capabilities rather than package ownership.

## Logging

Consider who should be able to:

- view Apex Log records
- update investigation fields such as resolution notes or working status
- report on errors and processing outcomes

Not every user who can view logs should be able to change configuration.

## Trigger Framework

Consider who should be able to:

- create or update `Trigger_Handler__mdt` records
- activate or deactivate handler definitions
- use `Trigger_Control__c` to suppress trigger execution for specific scenarios

This is usually a tightly controlled capability.

## Sharing Framework

Consider who should be able to:

- manage sharing configuration metadata
- review access rules
- operate batch or custom sharing logic

Because sharing affects data visibility, this area should normally have stronger governance.

## Sandbox Data Tools

Consider who should be able to:

- manage sandbox data object configuration
- define field mappings
- control which data is loaded after refresh

This is often appropriate for platform admins or technical implementation teams rather than general users.

## Email Utilities

Consider who should be able to:

- manage settings related to logging email errors
- use Flow actions that rely on package email functionality
- support operational troubleshooting where email sends fail

This may involve both technical and operational roles.

## Test Data Utilities

Consider who should be able to:

- define test generator metadata
- use test-support features in development environments
- manage metadata that exists primarily for package or implementation testing

This is usually more relevant to developers than business users.

---

## Suggested Permission Set Ideas

Although the package does not include permission sets, the following patterns are often useful as a starting point.

## ApexTools Log Reviewer

Possible responsibilities:

- view Apex Log records
- update support-focused status and note fields
- run reports on logged issues

## ApexTools Framework Admin

Possible responsibilities:

- manage trigger configuration
- manage sharing configuration
- manage logging configuration
- manage sandbox data configuration

## ApexTools Support Admin

Possible responsibilities:

- review logs
- manage cleanup settings
- support email logging and issue investigation

## ApexTools Developer

Possible responsibilities:

- configure metadata in non-production environments
- work with test data tools
- support implementation and package extension work

These should be treated as design ideas, not universal packaged roles.

---

## Security Design Principles

When creating your own permissions for ApexTools, the following principles are recommended.

## Least Privilege

Grant only the access needed for the user's actual responsibility.

For example, a support user who reviews logs should not automatically be able to change sharing rules.

## Separate Configuration from Operations

Where possible, separate:

- users who configure framework behaviour
- users who monitor or support framework outcomes

This helps reduce risk and makes governance clearer.

## Treat Sharing Configuration Carefully

Sharing-related metadata can affect who sees what data.

Access to sharing configuration should usually be restricted to trusted platform administrators or developers.

## Be Cautious with Broad Metadata Access

Access to custom metadata configuration can be powerful.

If users can change framework metadata, they may be able to alter trigger behaviour, sharing behaviour, or logging outcomes.

## Review Production Access Separately

It is common for teams to allow broader access in sandboxes than in production.

That is often appropriate, but production access should still be reviewed independently and intentionally.

---

## Nonprofit and Grant Management Considerations

In nonprofit and grant management implementations, package permissions often need to align with operational roles.

For example:

- grants administrators may need access to logs and troubleshooting information
- platform admins may need to manage framework configuration
- reviewers or programme staff may use automations powered by ApexTools without needing direct access to package configuration
- support teams may need visibility into failed submissions, sharing issues, or outbound email problems

This makes role separation especially important.

In most cases, applicants, reviewers, and general programme users should not need direct access to the package's configuration objects.

---

## Recommended Documentation to Add Later

As your package documentation grows, it may help to add more specific guidance such as:

- a logging permissions guide
- a sharing framework permissions guide
- a sandbox-data admin guide
- example permission set designs for different organisation sizes

That would let you move from high-level guidance into more implementation-ready recommendations over time.

---

## Final Recommendation

The best way to approach permissions for `ApexTools` is to treat the package as a toolkit and design access around responsibilities, not around the package as a single unit.

In practice, that usually means:

- no single universal permission set
- several smaller role-based permission sets
- stronger control over metadata and sharing configuration
- broader access only where users genuinely need it

This gives organisations a more secure, flexible, and maintainable way to adopt the package.