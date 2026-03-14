# Dynamic Checks Container

The **Dynamic Checks Container** component is the main record-page entry point for the package.

It loads checklist categories and checks for the current record, controls loading and refresh behaviour, and renders the category-level experience that users interact with on a Lightning record page.

This is the component admins place on supported objects when they want staff to work through operational checks directly from the record itself.

---

## API Name
`dynamicChecksContainer`

## Builder Name
`Dynamic Checks Component - SetupUI`

## Description
Adds Dynamic Checks to a Salesforce record page.

---

## Targets

- `lightning__RecordPage`

---

## Public Properties

| Name | API Name | Data Type | Required | Description |
|------|------|------|------|------|
| Expand All Sections | `expandAllSections` | Boolean | No | Expands all checklist categories automatically when the component first renders. |
| First Time Create Only | `firstTimeCreateOnly` | Boolean | No | Prevents additional checks being created after the initial record setup use case. |

---

## Behaviour Notes

| Area | Detail |
|------|------|
| Record context | Uses the current `recordId` provided by the record page. |
| Permission gating | Checks the `Dynamic_Checks_Access` custom permission before showing the full experience. |
| Data loading | Calls `ChecksContainerController.loadCategoriesAndChecks` after the record context becomes available. |
| Refresh pattern | Reloads checklist data when a child component dispatches a `checkupdated` event. |
| Loading state | Tracks `isLoading` and `isSaving` so the UI can reflect data retrieval and refresh activity. |

---

## Events

| Event | Description |
|------|------|
| `childcheckupdated` | Handled internally from child components to trigger a full checklist refresh. |

---

## Example Usage

Use this component on Lightning Record Pages for objects where users need to complete operational checks directly in context.

---

## Developer Notes

| Topic | Detail |
|------|------|
| Apex dependency | Depends on `ChecksContainerController` returning `CheckCategory` wrappers in the expected shape. |
| Record wire | Uses `getRecord` to wait for valid record context before loading checklist data. |
| Child composition | Renders `dynamicChecksCategory`, which in turn renders `dynamicCheck` items. |

---

## Related Components

- [Dynamic Checks Category](/dynamic-checks/components/dynamic-checks-category)
- [Dynamic Check](/dynamic-checks/components/dynamic-check)
