# Check Filter

## API Name
`Check_Filter__c`

## Description

The **Check Filter** object defines record-level conditions used to decide whether a filtered checklist category should apply.

Dynamic Checks uses this object to make checklist visibility conditional rather than universal. This means teams can show the right checklist at the right time instead of displaying every category on every record.

In practice, this helps organisations keep checklist experiences relevant to the current business context, such as only showing certain controls for records at a specific stage, status, or threshold.

Each **Check Filter** record belongs to a **Check Template Header** and contributes one condition that can be evaluated by the package filtering logic.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Check Filter Name | Name | Text | 80 |
| Check Template Header | Check_Template_Header__c | Master-Detail | Check_Template_Header__c |
| Field Name | Field_Name__c | Text | 255 |
| Field Operator | Field_Operator__c | Picklist | equals / not equal to / greater than / greater than or equals / less than / less than or equals |
| Field Value | Field_Value__c | Text | 255 |

---

## Field Details

| Field | Purpose |
|------|------|
| Check Filter Name | Identifies the individual filter row. |
| Check Template Header | Connects the filter to the checklist category that should be evaluated. |
| Field Name | Stores the API name of the field to inspect on the target record. |
| Field Operator | Defines how the record value should be compared against the configured filter value. |
| Field Value | Stores the comparison value used by the filter logic. |

---

## Usage Notes

- Use filters when a checklist should only appear for some records, such as a record type, stage, status, or amount threshold.
- `ChecksFilter` reads these records and evaluates them according to the filter type defined on the related template header.
- Because filters are configuration-driven, admins can adapt checklist visibility without changing the package code.
