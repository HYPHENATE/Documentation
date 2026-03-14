# HelpMessageConstants

## API Name
`HelpMessageConstants`

## Description

`HelpMessageConstants` centralises the filter and operator strings used throughout the **Help Messages** package.

This keeps the controller and helper logic aligned with the configured metadata values and reduces repeated hardcoded strings.

---

## Sharing Model
`with sharing`

## Tested By
`HelpMessageController_Test`

---

## Public Constants

| Constant | Value | Purpose |
|------|------|------|
| `FILTER_LOGIC_AND` | `AND` | Requires all filters on a message to match. |
| `FILTER_LOGIC_OR` | `OR` | Requires any one filter on a message to match. |
| `FIELD_OPERATOR_EQUALS` | `equals` | Equality comparison operator. |
| `FIELD_OPERATOR_NOT_EQUALS` | `not equal to` | Inequality comparison operator. |
| `FIELD_OPERATOR_GREATER_THAN` | `greater than` | Greater-than comparison operator. |
| `FIELD_OPERATOR_GREATER_THAN_EQUALS` | `greater than or equals` | Greater-than-or-equals comparison operator. |
| `FIELD_OPERATOR_LESS_THAN` | `less than` | Less-than comparison operator. |
| `FIELD_OPERATOR_LESS_THAN_EQUALS` | `less than or equals` | Less-than-or-equals comparison operator. |
| `FIELD_VALUE_OR_DELIMITER` | `,` | Delimiter used when one filter value contains multiple allowed values. |
