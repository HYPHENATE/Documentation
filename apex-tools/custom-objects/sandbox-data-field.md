# Sandbox Data Field

## API Name
`Sandbox_Data_Field__mdt`

## Description

The **Sandbox Data Field** custom metadata type defines how individual fields should be populated when sandbox data is generated.
It works alongside **Sandbox Data Object** records to describe which source column maps to which target field, what data type should be used, and whether lookup handling is required.

This metadata helps make sandbox refresh preparation more repeatable and easier to maintain.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Column Number | ColumnNumber__c | Number | 18,0 |
| Data Type | DataType__c | Picklist | STRING / NUMBER / DATE / BOOLEAN |
| Disabled | Disabled__c | Checkbox | True / False |
| Field | Field__c | Metadata Relationship | EntityParticle |
| Is Lookup | IsLookup__c | Checkbox | True / False |
| Lookup Object | LookupObject__c | Metadata Relationship | EntityDefinition |
| Object | Object__c | Metadata Relationship | EntityDefinition |
| Sandbox Data Object | SandboxDataObject__c | Metadata Relationship | Sandbox_Data_Object__mdt |

---

## Field Details

| Field | Purpose |
|------|------|
| Column Number | Defines which source column should be used for this field mapping. |
| Data Type | Defines how the incoming source value should be interpreted. |
| Disabled | Allows the field mapping to be turned off without deleting it. |
| Field | Identifies the target Salesforce field to populate. |
| Is Lookup | Indicates that the field should be treated as a lookup relationship. |
| Lookup Object | Identifies the related object used when resolving lookups. |
| Object | Identifies the object the mapped field belongs to. |
| Sandbox Data Object | Links the field mapping to its parent sandbox data object configuration. |
