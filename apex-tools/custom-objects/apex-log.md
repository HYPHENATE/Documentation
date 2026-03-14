# Apex Log

## API Name
`Apex_Log__c`

## Description

The **Apex Log** object stores structured log records created by ApexTools.
It is used to record processing outcomes, errors, Flow faults, and operational follow-up information so that technical issues can be reviewed inside Salesforce rather than being lost in debug logs or email notifications.

This object is especially useful for support, administration, and ongoing maintenance. It gives teams a consistent place to review what happened, which record was affected, which class or Flow was involved, and whether the issue has been resolved.

In practice, this can support use cases such as:

- recording failed batch updates
- logging Flow fault details
- tracking issues linked to specific records
- managing investigation and resolution activity

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Account | Account__c | Lookup | Account |
| Class Name | Class_Name__c | Text | 255 |
| Code Execution Time | Code_Execution_Time__c | DateTime |  |
| Errors | Errors__c | Long Text Area | 32768 |
| Expiry Date | Expiry_Date__c | Date |  |
| Fault Element | Fault_Element__c | Text | 255 |
| Flow API Name | Flow_API_Name__c | Text | 255 |
| Record Link | Record_Link__c | Text | Formula / derived value |
| Resolution Notes | Resolution_Notes__c | Html | 32768 |
| Retain as Knowledge Article | Retain_as_Knowledge_Article__c | Checkbox | True / False |
| Running User | Running_User__c | Lookup | User |
| SObject Id | SObject_Id__c | Text | 18 |
| Status | Status__c | Picklist | Success / Error |
| Working Status | Working_Status__c | Picklist | New / In Progress / Resolved / No Further Action |

---

## Field Details

| Field | Purpose |
|------|------|
| Account | Optional lookup used in test support and can also be used for normal logging scenarios where an Account relationship is helpful. |
| Class Name | Stores the Apex class or calling context associated with the log entry. |
| Code Execution Time | Records when the logged event happened. |
| Errors | Stores the main error message or processing detail. |
| Expiry Date | Used to control how long the log record should be retained before cleanup. |
| Fault Element | Stores the specific Flow element or node that caused a fault. |
| Flow API Name | Identifies the Flow related to the error or log event. |
| Record Link | Provides a link-style value to help users navigate to the related record. |
| Resolution Notes | Allows admins or support users to record investigation notes and fix details. |
| Retain as Knowledge Article | Prevents the record from being deleted by normal cleanup processes so it can be kept as a support reference. |
| Running User | Captures the user context in which the issue occurred. |
| SObject Id | Stores the related Salesforce record ID. |
| Status | Indicates whether the log entry represents success or error behaviour. |
| Working Status | Tracks investigation progress and support handling. |
