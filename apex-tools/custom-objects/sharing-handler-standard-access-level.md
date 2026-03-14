# Sharing Handler Standard Access Level

## API Name
`Sharing_Handler_Standard_Access_Level__mdt`

## Description

The **Sharing Handler Standard Access Level** custom metadata type stores additional access-level field values needed when sharing standard Salesforce objects.
Some standard share objects use multiple access-level fields, and this metadata allows those values to be configured rather than hardcoded.

This helps the sharing framework support more complex standard-object sharing scenarios.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Access Level Name | Access_Level_Name__c | Text | 255 |
| Access Level Value | Access_Level_Value__c | Text | 255 |
| Sharing Handler | Sharing_Handler__c | Metadata Relationship | Sharing_Handler__mdt |
| Sharing Handler Child | Sharing_Handler_Child__c | Metadata Relationship | Sharing_Handler_Child__mdt |

---

## Field Details

| Field | Purpose |
|------|------|
| Access Level Name | Stores the name of the access-level field to populate on a standard share record. |
| Access Level Value | Stores the value to apply to that access-level field. |
| Sharing Handler | Optionally links the setting to a parent-level sharing configuration. |
| Sharing Handler Child | Optionally links the setting to a child-level sharing configuration. |
