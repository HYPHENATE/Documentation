# CSV Export File

## API Name
`CSV_Export_File__mdt`

## Description

The **CSV Export File** custom metadata type defines the top-level structure of an export file. Each record represents one exportable file definition for a given `CSV_Export__c` record type.

This metadata tells the export helper which object to query, which relationship field links the data back to the current export record, whether the job should run in batch mode, and how the final file should be named.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Batch Size | `Batch_Size__c` | Number | 18,0 |
| CSV Export RecordType Name | `CSV_Export_RecordType_Name__c` | Text | 255 |
| CSV Header | `CSV_Header__c` | Long Text Area | 32768 |
| Export Object | `Export_Object__c` | Metadata Relationship |  |
| Export Related Field | `Export_Related_Field__c` | Metadata Relationship |  |
| FileName | `FileName__c` | Text | 255 |
| Use Batch Processing | `Use_Batch_Processing__c` | Checkbox |  |
| Use Versioning | `Use_Versioning__c` | Checkbox |  |

---

## Field Details

| Field | Purpose |
|------|------|
| Batch Size | Sets the batch scope when export processing runs asynchronously. |
| CSV Export RecordType Name | Matches the metadata record to the runtime export record type developer name. |
| CSV Header | Stores the header row that is written to the output file before data rows are added. |
| Export Object | Identifies the Salesforce object to query for export rows. |
| Export Related Field | Identifies the field on the export object that links records back to the current `CSV_Export__c` record. |
| FileName | Sets the file title and client path used when the package creates the content version. |
| Use Batch Processing | Determines whether the export should run through `CSVExport_ExportBatchable` instead of synchronously. |
| Use Versioning | Determines whether a new version should be written against an existing content document instead of creating a fresh file. |
