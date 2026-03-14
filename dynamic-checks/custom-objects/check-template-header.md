# Check Template Header

## API Name
`Check_Template_Header__c`

## Description

The **Check Template Header** object is the top-level grouping object for **Dynamic Checks** configuration.

It defines one checklist category, the object the category applies to, whether the category should appear for all records or only filtered records, and whether only the record owner should be allowed to update checks in that category.

In practical terms, this is the object admins use to say "for this kind of record, show this category of checks in this order, and only under these conditions."

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Check Template Header Name | Name | Auto Number | `CTH-{000000}` |
| Category | Category__c | Text | 255 |
| Description | Description__c | Long Text Area | 32768 |
| Filter Type | Filter_Type__c | Picklist | `AND`, `OR`, `CUSTOM`, `N/A` |
| Order | Order__c | Number | 18,0 |
| Owner Edit Only | Owner_Edit_Only__c | Checkbox | True / False |
| Records Valid For | Records_Valid_For__c | Picklist | `All`, `By Filter` |
| SObject | SObject__c | Text | 255 |

---

## Field Details

| Field | Purpose |
|------|------|
| Check Template Header Name | System-generated identifier for the category configuration record. |
| Category | The category label shown to end users in the checklist UI. |
| Description | Additional explanatory text shown with the category in the record-page experience. |
| Filter Type | Defines how child filter rows should be combined when the category is filter-driven. |
| Order | Controls the display order of categories in the checklist experience. |
| Owner Edit Only | Restricts category editing to the parent record owner when enabled. |
| Records Valid For | Determines whether the category applies to all records of the target object or only records that match configured filters. |
| SObject | Stores the API name of the target object the category applies to. |

---

## Usage Notes

- Each header acts as the parent for related `Check_Template__c` and `Check_Filter__c` records.
- Headers marked as valid for all records are processed directly by `ChecksHelper`.
- Headers marked as valid by filter are evaluated by `ChecksFilter` before any live checks are created.
- A typical setup is one header per meaningful checklist category, such as "Eligibility Checks" on a funding request or "Handover Checks" on a case record.
