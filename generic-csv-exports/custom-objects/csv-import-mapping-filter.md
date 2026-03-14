# CSV Import Mapping Filter

## API Name
`CSV_Import_Mapping_Filter__mdt`

## Description

The **CSV Import Mapping Filter** custom metadata type defines the individual field conditions used by the import helper when it builds its dynamic SOQL query.

Each filter belongs to a parent `CSV_Import_Mapping__mdt` record and contributes one condition to the final where clause. Together they let admins define which records should be linked to a given `CSV_Export__c` record without rewriting Apex.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| CSV Import Mapping | `CSV_Import_Mapping__c` | Metadata Relationship |  |
| Field API Name | `Field_API_Name__c` | Text | 255 |
| Filter type | `Filter_type__c` | Picklist | equals, not equals, greater than, greater than or equals, less than, less than or equals |
| Value | `Value__c` | Text | 255 |

---

## Field Details

| Field | Purpose |
|------|------|
| CSV Import Mapping | Links the filter back to the parent import-mapping definition. |
| Field API Name | Identifies the field that should be evaluated in the generated SOQL where clause. |
| Filter type | Tells the helper which comparison operator to use when building the condition. |
| Value | Stores the comparison value that will be applied at runtime. |
