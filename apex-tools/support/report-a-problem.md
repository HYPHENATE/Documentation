# Report a Problem

If you encounter an issue while using **ApexTools**, please report it through our Jira support process.

Reporting issues with clear and consistent information helps the team diagnose and resolve problems much faster.

> **Submit an issue:**  
> JIRA Link: `<<ADD YOUR JIRA ISSUE LINK HERE>>`

---

# Before Reporting a Problem

Before submitting a new issue, please check:

- The documentation to confirm expected behaviour
- Whether the issue has already been reported
- Whether the issue might be related to permissions or configuration

---

# Information to Include

When submitting a problem report, please include the following information.

Providing complete information helps the team reproduce and resolve the issue quickly.

| Information | Description |
|------|------|
| Client / Organisation | The organisation or Salesforce environment where the issue occurred |
| Package Version | The installed SimpleTags package version |
| Environment | Production, Sandbox, Developer Org, etc |
| Salesforce Edition | e.g. Enterprise, Unlimited, Nonprofit Cloud |
| User Profile / Permission Set | The permissions the affected user has |
| Object | The object where the issue occurred |
| Record Id (if applicable) | The specific record where the issue occurred |

---

# Steps to Reproduce

Please provide clear steps so the issue can be reproduced.

Example format:

1. Navigate to **Funding Request Page**
2. Change Status to **Submitted**
3. An error message appears

---

# Expected Behaviour

Describe what should have happened.

Example:

> The sharing on the record should have been updated to make the record read only to all external people

---

# Actual Behaviour

Describe what actually happened.

Example:

> A flow error was thrown and sharing did not take place.

---

# Screenshots or Screen Recording

If possible, include:

- screenshots
- screen recordings
- error messages
- console errors

These often make it significantly easier to diagnose the problem.

---

# Additional Context

If relevant, include:

- recent configuration changes
- metadata updates
- new components added to the page
- Flow changes
- Apex changes

---

# Priority

If the issue is impacting business processes, please indicate severity.

| Priority | Description |
|------|------|
| Low | Minor issue or cosmetic problem |
| Medium | Issue affecting normal workflow |
| High | Blocking key functionality |
| Critical | Production system unusable |