# CSVExport BatchHelper

## API Name
`CSVExport_BatchHelper`

## Description

`CSVExport_BatchHelper` provides the shared operational support used by both the import and export batch paths. It updates the runtime `CSV_Export__c` record, publishes progress events, and performs record updates during import processing.

This helper is one of the key classes that ties together the batch jobs, the platform event, and the record-page monitoring experience.

---

## Sharing Model
`with sharing`

## Tested By
`CSVExport_Test`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Event publishing | Publishes `CSVExport_Event__e` progress messages for batch jobs. |
| Runtime updates | Stores current import or export batch IDs back on the `CSV_Export__c` record. |
| Shared data updates | Applies the mapping field update to records selected by the import process. |
| CSV row generation | Reuses export helper logic to turn queried records into CSV row strings. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `fireImportEvent(String jobId, String currentExportRecordIdID, String message, String jobType)` | `void` | Publishes a progress or error platform event for the current batch job. |
| `processUpdates(List<SObject> listOfRecords, String mappingField, String recordId)` | `void` | Updates selected records so they reference the current export record. |
| `updateCSVExportRecord(String recordId, String importBatchProcessingId, String exportBatchProcessingId)` | `void` | Stores the current job IDs on the runtime record. |
| `generateCSVExportRow(List<SObject> listOfRecords, Map<String, List<String>> lineFieldMappings)` | `String` | Converts queried records into CSV text. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `AsyncApexJob` | Supplies the progress values published in platform events. |
| `CSVExport_Event__e` | Carries progress details to the Lightning component. |
| `CSVExport_ExportHelper` | Generates CSV lines from record data. |

---

## Typical Usage

This class is not a user-facing entry point. It is called from the import and export helper and batch classes wherever the package needs shared job-tracking behaviour.

---

## Related Classes

- [CSVExport ExportBatchable](/generic-csv-exports/classes/csvexport-export-batchable)
- [CSVExport ImportBatchable](/generic-csv-exports/classes/csvexport-import-batchable)
- [CSVExport BatchProgressController](/generic-csv-exports/classes/csvexport-batch-progress-controller)
