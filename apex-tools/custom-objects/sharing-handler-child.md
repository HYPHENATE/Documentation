# Sharing Handler Child

## API Name
`Sharing_Handler_Child__mdt`

## Description

The **Sharing Handler Child** custom metadata type defines child-level sharing rules used alongside parent sharing configurations.
It allows related child records to inherit or follow sharing logic defined on a parent configuration while still supporting their own access levels, filters, and optional custom sharing classes.

This is useful where access needs to cascade from a top-level record to one or more related records.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Access Level | Access_Level__c | Picklist | All / Edit / Read |
| Apex Sharing Reason | Apex_Sharing_Reason__c | Text | 255 |
| Child Object | Child_Object__c | Metadata Relationship | EntityDefinition |
| Child Relationship Name | Child_Relationship_Name__c | Text | 255 |
| Custom Share Delete Batch Operation | Custom_Share_Delete_Batch_Operation__c | Picklist | Update / Delete |
| Custom Share Delete Batch Values | Custom_Share_Delete_Batch_Values__c | Text Area | JSON |
| Custom Share Delete Class | Custom_Share_Delete_Class__c | Text | 255 |
| Custom Share Object | Custom_Share_Object__c | Metadata Relationship | EntityDefinition |
| Custom Sharing Class | Custom_Sharing_Class__c | Text | 255 |
| Custom Values | Custom_Values__c | Text Area | JSON |
| Enable Logging | Enable_Logging__c | Checkbox | True / False |
| Share Record Access Level Field | Share_Record_Access_Level_Field__c | Text | 255 |
| Share Record Parent Field | Share_Record_Parent_Field__c | Text | 255 |
| Sharing Handler | Sharing_Handler__c | Metadata Relationship | Sharing_Handler__mdt |
| WHERE Clause | WHERE_Clause__c | Long Text Area | 10000 |

---

## Field Details

| Field | Purpose |
|------|------|
| Access Level | Defines the access level to be applied to child share records. |
| Apex Sharing Reason | Stores the sharing reason to use for child sharing. |
| Child Object | Identifies the related child object that should also be shared. |
| Child Relationship Name | Defines the child relationship name used to query related records. |
| Custom Share Delete Batch Operation | Defines whether custom child share cleanup should update or delete records in batch mode. |
| Custom Share Delete Batch Values | Stores JSON values used for update-based child share cleanup. |
| Custom Share Delete Class | Identifies the custom Apex class used to delete child custom share records. |
| Custom Share Object | Identifies a non-standard child share object. |
| Custom Sharing Class | Identifies the custom Apex class used to create child custom share records. |
| Custom Values | Stores JSON configuration for child custom sharing logic. |
| Enable Logging | Controls whether child sharing errors should be logged. |
| Share Record Access Level Field | Defines the access-level field on the child share record. |
| Share Record Parent Field | Defines the field linking the child share record back to its source record. |
| Sharing Handler | Links the child sharing rule to its parent sharing configuration. |
| WHERE Clause | Stores optional criteria limiting which child records are included. |

---

## Validation Rules

| Name | Purpose |
|------|------|
| Custom_Share_Must_Have_Custom_Classes | Ensures custom supporting classes are provided when a custom share object is used. |
| If_Batch_Delete_Op_Update_Need_Values | Ensures update values are provided when update is selected for batch delete handling. |
