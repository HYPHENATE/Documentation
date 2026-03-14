# Trigger Handler

## API Name
`Trigger_Handler__mdt`

## Description

The **Trigger Handler** custom metadata type defines which Apex class should run for a given object and trigger event.
It is a core part of the ApexTools trigger framework and allows trigger behaviour to be configured through metadata rather than hardcoded into trigger bodies.

This supports cleaner triggers, ordered execution, and more maintainable automation design.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Active | Active__c | Checkbox | True / False |
| Apex Class | Apex_Class__c | Text | 255 |
| Description | Description__c | Long Text Area | 131072 |
| Event | Event__c | Picklist | BEFORE_DELETE / BEFORE_INSERT / BEFORE_UPDATE / AFTER_DELETE / AFTER_INSERT / AFTER_UNDELETE / AFTER_UPDATE |
| Order | Order__c | Number | 18,0 |
| Parameters | Parameters__c | Long Text Area | 131072 |
| SObject | SObject__c | Text | 255 |

---

## Field Details

| Field | Purpose |
|------|------|
| Active | Determines whether the trigger handler should be used. |
| Apex Class | Identifies the handler class that should be executed. |
| Description | Stores explanatory notes about the handler configuration. |
| Event | Defines the trigger event the handler applies to. |
| Order | Controls execution order when multiple handlers exist for the same object and event. |
| Parameters | Stores JSON parameters used to configure the handler class. |
| SObject | Identifies the object the trigger handler applies to. |
