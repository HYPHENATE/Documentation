# Help Message

The **Help Message** component is the main user-facing record-page component for the package.

It displays contextual guidance messages for the current record and, where the user has editor access, also provides actions to view, edit, publish, and unpublish the underlying message records.

---

## API Name
`helpMessage`

## Description
Displays contextual help messages on a Lightning record page.

---

## Targets

- `lightning__RecordPage`

---

## Public Properties

| Name | API Name | Data Type | Required | Description |
|------|------|------|------|------|
| Display Icon | `selectedIcon` | String | No | Overrides the icon shown in the component header. |
| Display Title | `componentTitle` | String | No | Overrides the component title shown to users. |

---

## Behaviour Notes

| Area | Detail |
|------|------|
| Record context | Uses the current `recordId` and `objectApiName` from the Lightning record page. |
| Message refresh | Calls Apex to retrieve messages and reevaluates content when watched record fields change. |
| Editor actions | Shows additional actions when `canViewRecordActions()` confirms the current user is an editor. |
| Navigation | Supports view and edit navigation to the underlying `Help_Message__c` records. |
| Publish workflow | Calls Apex to publish or unpublish message records and then refreshes the component state. |

---

## Events

| Event | Description |
|------|------|
| Toast events | Success and error toasts are dispatched after publish or unpublish actions. |

---

## Example Usage

Place this component on Lightning Record Pages where users need contextual process guidance.

---

## Developer Notes

| Topic | Detail |
|------|------|
| Apex dependencies | Uses `HelpMessageController.getHelpMessages`, `canViewRecordActions`, and `changeMessageStatus`. |
| Dynamic record watching | Adjusts the `getRecord` field list based on the field paths returned by Apex so the component can refresh when relevant values change. |
| JSON contract | Expects Apex to return a `messages` array and a `fieldArray` list of watched fields. |
