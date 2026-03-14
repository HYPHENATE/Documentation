# CSV Export

## API Name
`CSV_Export__c`

## Description

The **CSV Export** object is the operational record at the center of the package. Each record represents a single import or export job request and gives users a place to start the process, track its current status, and review the generated file or linked data results.

In practice, this is the record that an end user or admin interacts with. The record type developer name tells the package which metadata definitions to use, while the status drives the flow into either the import or export path.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| CSV Export ID | `Name` | Auto Number | `CSVEID-{000000000}` |
| ExportBatchId | `ExportBatchId__c` | Text | 255 |
| Export Date | `Export_Date__c` | Date |  |
| ImportBatchId | `ImportBatchId__c` | Text | 255 |
| Next Status | `Next_Status__c` | Text | 255 |
| Status | `Status__c` | Picklist | New, Import, Review, Export, Complete |

---

## Field Details

| Field | Purpose |
|------|------|
| CSV Export ID | Provides the human-readable identifier for each runtime record. |
| ExportBatchId | Stores the active export batch job ID when an export runs asynchronously. |
| Export Date | Captures the date associated with the export process. |
| ImportBatchId | Stores the active import batch job ID when an import runs asynchronously. |
| Next Status | Supports status progression or follow-on handling outside the core package flow. |
| Status | Controls whether the record-triggered flow runs the import path, export path, or leaves the record idle. |

---

## List Views

| Name | Fields | Filter |
|------|------|------|
| All | Name, Status, Export Date | No Filter |
