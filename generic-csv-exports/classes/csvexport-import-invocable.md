# CSVExport ImportInvocable

## API Name
`CSVExport_ImportInvocable`

## Description

`CSVExport_ImportInvocable` is the flow-facing entry point for import-style linking. The packaged record-triggered flow calls this class when a `CSV_Export__c` record moves into the `Import` status.

The class retrieves the relevant import mappings for the current record type and passes each one into the helper layer so the package can identify and link qualifying records.

---

## Sharing Model
`with sharing`

## Tested By
`CSVExport_Test`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Flow entry point | Exposes the `Import records for Export` invocable action to Flow. |
| Mapping retrieval | Retrieves import mappings for the current record type. |
| Runtime handoff | Passes each mapping to the import helper for processing. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `importRecordsForExport(List<CSVExport_Constants.ExportRecord> exportrecords)` | `void` | Starts import-linking processing for the supplied runtime records. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `CSVExport_Constants.ExportRecord` | Defines the invocable input payload. |
| `CSVExport_ImportHelper` | Retrieves mappings and runs the import-linking logic. |

---

## Typical Usage

This class is normally invoked by the packaged `CSV_Export_AU` flow after a `CSV_Export__c` record is updated to `Import`.

---

## Related Classes

- [CSVExport ImportHelper](/generic-csv-exports/classes/csvexport-import-helper)
- [CSVExport ExportInvocable](/generic-csv-exports/classes/csvexport-export-invocable)
