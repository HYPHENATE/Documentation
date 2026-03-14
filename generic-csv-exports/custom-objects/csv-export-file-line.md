# CSV Export File Line

## API Name
`CSV_Export_File_Line__mdt`

## Description

The **CSV Export File Line** custom metadata type defines the field-level rows that make up an export file. These records sit underneath a parent `CSV_Export_File__mdt` definition and tell the package which field values to output and in what order.

This allows a single export file to be built from one or more logical lines per source record, which is useful when integrations need repeated rows or a specific flat-file structure.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| CSV Export File | `CSV_Export_File__c` | Metadata Relationship |  |
| Line | `Line__c` | Number | 18,0 |
| Order | `Order__c` | Number | 18,0 |
| Output Field API Name | `Output_Field_API_Name__c` | Text | 255 |

---

## Field Details

| Field | Purpose |
|------|------|
| CSV Export File | Links the line definition back to the parent export-file metadata record. |
| Line | Groups fields into the same output row when a source record produces multiple lines in the CSV. |
| Order | Controls the sequence of values within the output row. |
| Output Field API Name | Stores the SOQL field path that should be queried and written into the CSV output. |
