# CSVExport ExportHelper

## API Name
`CSVExport_ExportHelper`

## Description

`CSVExport_ExportHelper` contains the core export runtime logic. It loads export-file metadata, builds the SOQL query, groups field mappings by line, and either runs the export synchronously or starts the batchable export path.

This is the class that turns metadata definitions into a real file attached to the `CSV_Export__c` record.

---

## Sharing Model
`with sharing`

## Tested By
`CSVExport_Test`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Metadata loading | Retrieves `CSV_Export_File__mdt` and `CSV_Export_File_Line__mdt` records for the current record type. |
| Query construction | Builds the field list and final SOQL query used to gather export rows. |
| File generation | Creates or versions the output `ContentVersion` file. |
| Batch routing | Starts `CSVExport_ExportBatchable` when batch mode is enabled. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `getMappings(String developerName)` | `List<CSV_Export_File__mdt>` | Retrieves export-file definitions for the runtime record type. |
| `getMappingsLines(String metaDataID)` | `List<CSV_Export_File_Line__mdt>` | Retrieves the child line definitions for an export file. |
| `processinfuture(String recordId, String developerName)` | `void` | Loads export mappings and starts generation for each one. |
| `generateFile(String recordId, CSV_Export_File__mdt exportMappingRecord)` | `void` | Runs either the synchronous or batch export path for one file definition. |
| `getExistingContentDocumentID(String recordId, String fileName)` | `Id` | Finds an existing file so versioning can be used when configured. |
| `getSOQLFieldQuery(List<CSV_Export_File_Line__mdt> listOfFilterLines)` | `String` | Builds the field list portion of the export query. |
| `getRecordsToProcess(CSV_Export_File__mdt exportMappingRecord, String fieldSetQuery, String recordId)` | `String` | Builds the final SOQL query used for export processing. |
| `getLineFieldMapping(List<CSV_Export_File_Line__mdt> listOfFilterLines)` | `Map<String, List<String>>` | Groups output fields by line number. |
| `getLineValues(SObject record, Map<String, List<String>> lineFieldMappings)` | `String` | Converts one record into one or more CSV lines. |
| `generateContentFile(String csv, String recordId, String contentDocumentID, Boolean useVersioning, String fileName)` | `void` | Writes the generated CSV content into Salesforce Files. |

---

## Runtime Notes

| Area | Detail |
|------|------|
| Relationship fields | The helper supports relationship-style field paths when reading output values. |
| Versioning | If metadata enables versioning and a matching file already exists, the helper writes a new content version instead of a fresh file. |
| Batch support | Batch mode delegates the heavy lifting to `CSVExport_ExportBatchable` and progress events. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `CSV_Export_File__mdt` | Defines the export file configuration. |
| `CSV_Export_File_Line__mdt` | Defines line-level field mappings. |
| `CSVExport_ExportBatchable` | Processes large exports asynchronously. |
| `CSVExport_BatchHelper` | Updates runtime records and publishes progress events. |

---

## Typical Usage

This helper is reached from `CSVExport_ExportInvocable` and is not usually called directly by end-user automation outside the package flow.

---

## Related Classes

- [CSVExport ExportInvocable](/generic-csv-exports/classes/csvexport-export-invocable)
- [CSVExport ExportBatchable](/generic-csv-exports/classes/csvexport-export-batchable)
- [CSVExport BatchHelper](/generic-csv-exports/classes/csvexport-batch-helper)
