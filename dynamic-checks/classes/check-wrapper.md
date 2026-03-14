# Check

## API Name
`Check`

## Description

`Check` is a lightweight Apex wrapper class used to send UI-friendly checklist data to the Lightning layer.

It packages a `Check__c` record together with extra display information such as help text, comment settings, owner editability, and custom answer metadata so the UI can render the right controls without repeating server-side logic.

---

## Sharing Model
`Inherits caller context`

## Tested By
`ChecksHelperTest` (indirect coverage)

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Record transport | Carries the underlying `Check__c` row to the UI. |
| Display metadata | Includes help text and comment settings taken from the related template. |
| Editability context | Flags when the current user is not allowed to edit owner-only checks. |
| Custom answer support | Provides custom answer options and valid answer values for non-binary check types. |

---

## Public Properties

| Property | Type | Purpose |
|------|------|------|
| `check` | `Check__c` | The live checklist record to display and update. |
| `helpText` | `String` | Help text shown to users alongside the check. |
| `notRecordOwner` | `Boolean` | Indicates that the current user should not edit owner-only checks. |
| `allowComments` | `Boolean` | Indicates whether comments may be entered for the check. |
| `customOptions` | `String` | Comma-delimited custom answer options passed to the UI. |
| `customAnswers` | `String` | Comma-delimited list of values treated as completion answers. |

---

## Runtime Notes

| Area | Detail |
|------|------|
| UI payload role | This wrapper exists to shape a single record into something the LWC layer can render directly. |
| Wrapper population | `ChecksHelper.buildChecks` populates this class when existing or newly created checks are prepared for the UI. |
| Completion handling | The `dynamicCheck` component uses `customAnswers` to decide whether a custom-value check should count as complete. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `Check__c` | Provides the underlying stored checklist state. |
| `ChecksHelper` | Creates and populates wrapper instances. |
| `dynamicCheck` | Consumes the wrapper data on the client side. |

---

## Typical Usage

This wrapper is returned as part of a `CheckCategory` payload whenever the record-page UI needs to display one checklist item and its display metadata.

---

## Related Classes

- [CheckCategory](/dynamic-checks/classes/check-category-wrapper)
- [ChecksHelper](/dynamic-checks/classes/checks-helper)
