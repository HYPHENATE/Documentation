# Extended Field History

## API Name
`extendedFieldHistory`

## Builder Name
`Extended Field History`

## Description

This Lightning Web Component renders recent audit history for the current record directly on a Lightning record page.

It supports filtering by field and by user, opening a modal for a single history row, and linking to the packaged report when more than the most recent records need to be reviewed.

---

## Targets

- `lightning__RecordPage`

---

## Public Properties

| Name | API Name | Data Type | Required | Description |
|------|------|------|------|------|
| Record Id | `recordId` | String | Yes | The current record whose history should be displayed. |

---

## Behaviour Notes

| Area | Detail |
|------|------|
| Initial load | Calls `ExtendedFieldHistoryController.getCurrentRecordHistory` during `connectedCallback`. |
| Filtering | Reloads the history payload when the selected field or user changes. |
| Detail modal | Calls `ExtendedFieldHistoryRecordView.getHistoryRecord` when a user opens a specific history row. |
| Report handoff | Navigates to the packaged report when more than the recent on-screen history window is needed. |

---

## Related Components

- [Extended Field HistoryController](/extended-field-history/classes/extended-field-history-controller)
