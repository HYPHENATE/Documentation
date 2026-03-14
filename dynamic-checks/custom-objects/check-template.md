# Check Template

## API Name
`Check_Template__c`

## Description

The **Check Template** object stores the reusable definition of an individual checklist item.

It describes what should appear to users when a live `Check__c` record is generated for a qualifying business record, including the title, help text, response style, optional comments, and any flow-launch settings that should apply after completion.

This is where admins define the checklist items they want the package to create repeatedly whenever a record qualifies for a given category.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Check Template ID | Name | Auto Number | `CTID-{000000000}` |
| Allow Custom Comments on Check | Allow_Custom_Comments_on_Check__c | Checkbox | True / False |
| Check Template Header | Check_Template_Header__c | Master-Detail | Check_Template_Header__c |
| Custom Display Type Options | Custom_Display_Type_Options__c | Long Text Area | 32768 |
| Custom Display Type Valid Option | Custom_Display_Type_Valid_Option__c | Long Text Area | 32768 |
| Display Type | Display_Type__c | Picklist | Package-defined display modes including custom-answer handling |
| Flow API Name | Flow_API_Name__c | Text | 255 |
| Flow Input Variables | Flow_Input_Variables__c | Long Text Area | 32768 |
| Help Text | Help_Text__c | Long Text Area | 32768 |
| Inactive | Inactive__c | Checkbox | True / False |
| Launch Flow on Complete | Launch_Flow_On_Complete__c | Checkbox | True / False |
| Order | Order__c | Number | 18,0 |
| Title | Title__c | Text | 255 |

---

## Field Details

| Field | Purpose |
|------|------|
| Check Template ID | System-generated identifier for the template record. |
| Allow Custom Comments on Check | Determines whether users may store comments against the generated check. |
| Check Template Header | Connects the template to its parent checklist category. |
| Custom Display Type Options | Stores the answer options shown for custom response types. |
| Custom Display Type Valid Option | Stores the values that should count as a completed check for custom response types. |
| Display Type | Determines whether the check behaves like a simple complete/incomplete item or uses a custom answer pattern. |
| Flow API Name | Stores the autolaunched flow API name to invoke after completion when enabled. |
| Flow Input Variables | Stores a JSON payload of input variables that should be passed into the flow. |
| Help Text | Provides additional guidance shown to users alongside the check. |
| Inactive | Prevents new live checks being created from this template when enabled. |
| Launch Flow on Complete | Indicates that a completed check should start a configured flow. |
| Order | Controls the order of checks within the category. |
| Title | The checklist item title shown to end users. |

---

## Usage Notes

- Templates sit under one `Check_Template_Header__c` record and define the individual checks in that category.
- `ChecksHelper` creates live `Check__c` rows from active templates when a record qualifies for the category.
- Custom display type settings allow a check to behave like a guided answer selection rather than a simple checkbox.
- Flow launch fields are used together with `CheckLaunchFlow` when a completed check should start downstream automation.
