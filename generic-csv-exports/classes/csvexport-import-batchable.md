# CSVExport ImportBatchable

## API Name
`CSVExport_ImportBatchable`

## Description

`CSVExport_ImportBatchable` is the asynchronous import-linking engine used when an import mapping enables batch processing.

It runs the query prepared by the import helper, updates each matching record so it references the current `CSV_Export__c` record, and publishes progress updates as it goes.

---

## Sharing Model
`inherited`

## Tested By
`CSVExport_Test`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Query execution | Runs the import helper's generated query in batch mode. |
| Record linking | Updates each selected record through the configured mapping field. |
| Progress publishing | Publishes batch progress and completion events. |
| Cleanup | Clears batch IDs on the runtime record when processing finishes. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `CSVExport_ImportBatchable(String rid, CSV_Import_Mapping__mdt cim, String soql)` | `constructor` | Stores the runtime record ID, mapping metadata, and generated query. |
| `start(Database.BatchableContext bc)` | `Database.QueryLocator` | Returns the prebuilt query locator. |
| `execute(Database.BatchableContext bc, List<SObject> listOfRecords)` | `void` | Updates selected records and publishes progress. |
| `finish(Database.BatchableContext bc)` | `void` | Clears current batch IDs and publishes the final update. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `CSVExport_BatchHelper` | Applies record updates, clears runtime job IDs, and publishes progress events. |
| `CSV_Import_Mapping__mdt` | Supplies the mapping field used to update the records. |

---

## Typical Usage

This class is started from `CSVExport_ImportHelper.startProcess` whenever the selected import mapping enables batch processing.

---

## Related Classes

- [CSVExport ImportHelper](/generic-csv-exports/classes/csvexport-import-helper)
- [CSVExport BatchHelper](/generic-csv-exports/classes/csvexport-batch-helper)
