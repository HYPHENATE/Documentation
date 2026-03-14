# CSVExport ExportBatchable

## API Name
`CSVExport_ExportBatchable`

## Description

`CSVExport_ExportBatchable` is the asynchronous export engine used when an export-file definition enables batch processing.

It prepares the query and line mappings in `start`, appends CSV row content during each `execute` chunk, and then writes the final file to Salesforce Files during `finish`.

---

## Sharing Model
`inherited`

## Tested By
`CSVExport_Test`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Query startup | Builds the export query and CSV header before the first batch chunk runs. |
| Chunk processing | Converts each queried record set into CSV row text. |
| Final file write | Creates or versions the final file in `finish`. |
| Progress publishing | Publishes platform event updates as the batch runs. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `CSVExport_ExportBatchable(String rid, CSV_Export_File__mdt emr)` | `constructor` | Stores the runtime record ID and export-file metadata. |
| `start(Database.BatchableContext bc)` | `Database.QueryLocator` | Prepares the export query and returns the batch scope. |
| `execute(Database.BatchableContext bc, List<SObject> listOfRecords)` | `void` | Appends CSV rows and publishes progress. |
| `finish(Database.BatchableContext bc)` | `void` | Writes the final file and publishes the completion event. |

---

## Runtime Notes

| Area | Detail |
|------|------|
| Stateful batch | The class uses `Database.Stateful` so the accumulated CSV text survives across execute chunks. |
| File creation timing | The actual file is only written once the batch finishes. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `CSVExport_ExportHelper` | Supplies mappings, query generation, and final file creation. |
| `CSVExport_BatchHelper` | Publishes progress and builds CSV row content. |

---

## Typical Usage

This class is started from `CSVExport_ExportHelper.generateFile` whenever the export metadata enables batch processing.

---

## Related Classes

- [CSVExport ExportHelper](/generic-csv-exports/classes/csvexport-export-helper)
- [CSVExport BatchHelper](/generic-csv-exports/classes/csvexport-batch-helper)
