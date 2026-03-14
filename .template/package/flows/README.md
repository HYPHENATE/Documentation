# Flows

Add one markdown file per important flow or per closely related flow set.

Suggested naming pattern:

- `donor-renewal-automation.md`
- `grant-reporting-reminder.md`
- `membership-onboarding-flow.md`

Use a consistent flow-page structure so automation docs read the same way across packages, even when the flows themselves are different.

Suggested content for each page:

- Title
- API Name
- Flow type
- Purpose and business trigger
- Who launches, owns, or depends on the flow
- Entry criteria or launch method
- Key decisions, branches, screens, or subflows
- Objects, fields, actions, or notifications affected
- Inputs and outputs where relevant
- Error handling, monitoring, or operational notes
- Related flows or classes

Where possible, explain the flow in nonprofit terms so readers can understand the business process behind the automation, such as donation follow-up, member renewal, grant compliance, or outcome capture.

For standard flow pages, use a structure like:

```md
# Flow Name

## API Name
`Flow_API_Name`

## Flow Type
`Screen Flow`

## Description

Explain what the flow does and why teams run it.

---

## Launch Context

| Area | Detail |
|------|------|
| Trigger | Explain how the flow starts. |
| Users | Explain who launches it or depends on it. |

---

## Flow Steps

### Step 1 - Example Step

Explain what happens at this stage.

---

## Data Impact

| Area | Detail |
|------|------|
| Objects | Explain what records are created, updated, or queried. |

---

## Operational Notes

| Topic | Detail |
|------|------|
| Errors | Explain what admins should watch for. |
```

If a section does not apply, omit it rather than inventing content.
