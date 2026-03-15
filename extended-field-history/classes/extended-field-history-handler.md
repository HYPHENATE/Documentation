# Extended Field HistoryHandler

## API Name
`ExtendedFieldHistoryHandler`

## Description

`ExtendedFieldHistoryHandler` is the main trigger handler responsible for creating audit rows when tracked records are inserted or updated, and for cleaning up history when tracked records are deleted.

It is the runtime bridge between record-change events and the `FieldAuditHistory__c` storage object.

---

## Sharing Model
`with sharing`

## Tested By
`ExtendedFieldHistoryHandlerTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Insert auditing | Captures configured field values when a tracked record is created. |
| Update auditing | Compares old and new values and writes audit rows for changed tracked fields. |
| Delete cleanup | Starts the package clean-up path when tracked source records are deleted. |
| Row construction | Builds `FieldAuditHistory__c` rows with object, field, old/new value, and process type details. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `handleAfterInsert(List<SObject> newRecords)` | `void` | Creates audit rows for configured created-value tracking. |
| `handleAfterUpdate(List<SObject> oldRecords, List<SObject> newRecords)` | `void` | Creates audit rows for configured updated-value tracking. |
| `handleAfterDelete(List<SObject> oldRecords)` | `void` | Starts deletion clean-up for related audit rows. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `ExtendedFieldHistoryHelper` | Supplies tracking rules, field schema, value conversion, and delete handling. |
| `FieldAuditHistory__c` | Stores the generated history rows. |

---

## Typical Usage

This handler is called by package trigger infrastructure when tracked records change.

---

## Related Classes

- [Extended Field HistoryHelper](/extended-field-history/classes/extended-field-history-helper)
- [Extended Field HistoryBatchDelete](/extended-field-history/classes/extended-field-history-batch-delete)
