# CSVExport ImportHelper

## API Name
`CSVExport_ImportHelper`

## Description

`CSVExport_ImportHelper` contains the core import-linking runtime logic. It reads import mapping metadata, constructs the SOQL where clause from the configured filters, and then either updates matching records directly or launches batch processing.

This class is what makes the package's metadata-driven import pattern work without custom code for each object.

---

## Sharing Model
`with sharing`

## Tested By
`CSVExport_Test`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Metadata loading | Retrieves `CSV_Import_Mapping__mdt` records and child filter metadata. |
| Query construction | Builds the SOQL query that finds qualifying records for the current export record. |
| Filter translation | Converts business-friendly filter operators into SOQL operators. |
| Batch routing | Starts `CSVExport_ImportBatchable` when batch mode is enabled. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `getMappings(String developerName)` | `List<CSV_Import_Mapping__mdt>` | Retrieves import mappings for the runtime record type. |
| `processLinking(String recordId, CSV_Import_Mapping__mdt importMappingRecord)` | `void` | Builds the import query and starts processing for one mapping. |
| `buildWhereClause(List<String> whereQueryList, CSV_Import_Mapping__mdt importMappingRecord)` | `String` | Builds the combined where clause from child filters. |
| `startProcess(String query, CSV_Import_Mapping__mdt importMappingRecord, String recordId)` | `void` | Runs either the synchronous or batch import path. |
| `filterTypeHandling(String filterType)` | `String` | Converts configured filter labels into SOQL operators. |
| `getSObjectFieldType(SObjectType objectType, String sOQLField)` | `DisplayType` | Determines the field type so values can be quoted or formatted correctly. |

---

## Runtime Notes

| Area | Detail |
|------|------|
| Re-import prevention | When `Allow_re_imports__c` is false, the helper only selects records where the mapping field is null. |
| Data-type handling | Date and numeric filters are formatted differently from text filters before being added to the query. |
| Logical grouping | `OR` filter sets are wrapped in parentheses so the generated where clause behaves correctly. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `CSV_Import_Mapping__mdt` | Defines the top-level import configuration. |
| `CSV_Import_Mapping_Filter__mdt` | Defines the field-level filter criteria. |
| `CSVExport_ImportBatchable` | Processes large import-linking jobs asynchronously. |
| `CSVExport_BatchHelper` | Updates runtime records and publishes progress events. |
| `CSVExport_Constants` | Supplies the supported filter operator labels. |

---

## Typical Usage

This helper is reached from `CSVExport_ImportInvocable` after the packaged flow decides that a runtime record should run the import path.

---

## Related Classes

- [CSVExport ImportInvocable](/generic-csv-exports/classes/csvexport-import-invocable)
- [CSVExport ImportBatchable](/generic-csv-exports/classes/csvexport-import-batchable)
- [CSVExport BatchHelper](/generic-csv-exports/classes/csvexport-batch-helper)
