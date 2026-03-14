# ChecksFilter

## API Name
`ChecksFilter`

## Description

`ChecksFilter` evaluates whether filter-driven checklist headers should apply to a record.

It reads the `Check_Filter__c` rows attached to each header, dynamically queries the fields required for evaluation, and then checks whether the current record satisfies the configured conditions.

This is what makes **Dynamic Checks** adaptable across different processes. Without this class, checklist categories would need to appear for every record of a supported object rather than only when business criteria are met.

---

## Sharing Model
`without sharing`

## Tested By
`ChecksHelperTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Dynamic field collection | Inspects filter metadata to determine which record fields need to be queried. |
| Record loading | Builds and runs a dynamic SOQL query for the record IDs being evaluated. |
| Filter evaluation | Applies `AND` or `OR` logic across the configured filter rows for each header. |
| Field type handling | Detects field data types so equality and numeric comparisons can be processed correctly. |
| Relationship support | Supports dotted field references by traversing relationship fields where possible. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `ChecksFilter(List<Id> recordIds, List<Check_Template_Header__c> checkTemplateHeadersToFilter)` | Constructor | Loads the record describe context, determines required fields, and queries the records to process. |
| `getFilteredCheckTemplateHeaders(Id recordId)` | `Map<Id, List<Check_Template_Header__c>>` | Returns the subset of filter-driven headers that match the supplied record. |

---

## Internal Methods

| Method | Purpose |
|------|------|
| `fieldFilterMatch` | Applies the header-level filter logic across all child `Check_Filter__c` rows. |
| `getSObjectFieldType` | Resolves the display type of the configured field reference. |
| `getSObjectField` | Retrieves the current value of a field, including relationship traversal where needed. |
| `getSObjectFieldTypeRelationship` | Resolves field types when the configured field path crosses a relationship. |
| `handleFilterChecks` | Evaluates one filter row using the selected operator and record value. |

---

## Runtime Notes

| Area | Detail |
|------|------|
| Supported logic | The class actively supports `AND` and `OR` logic. A constant for custom logic exists elsewhere in the package, but advanced custom filter logic is not implemented here. |
| Supported operators | Equality, inequality, greater-than, greater-than-or-equals, less-than, and less-than-or-equals comparisons are supported. |
| Multi-value equals | For string and picklist fields, equals comparisons can support comma-delimited values using the package delimiter constant. |
| Relationship fields | Dotted field references such as parent lookups can be evaluated when the relationship can be resolved from describe information. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `Check_Template_Header__c` | Supplies the headers whose filter criteria need to be evaluated. |
| `Check_Filter__c` | Stores the individual field, operator, and value conditions for each header. |
| `ChecksConstants` | Provides the supported filter logic and operator values used during evaluation. |
| Schema describe APIs | Used to resolve field types and relationship traversal dynamically. |

---

## Typical Usage

This class is called by `ChecksHelper` when a header is configured as valid only for filtered records instead of all records for the object.

---

## Related Classes

- [ChecksHelper](/dynamic-checks/classes/checks-helper)
- [ChecksConstants](/dynamic-checks/classes/checks-constants)
