# ChecksHelper

## API Name
`ChecksHelper`

## Description

`ChecksHelper` is the core orchestration class in the **Dynamic Checks** package.

It determines which checklist categories apply to a record, loads any existing `Check__c` rows, creates missing checks when required, and then returns a UI-friendly hierarchy of `CheckCategory` and `Check` wrapper objects.

This class is the main bridge between metadata configuration and the record-page experience. Most of the package behaviour that users perceive as "show me the right checks for this record" is assembled here.

---

## Sharing Model
`without sharing`

## Tested By
`ChecksHelperTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Record context detection | Derives the target object from the incoming record ID and stores object describe information for later use. |
| Existing check retrieval | Loads current `Check__c` rows for the record and indexes them by template ID for fast lookups. |
| Template header processing | Queries `Check_Template_Header__c` and child template/filter records for the current object. |
| Filtered applicability | Sends filter-driven headers to `ChecksFilter` when checklist visibility depends on record data. |
| Missing check creation | Inserts new `Check__c` rows for active templates that do not yet have a live check for the record. |
| Wrapper construction | Builds `CheckCategory` and `Check` wrappers so the LWC layer receives category-grouped, UI-ready data. |
| Owner-edit enforcement | Sets `notRecordOwner` flags when a category is configured for owner-only updates. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `ChecksHelper(Id recordId, Boolean firstTimeCreateOnly)` | Constructor | Establishes record context, loads existing checks, and resolves the record owner. |
| `getAllExistingChecks(List<Id> recordIds)` | `SObjectIndex` | Returns all existing checks for a set of record IDs, indexed by `Record_Id__c`. |
| `getCategoriesAndChecksForRecord()` | `List<CheckCategory>` | Builds the final set of checklist categories and checks that should appear for the current record. |

---

## Internal Methods

| Method | Purpose |
|------|------|
| `processCheckTemplateHeaders` | Works out which templates already have live checks and which still need `Check__c` rows creating. |
| `buildMissingChecks` | Inserts new check records and re-queries them with the related template/header data needed by the UI. |
| `buildChecks` | Converts `Check__c` rows into `Check` wrapper objects with help text, custom answer, and editability metadata. |
| `loadRecordOwner` | Attempts to load the parent record owner so owner-only edit logic can be enforced correctly. |

---

## Runtime Notes

| Area | Detail |
|------|------|
| Query scope fix | The class explicitly filters existing checks by the current `Record_Id__c`, which avoids excessive row retrieval in large orgs. |
| Header ordering | Headers and templates are sorted by configured order values before wrappers are returned to the UI. |
| First-time creation mode | When `firstTimeCreateOnly` is true, the class avoids creating new checks after the initial record setup case. |
| Wrapper enrichment | The helper copies template attributes such as help text, allowed comments, and custom answer configuration onto wrapper objects for the UI. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `Check_Template_Header__c` | Defines which checklist categories and filter rules apply to the current object. |
| `Check_Template__c` | Defines the individual checks that should exist under each category. |
| `Check__c` | Stores the live record-level checklist state. |
| `ChecksFilter` | Evaluates headers that only apply when configured filter conditions match the target record. |
| `CheckCategory` | Wrapper used to return a category and its child checks to the UI. |
| `Check` | Wrapper used to return a single check together with display and editability metadata. |

---

## Typical Usage

This class is normally invoked by `ChecksContainerController` when the `dynamicChecksContainer` component loads a record page and needs a complete, ordered checklist payload.

---

## Related Classes

- [ChecksContainerController](/dynamic-checks/classes/checks-container-controller)
- [ChecksFilter](/dynamic-checks/classes/checks-filter)
- [Check](/dynamic-checks/classes/check-wrapper)
- [CheckCategory](/dynamic-checks/classes/check-category-wrapper)
