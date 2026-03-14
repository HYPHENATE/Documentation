# Dynamic Checks Container

`dynamicChecksContainer` is the exposed record-page component for the package.

## Purpose

It loads the checklist data for the current record and renders category-level sections for end users.

## Target

- `lightning__RecordPage`

## Configurable Properties

- `expandAllSections`
- `firstTimeCreateOnly`

## Runtime Behavior

- checks for the `Dynamic_Checks_Access` custom permission
- loads the current record context
- calls `ChecksContainerController`
- refreshes after child check updates

## When To Use

Use this component on the Lightning record pages where staff should work through operational checks directly on the record.
