# Check

`Check__c` is the live checklist item created for a specific business record.

## Purpose

This object represents the operational checklist entry that a user actually completes.

## Key Responsibilities

- links a generated check back to its template
- stores completion state or selected answer
- stores optional user comments
- stores the parent record ID
- carries flow-launch data used after completion

## Important Fields

- `Check_Template__c`
- `Record_Id__c`
- `Checked__c`
- `CheckValue__c`
- `CheckComments__c`
- `Display_Type__c`
- `Launch_Flow_On_Complete__c`
- `Flow_API_Name__c`
- `Flow_Input_Variables__c`

## Notes

`Check__c` is reportable and history-enabled, which makes it the best place to analyse checklist completion over time.
