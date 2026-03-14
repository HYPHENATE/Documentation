# Check

## API Name
`Check__c`

## Description

The **Check** object is the live checklist item created for a specific business record.

This is the operational record that users actually see and update in the checklist interface. Each row is generated from a `Check_Template__c` definition and stores the real completion state, chosen answer values, comments, and any runtime automation data needed after completion.

Because these are live, record-level rows rather than reusable templates, `Check__c` is also the best place to report on checklist completion activity over time.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Check ID | Name | Auto Number | `CID-{000000000}` |
| Category | Category__c | Text | 255 |
| Check Comments | CheckComments__c | Long Text Area | 32768 |
| Checked | Checked__c | Checkbox | True / False |
| Check Value | CheckValue__c | Text | 255 |
| Check Template | Check_Template__c | Lookup / Master source | Check_Template__c |
| Disabled Criteria Field | Disabled_Criteria_Field__c | Text | 255 |
| Display Type | Display_Type__c | Text / Picklist-style runtime value | Package-defined display mode |
| Flow API Name | Flow_API_Name__c | Text | 255 |
| Flow Input Variables | Flow_Input_Variables__c | Long Text Area | 32768 |
| Header Disabled Criteria Field | Header_Disabled_Criteria_Field__c | Text | 255 |
| Launch Flow on Complete | Launch_Flow_On_Complete__c | Checkbox | True / False |
| Order | Order__c | Number | 18,0 |
| Owner Edit Only | Owner_Edit_Only__c | Checkbox | True / False |
| Record Id | Record_Id__c | Text | 18 |
| SObject | SObject__c | Text | 255 |
| Title | Title__c | Text | 255 |

---

## Field Details

| Field | Purpose |
|------|------|
| Check ID | System-generated identifier for the live checklist record. |
| Category | Stores the category label copied onto the live check for reporting and display use. |
| Check Comments | Stores optional comments entered by users while working through the checklist. |
| Checked | Stores the completion state for standard binary checks. |
| Check Value | Stores the selected answer for custom display type checks. |
| Check Template | Links the live check back to the reusable template it was generated from. |
| Disabled Criteria Field | Stores runtime criteria used by the package when disabling a check in specific scenarios. |
| Display Type | Stores the display style used by the UI when rendering the check. |
| Flow API Name | Stores the flow that should launch after completion when enabled. |
| Flow Input Variables | Stores the JSON payload used when the package starts a configured flow. |
| Header Disabled Criteria Field | Stores category-level disabled criteria used in the runtime experience. |
| Launch Flow on Complete | Indicates whether the completed check should trigger a flow launch. |
| Order | Controls the display order of the check within its category. |
| Owner Edit Only | Indicates whether only the parent record owner should edit this check. |
| Record Id | Stores the ID of the parent business record the check belongs to. |
| SObject | Stores the API name of the parent record's object type. |
| Title | Stores the checklist item title shown to end users. |

---

## Usage Notes

- Live checks are created on demand by `ChecksHelper` when a record qualifies for the relevant category.
- Users update these records through the `dynamicCheck` Lightning component using Lightning Data Service.
- `CheckLaunchFlow` uses the flow-related fields on this object to trigger downstream automation after completion.
- `Check__c` is history-enabled and reportable, which makes it well suited for operational reporting and audit-style review.
