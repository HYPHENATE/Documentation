# Extended Field HistoryRecordView

## API Name
`ExtendedFieldHistoryRecordView`

## Description

`ExtendedFieldHistoryRecordView` retrieves the full details of a single audit row so the frontend can display it in a modal.

It also attempts to resolve old and new values that look like Salesforce IDs into the referenced record names, making the history easier for users to interpret.

---

## Sharing Model
`with sharing`

## Tested By
`ExtendedFieldHistoryRecordViewTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Single-row retrieval | Loads a specific `FieldAuditHistory__c` record. |
| Reference resolution | Resolves old and new values into names where the stored values are Salesforce IDs. |
| Modal payload shaping | Returns the JSON payload used for the detailed record-view modal. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `getHistoryRecord(String recordId)` | `String` | Returns the full detail payload for one audit row. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `FieldAuditHistory__c` | Supplies the base audit row data. |

---

## Typical Usage

This class is called by the `extendedFieldHistory` component when the user opens the detail modal for a specific history row.

---

## Related Classes

- [Extended Field HistoryController](/extended-field-history/classes/extended-field-history-controller)
