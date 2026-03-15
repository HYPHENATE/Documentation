# Extended Field HistoryController

## API Name
`ExtendedFieldHistoryController`

## Description

`ExtendedFieldHistoryController` is the main Apex controller used by the record-page history component. It retrieves recent audit rows, resolves lookup-like values into display names where possible, builds the field and user filter lists, and returns the JSON payload the component renders.

It is the main read path into the audit data for end users.

---

## Sharing Model
`with sharing`

## Tested By
`ExtendedFieldHistoryControllerTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| History retrieval | Loads the most recent audit rows for the current record. |
| Filter support | Builds the field and user picklists used by the frontend filters. |
| Reference resolution | Attempts to resolve ID values in old or new values into record names. |
| Report linking | Looks up the packaged report so users can move from the component into the full history view. |
| JSON response shaping | Returns the history list plus filter data and report metadata. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `getCurrentRecordHistory(String recordId, String fieldName, String userId)` | `String` | Returns the history payload used by the `extendedFieldHistory` LWC. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `FieldAuditHistory__c` | Supplies the audit rows shown to the user. |
| `Report` | Supplies the packaged report ID for the full-history link. |

---

## Typical Usage

This controller is called by the `extendedFieldHistory` component when a record page loads or when the user changes the field or user filters.

---

## Related Classes

- [Extended Field HistoryRecordView](/extended-field-history/classes/extended-field-history-record-view)
