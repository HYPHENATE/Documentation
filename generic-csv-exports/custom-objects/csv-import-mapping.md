# CSV Import Mapping

## API Name
`CSV_Import_Mapping__mdt`

## Description

The **CSV Import Mapping** custom metadata type defines how an import-style process should find Salesforce records and link them back to a `CSV_Export__c` runtime record.

Each mapping identifies the target object, the field that should be updated with the export record ID, the logical filter mode, and whether the work should be done in batch mode. Child filter metadata records then define the field-by-field criteria used to select the records.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Allow re-imports | `Allow_re_imports__c` | Checkbox |  |
| Batch Size | `Batch_Size__c` | Number | 18,0 |
| CSV Import RecordType | `CSV_Import_RecordType__c` | Text | 255 |
| Filter Type | `Filter_Type__c` | Picklist | AND, OR |
| Import Object | `Import_Object__c` | Metadata Relationship |  |
| Mapping Field | `Mapping_Field__c` | Metadata Relationship |  |
| Use Batch Processing | `Use_Batch_Processing__c` | Checkbox |  |

---

## Field Details

| Field | Purpose |
|------|------|
| Allow re-imports | Determines whether already-linked records can be selected again in later runs. |
| Batch Size | Sets the batch scope when import processing runs asynchronously. |
| CSV Import RecordType | Matches the mapping to the runtime export record type developer name. |
| Filter Type | Determines whether child filters are combined with `AND` or `OR` logic. |
| Import Object | Identifies the Salesforce object to query for records to link. |
| Mapping Field | Identifies the field on the import object that should be updated with the current export record ID. |
| Use Batch Processing | Determines whether the import should run through `CSVExport_ImportBatchable`. |
