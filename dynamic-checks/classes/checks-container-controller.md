# ChecksContainerController

`ChecksContainerController` is the Apex entry point used by the main Lightning component.

## Purpose

It exposes a single Aura-enabled method that loads checklist categories and checks for the current record.

## Main Method

- `loadCategoriesAndChecks(recordId, firstTimeCreateOnly)`

## Operational Role

This class keeps the client-side component lightweight by delegating the heavy lifting to `ChecksHelper`.
