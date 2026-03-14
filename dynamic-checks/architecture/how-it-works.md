# How Dynamic Checks Works

Dynamic Checks separates checklist design from checklist execution. Admins define reusable checklist templates using custom objects, and the package then creates live `Check__c` records for the records where those templates apply.

At a high level, the system works by combining checklist configuration, record-level filtering, Lightning components, and optional flow automation.

---

## Step 1: Configure Template Headers

`Check_Template_Header__c` records define the high-level checklist category for a target object.

These records control:

- the object the checklist applies to
- the category name and description shown in the UI
- the category order
- whether the category applies to all records or only filtered records
- whether editing should be limited to the record owner

This gives admins a structured way to model checklist categories without building object-specific custom UI each time.

---

## Step 2: Add Check Templates

`Check_Template__c` records define the individual checks within each category.

Templates can control:

- the checklist item title
- the display type
- help text
- whether comments are allowed
- custom answer options
- optional flow launch settings

These templates are the reusable definitions from which live checks are created.

---

## Step 3: Apply Filters Where Needed

When a checklist category should only appear for some records, related `Check_Filter__c` records are used to evaluate the record against configured criteria.

This means teams can show different checklist categories depending on things like:

- status
- stage
- record type
- threshold values
- related record field values

This helps keep checklists relevant instead of showing every category on every record.

---

## Step 4: Load or Create Live Checks

When a user opens a record page containing the `dynamicChecksContainer` component, the package calls `ChecksContainerController`, which then uses `ChecksHelper`.

`ChecksHelper`:

- identifies the current object
- loads the applicable template headers
- evaluates filtered headers through `ChecksFilter`
- checks for existing `Check__c` records
- creates any missing live checks
- returns grouped wrapper data to the Lightning UI

This allows the package to generate record-specific checklist entries dynamically while still keeping the admin setup reusable.

---

## Step 5: Complete Checks in Lightning

The Lightning components display the resulting checklist categories and checks on the record page.

Users can:

- mark checks complete
- choose values for custom-answer checks
- add comments where the template allows it
- view category progress on screen

Because the checklist sits directly on the record page, it becomes part of normal operational work rather than a separate process.

---

## Step 6: Launch Optional Follow-On Automation

If a template is configured to launch a flow after completion, `CheckLaunchFlow` can run an autolaunched flow when a `Check__c` record is updated to a completed state.

This allows Dynamic Checks to support process completion and also trigger the next action where needed.

---

## Architecture Overview

At a simple level, Dynamic Checks works like this:

```text
Template Header + Template + Filter
              ↓
        Live Check Records
              ↓
 Lightning Record Page Experience
              ↓
 Optional Flow Automation
```

---

## Why This Approach Works

Dynamic Checks is useful because it keeps checklist behavior configurable while still giving users a structured, visible record-page experience.

| Capability | Benefit |
|------|------|
| Template-driven checklist design | Reduces repeated custom build effort |
| Filtered category visibility | Keeps the user experience relevant |
| Live `Check__c` records | Supports reporting and operational tracking |
| Lightning component delivery | Brings the checklist into day-to-day record work |
| Optional flow launching | Connects checklist completion to wider automation |
