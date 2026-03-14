# Sandbox Data Object

## API Name
`Sandbox_Data_Object__mdt`

## Description

The **Sandbox Data Object** custom metadata type defines which objects should be populated during sandbox data generation.
It is used to control the order of processing, identify the static resource that contains source data, and optionally define whether created values should be stored for later use in related records.

This supports a more repeatable sandbox setup process after refreshes.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Disabled | Disabled__c | Checkbox | True / False |
| Object | Object__c | Metadata Relationship | EntityDefinition |
| Order | Order__c | Number | 18,0 |
| Static Resource Name | StaticResourceName__c | Text | 255 |
| Store Field Value | StoreFieldValue__c | Metadata Relationship | EntityParticle |
| Store Value | StoreValue__c | Checkbox | True / False |

---

## Field Details

| Field | Purpose |
|------|------|
| Disabled | Allows the object configuration to be excluded from sandbox data generation. |
| Object | Identifies which Salesforce object should be populated. |
| Order | Controls processing order so parent records can be created before dependent records. |
| Static Resource Name | Identifies the static resource containing the source data. |
| Store Field Value | Identifies which field value should be stored for later lookup resolution. |
| Store Value | Controls whether values from created records should be stored and reused during generation. |
