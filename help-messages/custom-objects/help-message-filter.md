# Help Message Filter

## API Name
`Help_Message_Filter__c`

## Description

The **Help Message Filter** object stores the individual conditions used to decide whether a help message should appear on a record.

Each filter record belongs to one `Help_Message__c` parent and defines a field, operator, and comparison value. The parent message then decides whether those filters should be combined with `AND` or `OR` logic.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Help Message Filter Name | Name | Text | 80 |
| Field Name | Field_Name__c | Text | 255 |
| Field Operator | Field_Operator__c | Picklist | equals / not equal to / greater than / greater than or equals / less than / less than or equals |
| Field Value | Field_Value__c | Text | 255 |
| Help Message | Help_Message__c | Master-Detail | Help_Message__c |
| Type | Type__c | Text / Picklist-style config | Package-defined filter type support |

---

## Field Details

| Field | Purpose |
|------|------|
| Help Message Filter Name | Identifies the filter row. |
| Field Name | Stores the field API name, including relationship paths where needed. |
| Field Operator | Defines how the current record value should be compared. |
| Field Value | Stores the comparison value used in the filter. |
| Help Message | Connects the filter to its parent message. |
| Type | Stores filter-type metadata used in the overall configuration pattern. |

---

## Usage Notes

- Filters are only needed when a message should not appear for every record of the target object.
- `HelpMessageHelper` evaluates these rows dynamically against the current record.
- Relationship field paths can be used where the helper can resolve the target value from the record context.
