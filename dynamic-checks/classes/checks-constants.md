# ChecksConstants

## API Name
`ChecksConstants`

## Description

`ChecksConstants` centralises the shared string constants used across the **Dynamic Checks** package.

These values are referenced by filtering logic, record applicability checks, and custom answer handling so that the rest of the codebase does not rely on duplicated hardcoded strings.

---

## Sharing Model
`N/A`

## Tested By
`ChecksConstantsTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Applicability constants | Stores the values used to distinguish checks that apply to all records from those that apply only by filter. |
| Filter logic constants | Stores the supported `AND`, `OR`, `CUSTOM`, and `N/A` filter type values. |
| Operator constants | Stores the supported comparison operators used by `Check_Filter__c` rows. |
| Utility constants | Stores the delimiter used when multiple custom-answer values are provided in one field. |

---

## Public Constants

| Constant | Value | Purpose |
|------|------|------|
| `VALID_FOR_ALL` | `All` | Indicates a header applies to all records of the configured object. |
| `VALID_FOR_FILTERED` | `By Filter` | Indicates a header applies only when its filters match the record. |
| `FILTER_TYPE_AND` | `AND` | Requires all filter rows to match. |
| `FILTER_TYPE_OR` | `OR` | Requires at least one filter row to match. |
| `FILTER_TYPE_CUSTOM` | `CUSTOM` | Reserved constant for advanced custom logic. |
| `FILTER_TYPE_N_A` | `N/A` | Used where filter logic is not applicable. |
| `FIELD_OPERATOR_EQUALS` | `equals` | Equality comparison operator. |
| `FIELD_OPERATOR_NOT_EQUALS` | `not equal to` | Inequality comparison operator. |
| `FIELD_OPERATOR_GREATER_THAN` | `greater than` | Greater-than comparison operator. |
| `FIELD_OPERATOR_GREATER_THAN_EQUALS` | `greater than or equals` | Greater-than-or-equals comparison operator. |
| `FIELD_OPERATOR_LESS_THAN` | `less than` | Less-than comparison operator. |
| `FIELD_OPERATOR_LESS_THAN_EQUALS` | `less than or equals` | Less-than-or-equals comparison operator. |
| `FIELD_VALUE_OR_DELIMITER` | `,` | Delimiter used when one field stores multiple allowed comparison values. |

---

## Runtime Notes

| Area | Detail |
|------|------|
| Filter consistency | `ChecksFilter` relies on these values to keep operator handling consistent with the configured metadata. |
| Metadata alignment | Admin configuration in picklists and templates should align with these constant values for the package to behave correctly. |
| Maintainability | Centralising these values reduces the risk of drift across helper, filter, and trigger code. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `ChecksHelper` | Uses applicability constants when deciding how headers should be processed. |
| `ChecksFilter` | Uses filter logic, operator, and delimiter constants during evaluation. |

---

## Typical Usage

This class is referenced wherever the package needs to compare metadata values reliably instead of using hardcoded string literals.

---

## Related Classes

- [ChecksHelper](/dynamic-checks/classes/checks-helper)
- [ChecksFilter](/dynamic-checks/classes/checks-filter)
