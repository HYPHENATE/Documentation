# How Extended Field History Works

The package defines tracked fields in custom metadata, listens for relevant record changes, and writes audit rows into `FieldAuditHistory__c`.

Representative classes handle trigger logic, data preparation, batch cleanup, and record-page rendering of audit history.
