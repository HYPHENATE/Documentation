# CSV Import Mapping Header

## API Name
`CSV_Import_Mapping_Header__mdt`

## Description

The **CSV Import Mapping Header** custom metadata type is a lighter-weight mapping definition that captures the key import context values of record type, target object, and mapping field.

In the current source package, the richer import runtime is driven primarily through `CSV_Import_Mapping__mdt` and its child filter metadata, but this metadata type still documents the package's intended header-level configuration shape.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| CSV Import RecordType | `CSV_Import_RecordType__c` | Text | 255 |
| Import Object | `Import_Object__c` | Metadata Relationship |  |
| Mapping Field | `Mapping_Field__c` | Metadata Relationship |  |

---

## Field Details

| Field | Purpose |
|------|------|
| CSV Import RecordType | Identifies which runtime record type this header applies to. |
| Import Object | Identifies the Salesforce object that an import process should query. |
| Mapping Field | Identifies the target field that will be populated with the current export record ID. |
