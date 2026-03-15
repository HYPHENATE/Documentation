# Extended Field History Control

## API Name
`ExtendedFieldHistoryControl__c`

## Description

The **Extended Field History Control** custom setting governs whether existing audit rows can be edited or deleted.

This lets organisations decide whether they want the package to behave as a stricter audit log or allow administrators to correct or remove rows when necessary.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Allow Delete | `AllowDelete__c` | Checkbox |  |
| Allow Edit | `AllowEdit__c` | Checkbox |  |

---

## Field Details

| Field | Purpose |
|------|------|
| Allow Delete | Determines whether `FieldAuditHistory__c` rows can be deleted outside the package's batch clean-up path. |
| Allow Edit | Determines whether `FieldAuditHistory__c` rows can be updated manually. |
