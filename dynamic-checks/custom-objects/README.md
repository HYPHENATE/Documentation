# Custom Objects

Dynamic Checks is driven by four main custom objects.

Together these objects let admins define reusable checklist logic, control when checklist categories should apply, and store the live record-level checks that users complete on supported records.

---

## Object Overview

| Object | Purpose |
|------|------|
| [Check Template Header](/dynamic-checks/custom-objects/check-template-header) | Defines one checklist category, the target object, and whether the category applies to all records or only filtered records. |
| [Check Template](/dynamic-checks/custom-objects/check-template) | Defines one reusable checklist item and its display, comment, and optional flow-launch behaviour. |
| [Check Filter](/dynamic-checks/custom-objects/check-filter) | Stores the field-based conditions used to decide whether a filtered category should apply. |
| [Check](/dynamic-checks/custom-objects/check) | Stores the live checklist item created for a specific business record. |

---

## Design Notes

| Area | Detail |
|------|------|
| Configuration layer | `Check_Template_Header__c`, `Check_Template__c`, and `Check_Filter__c` form the admin-managed configuration model. |
| Runtime layer | `Check__c` stores the generated checklist state that users see and update on records. |
| Metadata-driven applicability | Categories can apply universally or only when record values satisfy configured filter rules. |
| Automation support | Template and live check records can carry flow-launch settings that support downstream automation on completion. |
