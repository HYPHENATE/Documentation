# Check Template

`Check_Template__c` stores the reusable definition of an individual checklist item.

## Purpose

It describes what should appear to users when a live check is generated for a record.

## Key Responsibilities

- stores the checklist item title
- controls display order within the category
- determines the display type
- holds help text and optional comment settings
- optionally stores custom answer options and valid values
- optionally stores flow-launch configuration

## Important Fields

- `Title__c`
- `Display_Type__c`
- `Help_Text__c`
- `Allow_Custom_Comments_on_Check__c`
- `Custom_Display_Type_Options__c`
- `Custom_Display_Type_Valid_Option__c`
- `Launch_Flow_On_Complete__c`
- `Flow_API_Name__c`
- `Flow_Input_Variables__c`

## Typical Use

Use templates to model the repeatable checks you want to see each time a qualifying record is opened in the checklist experience.
