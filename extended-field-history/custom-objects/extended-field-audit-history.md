# Extended Field Audit History

## API Name
`ExtendedFieldAuditHistory__mdt`

## Description

The **Extended Field Audit History** custom metadata type is the configuration layer that tells the package what to audit.

Each metadata record defines the object to track, the field to track, whether the rule is active, and whether created values, updated values, or both should be captured.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Active | `Active__c` | Checkbox |  |
| Track Created Values | `TrackCreatedValues__c` | Checkbox |  |
| Tracking Field | `TrackingField__c` | Metadata Relationship |  |
| Tracking Object | `TrackingObject__c` | Metadata Relationship |  |
| Track Updated Values | `TrackUpdatedValues__c` | Checkbox |  |

---

## Field Details

| Field | Purpose |
|------|------|
| Active | Turns the tracking rule on or off without deleting the metadata. |
| Track Created Values | Determines whether non-null values should be captured when a record is first inserted. |
| Tracking Field | Identifies the field that should be audited. |
| Tracking Object | Identifies the object the field belongs to. |
| Track Updated Values | Determines whether changes to the field should be captured on update. |
