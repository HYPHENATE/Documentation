# Apex Logger Config

## API Name
`Apex_Logger_Config__mdt`

## Description

The **Apex Logger Config** custom metadata type controls how ApexTools logging behaves.
It allows developers and administrators to define which objects or Flows should be logged, whether successes and errors should be recorded, how long logs should be kept, and whether related lookup values should be populated.

This metadata type gives the logging framework flexibility without requiring hardcoded rules for every use case.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Days To Keep | Days_To_Keep__c | Number | 18,0 |
| Description | Description__c | Text Area |  |
| Flow API Name | Flow_API_Name__c | Text | 255 |
| Has Lookup Field | Has_Lookup_Field__c | Checkbox | True / False |
| Is Test Record | Is_Test_Record__c | Checkbox | True / False |
| Log Errors | Log_Errors__c | Checkbox | True / False |
| Log Successes | Log_Successes__c | Checkbox | True / False |
| Lookup Field | Lookup_Field__c | Metadata Relationship | FieldDefinition |
| Set Status Field | Set_Status_Field__c | Checkbox | True / False |
| SObject | SObject__c | Metadata Relationship | EntityDefinition |

---

## Field Details

| Field | Purpose |
|------|------|
| Days To Keep | Defines how long related log records should be retained. |
| Description | Stores explanatory notes about the configuration. |
| Flow API Name | Identifies the Flow this config should apply to when logging Flow faults. |
| Has Lookup Field | Indicates whether the log should populate a lookup field to the related record. |
| Is Test Record | Marks a configuration as intended for testing scenarios. |
| Log Errors | Controls whether errors should be logged. |
| Log Successes | Controls whether successful processing should also be logged. |
| Lookup Field | Identifies which field on the log record should store a related record lookup. |
| Set Status Field | Controls whether the log status field should be populated automatically. |
| SObject | Identifies the object this logging configuration applies to. |

---

## Validation Rules

| Name | Purpose |
|------|------|
| If_Has_Lookup_Populate_Lookup_Field | Ensures that the object and lookup field are both provided when lookup logging is enabled. |
