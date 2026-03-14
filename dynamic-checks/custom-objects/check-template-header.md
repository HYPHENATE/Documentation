# Check Template Header

`Check_Template_Header__c` is the top-level grouping object for Dynamic Checks configuration.

## Purpose

It defines the checklist category, the target object, and whether the related check templates apply to all records or only to records that match filters.

## Key Responsibilities

- groups related checklist templates together
- defines category label and description shown in the UI
- sets display order for the category
- identifies the target Salesforce object
- controls whether only the record owner should edit checks in that category
- determines whether the category always applies or is filter-driven

## Related Records

- parent to `Check_Template__c`
- parent to `Check_Filter__c`

## Typical Use

Create one header per meaningful checklist category on a target object, such as "Eligibility Checks" on a funding request or "Handover Checks" on a case record.
