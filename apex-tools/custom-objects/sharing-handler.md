# Sharing Handler

## API Name
`Sharing_Handler__mdt`

## Description

The **Sharing Handler** custom metadata type defines parent-level sharing rules used by the ApexTools dynamic sharing framework.
It allows teams to describe which object should be shared, which role the sharing logic applies to, what access level should be granted, and whether custom sharing behaviour or batch processing is needed.

This metadata type is central to the package's configurable record-sharing model.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Access Level | Access_Level__c | Picklist | All / Edit / Read |
| Apex Sharing Reason | Apex_Sharing_Reason__c | Text | 255 |
| Batch Mode | Batch_Mode__c | Checkbox | True / False |
| Custom Share Delete Batch Operation | Custom_Share_Delete_Batch_Operation__c | Picklist | Update / Delete |
| Custom Share Delete Batch Values | Custom_Share_Delete_Batch_Values__c | Text Area | JSON |
| Custom Share Delete Class | Custom_Share_Delete_Class__c | Text | 255 |
| Custom Share Object | Custom_Share_Object__c | Metadata Relationship | EntityDefinition |
| Custom Sharing Class | Custom_Sharing_Class__c | Text | 255 |
| Custom Values | Custom_Values__c | Text Area | JSON |
| Enable Logging | Enable_Logging__c | Checkbox | True / False |
| Fields For Query | Fields_For_Query__c | Long Text Area | 32768 |
| Parent Field | Parent_Field__c | Metadata Relationship | FieldDefinition |
| Primary Object | Primary_Object__c | Metadata Relationship | EntityDefinition |
| Share Record Access Level Field | Share_Record_Access_Level_Field__c | Text | 255 |
| Share Record Parent Field | Share_Record_Parent_Field__c | Text | 255 |
| Sharing Batch Size | Sharing_Batch_Size__c | Number | 18,0 |
| User Role | User_Role__c | Text | 255 |
| WHERE Clause | WHERE_Clause__c | Long Text Area | 10000 |

---

## Field Details

| Field | Purpose |
|------|------|
| Access Level | Defines the access level to be granted by the generated share records. |
| Apex Sharing Reason | Stores the sharing reason name or API name to apply to the share records. |
| Batch Mode | Controls whether sharing should run in batch for large data volumes. |
| Custom Share Delete Batch Operation | Defines whether custom share cleanup should update or delete records in batch mode. |
| Custom Share Delete Batch Values | Stores JSON values used when batch cleanup performs updates instead of deletes. |
| Custom Share Delete Class | Identifies the custom Apex class used to delete custom share records. |
| Custom Share Object | Identifies a non-standard share object used for custom sharing patterns. |
| Custom Sharing Class | Identifies the custom Apex class used to create custom share records. |
| Custom Values | Stores JSON configuration passed into custom sharing logic. |
| Enable Logging | Controls whether sharing errors should create Apex Log records. |
| Fields For Query | Stores additional fields to include when building source record queries. |
| Parent Field | Identifies the field that connects the primary object to its parent context. |
| Primary Object | Identifies the top-level object for this sharing configuration. |
| Share Record Access Level Field | Defines the name of the access-level field on the generated share record. |
| Share Record Parent Field | Defines the parent-link field on the generated share record. |
| Sharing Batch Size | Defines the batch size to use when batch sharing is enabled. |
| User Role | Defines the business role this sharing rule applies to. |
| WHERE Clause | Stores optional criteria used to limit which records are shared. |

---

## Validation Rules

| Name | Purpose |
|------|------|
| Custom_Share_Must_Have_Custom_Classes | Ensures supporting custom classes are provided when a custom share object is used. |
| If_Batch_Delete_Op_Update_Need_Values | Ensures update values are provided when batch delete operation is set to update. |
| Is_Batch_Mode_Must_Have_Batch_Size | Ensures a batch size is provided when batch mode is enabled. |
