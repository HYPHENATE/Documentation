# Trigger Control

## API Name
`Trigger_Control__c`

## Description

The **Trigger Control** object is used to deactivate metadata-driven triggers for a specific user or profile.
If a record exists with trigger deactivation enabled, trigger logic routed through the ApexTools trigger framework can be bypassed for that user or profile.

This is useful for administration, deployment support, controlled data operations, and troubleshooting.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Triggers Deactivated | Triggers_Deactivated__c | Checkbox | True / False |

---

## Field Details

| Field | Purpose |
|------|------|
| Triggers Deactivated | Controls whether metadata-driven triggers should be switched off for the related user or profile. |
