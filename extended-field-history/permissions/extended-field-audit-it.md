# Extended Field Audit IT

## API Name
`ExtendedFieldAuditIT`

## Description

`ExtendedFieldAuditIT` is the packaged permission set for users who need access to the Extended Field History runtime and audit data.

It grants access to the history object, the controller and helper classes, the tracking metadata type, and the control custom setting used to protect audit rows.

---

## Access Summary

| Area | Detail |
|------|------|
| Apex access | Grants access to the batch, controller, handler, helper, and record-view classes. |
| Custom metadata | Grants access to `ExtendedFieldAuditHistory__mdt` so tracking rules can be read. |
| Custom settings | Grants access to `ExtendedFieldHistoryControl__c` so row-protection behaviour can be applied. |
| Object access | Grants read and create access to `FieldAuditHistory__c`. |

---

## Field Access Highlights

| Field | Access | Purpose |
|------|------|------|
| `FieldAPIName__c` | Read | Shows which field changed. |
| `FieldLabel__c` | Read | Shows a user-friendly label for the changed field. |
| `NewValue__c` | Read | Stores the new value after the change. |
| `OldValue__c` | Read | Stores the previous value before the change. |
| `ObjectName__c` | Read | Identifies the source object. |
| `RecordId__c` | Read | Identifies the source record. |
| `Type__c` | Read | Indicates whether the audit row came from a created or updated value. |

---

## Operational Notes

| Topic | Detail |
|------|------|
| Intended users | Suitable for admins, compliance users, auditors, or internal staff who need to view or manage the audit trail. |
| Create access | The package requires create access to `FieldAuditHistory__c` so runtime audit rows can be inserted. |
| Edit and delete | The permission set does not grant edit or delete access to audit rows; further control is handled through the package's control object and trigger logic. |
