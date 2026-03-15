# Extended Field HistoryHelper

## API Name
`ExtendedFieldHistoryHelper`

## Description

`ExtendedFieldHistoryHelper` contains the shared logic that supports the package's audit runtime. It resolves tracking metadata, protects audit rows from unwanted edits or deletes, converts field values into storable text, and starts the batch delete process when source records are removed.

This class is the core utility layer behind both the trigger handler and the package's governance controls.

---

## Sharing Model
`with sharing`

## Tested By
`ExtendedFieldHistoryHelperTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Tracking resolution | Reads `ExtendedFieldAuditHistory__mdt` to determine which fields should be tracked. |
| Schema support | Returns valid field metadata for the tracked fields. |
| Value conversion | Converts different field data types into storable text for the audit object. |
| Audit protection | Applies edit and delete blocking logic based on the control custom setting. |
| Delete orchestration | Starts batch cleanup of audit rows when source records are deleted. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `fieldsToTrack(String objectAPIName, String processType)` | `Set<String>` | Returns the configured fields that should be audited for the object and process type. |
| `getAPIFieldLabels(String objectAPIName, Set<String> fieldsToTrack)` | `Map<String, Schema.SObjectField>` | Returns the field schema for configured tracked fields. |
| `getRecordValue(SObject record, String fieldAPIName)` | `Object` | Retrieves the value from the current record. |
| `getObjectAPIName(Id recordId)` | `String` | Returns the source object API name from a record ID. |
| `getConfigurationRecord()` | `ExtendedFieldHistoryControl__c` | Returns the package's current control settings. |
| `handleFieldHistoryValidations(List<FieldAuditHistory__c> records, String triggerContext)` | `void` | Blocks updates or deletes to audit rows when the control settings disallow them. |
| `processRecordValue(String fieldName, Object value, FieldAuditHistory__c historyRecord, Schema.SObjectField fieldData)` | `FieldAuditHistory__c` | Converts a runtime value into text and stores it on the history row. |
| `processDeleteRecords(Set<Id> recordsToDelete)` | `void` | Starts the batch deletion of audit rows for deleted source records. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `ExtendedFieldAuditHistory__mdt` | Defines the tracking rules. |
| `ExtendedFieldHistoryControl__c` | Defines whether audit rows can be edited or deleted. |
| `ExtendedFieldHistoryBatchDelete` | Handles bulk cleanup of history rows after source record deletion. |

---

## Typical Usage

This helper is used by the trigger handler, the history-protection trigger, and the delete cleanup path.

---

## Related Classes

- [Extended Field HistoryHandler](/extended-field-history/classes/extended-field-history-handler)
