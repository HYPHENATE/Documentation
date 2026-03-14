# CSVExport ExportInvocable

## API Name
`CSVExport_ExportInvocable`

## Description

`CSVExport_ExportInvocable` is the flow-facing entry point for export processing. The packaged record-triggered flow calls this class when a `CSV_Export__c` record moves into the `Export` status.

The class is intentionally thin. Its main job is to accept the invocable input wrapper, loop through the runtime records supplied by Flow, and hand off each export request to the helper layer.

---

## Sharing Model
`with sharing`

## Tested By
`CSVExport_Test`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Flow entry point | Exposes the `Generate export files` invocable action to Flow. |
| Runtime handoff | Passes each export request to `CSVExport_ExportHelper.processinfuture`. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `generateExportFiles(List<CSVExport_Constants.ExportRecord> exportrecords)` | `void` | Starts export processing for the supplied runtime records. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `CSVExport_Constants.ExportRecord` | Defines the invocable input payload. |
| `CSVExport_ExportHelper` | Performs the actual export orchestration. |

---

## Typical Usage

This class is normally invoked by the packaged `CSV_Export_AU` flow rather than called directly by custom code.

---

## Related Classes

- [CSVExport ExportHelper](/generic-csv-exports/classes/csvexport-export-helper)
- [CSVExport ImportInvocable](/generic-csv-exports/classes/csvexport-import-invocable)
