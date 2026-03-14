# Configuration

## Initial Setup

Assign the admin permission set, add the `dynamicChecksContainer` component to the target Lightning record page, and identify the first object and process you want to support.

## Recommended Configuration

- Create `Check_Template_Header__c` records for the target object and checklist categories.
- Add `Check_Template__c` records for each individual check you want users to complete.
- Add `Check_Filter__c` rows when a checklist should only apply to records meeting certain criteria.
- Assign the `Dynamic_Checks` permission set to end users.

## Optional Configuration

- Enable `expandAllSections` on the component if users benefit from seeing every category open on load.
- Enable `firstTimeCreateOnly` if you want to prevent later checklist template additions from creating new checks on records that were already initialised.
- Configure `Launch_Flow_On_Complete__c`, `Flow_API_Name__c`, and `Flow_Input_Variables__c` on templates where completing a check should trigger follow-on automation.
