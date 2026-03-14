# Dynamic Check

`dynamicCheck` is the internal component for an individual checklist item.

## Purpose

It lets a user complete a check, select a custom answer, and save optional comments.

## Notable Behavior

- supports standard completed or not completed checks
- supports custom answer options
- saves updates using Lightning Data Service
- emits update events back to the parent components

## Design Note

For custom display types, completion is based on whether the selected answer is one of the configured valid answers.
