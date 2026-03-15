# User Guide

Admins configure the tracking metadata and assign the packaged audit access permission set.

In a typical setup, an admin creates `ExtendedFieldAuditHistory__mdt` records to define which fields should be tracked for which objects and whether created values, updated values, or both should be stored. Once this configuration is active, the package begins writing audit rows into `FieldAuditHistory__c` when tracked records change.

End users and administrators can then review field-change history through the packaged `extendedFieldHistory` component on record pages. Where larger history volumes exist, they can also move into the packaged report view to see the full audit trail.

Admins can additionally control whether audit rows are editable or deletable through `ExtendedFieldHistoryControl__c`, which is useful when balancing data stewardship needs against the requirement for a tamper-resistant audit log.
