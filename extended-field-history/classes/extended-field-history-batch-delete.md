# Extended Field HistoryBatchDelete

## API Name
`ExtendedFieldHistoryBatchDelete`

## Description

`ExtendedFieldHistoryBatchDelete` is the cleanup batch used when source records are deleted. It finds and removes the related `FieldAuditHistory__c` rows so the audit table does not retain orphaned history records.

---

## Sharing Model
`inherited`

## Tested By
`ExtendedFieldHistoryHandlerTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Query setup | Finds audit rows linked to deleted source records. |
| Bulk cleanup | Deletes the matching `FieldAuditHistory__c` rows in batch chunks. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `ExtendedFieldHistoryBatchDelete(Set<Id> recordIds)` | `constructor` | Stores the source record IDs whose history should be removed. |
| `start(Database.BatchableContext bC)` | `Database.QueryLocator` | Returns the batch query for matching audit rows. |
| `execute(Database.BatchableContext bC, List<FieldAuditHistory__c> fieldHistoryRecords)` | `void` | Deletes the current batch of audit rows. |
| `finish(Database.BatchableContext bC)` | `void` | Completes the batch without additional post-processing. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `FieldAuditHistory__c` | The object being cleaned up after parent-record deletion. |

---

## Typical Usage

This batch is started by `ExtendedFieldHistoryHelper.processDeleteRecords` when tracked source records are deleted.
