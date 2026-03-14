# Test Record Generator Field

## API Name
`Test_Record_Generator_Field__mdt`

## Description

The **Test Record Generator Field** custom metadata type defines field-level values used by a test record generator.
It allows a parent generator configuration to describe which fields should be populated, what values should be supplied, and whether a field-specific helper class should be used.

This makes test-data setup more configurable and easier to extend.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Apex Class | Apex_Class__c | Text | 255 |
| Apex Class Parameters | Apex_Class_Parameters__c | Long Text Area | 131072 |
| Field | Field__c | Text | 255 |
| Test Record Generator | Test_Record_Generator__c | Metadata Relationship | Test_Record_Generator__mdt |
| Value | Value__c | Text | 255 |

---

## Field Details

| Field | Purpose |
|------|------|
| Apex Class | Optionally identifies a helper class used to generate the field value dynamically. |
| Apex Class Parameters | Stores JSON parameters for the field-level helper class. |
| Field | Identifies the field to populate on the generated test record. |
| Test Record Generator | Links the field definition to its parent generator configuration. |
| Value | Stores a direct value used when no custom field helper is needed. |
