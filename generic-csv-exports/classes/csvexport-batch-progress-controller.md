# CSVExport BatchProgressController

## API Name
`CSVExport_BatchProgressController`

## Description

`CSVExport_BatchProgressController` is the Aura-enabled controller used by the packaged Lightning component. Its job is to decide whether the current `CSV_Export__c` record has any configured import or export mappings that use batch processing.

That lets the UI avoid subscribing to the event channel when batch monitoring is not relevant for the current record type.

---

## Sharing Model
`with sharing`

## Tested By
`CSVExport_BatchProgressController_Test`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| UI gatekeeping | Tells the LWC whether it should display and subscribe to the platform event channel. |
| Metadata inspection | Checks both import and export metadata for batch-enabled definitions. |
| Error handling | Converts runtime exceptions into `AuraHandledException` errors that the component can surface. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `isCSVExportBatchEnabled(String recordId)` | `Boolean` | Returns true when the current export record type has at least one batch-enabled import or export mapping. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `CSV_Export__c` | Supplies the current record type developer name. |
| `CSVExport_ImportHelper` | Retrieves import mappings for the record type. |
| `CSVExport_ExportHelper` | Retrieves export-file mappings for the record type. |

---

## Typical Usage

This class is called by `cSVExportBatchProgressComponent` during `connectedCallback` before the component subscribes to `CSVExport_Event__e`.

---

## Related Classes

- [CSVExport BatchHelper](/generic-csv-exports/classes/csvexport-batch-helper)
- [CSVExport ExportHelper](/generic-csv-exports/classes/csvexport-export-helper)
- [CSVExport ImportHelper](/generic-csv-exports/classes/csvexport-import-helper)
