# ChecksContainerController

## API Name
`ChecksContainerController`

## Description

`ChecksContainerController` is the Apex entry point used by the main **Dynamic Checks** Lightning component.

Its role is deliberately narrow. It exposes a single Aura-enabled method, accepts the current record context from the client, and hands the real processing work to `ChecksHelper`.

This keeps the client-side component lightweight while preserving a clear boundary between UI rendering and checklist orchestration.

---

## Sharing Model
`without sharing`

## Tested By
`ChecksContainerControllerTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Client entry point | Receives the record context from `dynamicChecksContainer` and exposes the package load operation to Lightning. |
| Delegation | Instantiates `ChecksHelper` and passes through the `recordId` and `firstTimeCreateOnly` settings. |
| Response handoff | Returns a list of `CheckCategory` wrapper records that the UI can render directly. |

---

## AuraEnabled Methods

| Method | Returns | Purpose |
|------|------|------|
| `loadCategoriesAndChecks(String recordId, Boolean firstTimeCreateOnly)` | `List<CheckCategory>` | Loads the checklist categories and check wrappers for the current record. |

---

## Runtime Notes

| Area | Detail |
|------|------|
| Controller scope | The class contains no business logic beyond instantiating `ChecksHelper` and returning the result. |
| UI dependency | It is called by the exposed `dynamicChecksContainer` Lightning component when the record page loads or refreshes. |
| Return shape | The response is already grouped by category, so the client does not need to rebuild the package hierarchy. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `ChecksHelper` | Performs the main record evaluation, check creation, and wrapper-building logic. |
| `CheckCategory` | Provides the wrapper structure returned to the client. |

---

## Typical Usage

This class is called when the main record-page component needs to load the current state of checklist categories and child checks for a record.

---

## Related Classes

- [ChecksHelper](/dynamic-checks/classes/checks-helper)
- [CheckCategory](/dynamic-checks/classes/check-category-wrapper)
