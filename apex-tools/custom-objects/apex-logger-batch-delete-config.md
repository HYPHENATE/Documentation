# Apex Logger Batch Delete Config

## API Name
`Apex_Logger_Batch_Delete_Config__mdt`

## Description

The **Apex Logger Batch Delete Config** custom metadata type controls how Apex Log cleanup is handled.
It is used to define whether notifications should be sent when batch deletion runs and, optionally, which Apex Logger configuration a cleanup rule relates to.

This helps administrators manage log retention in a more controlled way, especially where logs are regularly created and need to be cleaned up without losing oversight of the process.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Apex Logger Config | Apex_Logger_Config__c | Metadata Relationship | Apex_Logger_Config__mdt |
| Batch Delete Email Addresses | Batch_Delete_Email_Addresses__c | Text Area | Comma-separated values |
| Send Batch Delete Emails | Send_Batch_Delete_Emails__c | Checkbox | True / False |

---

## Field Details

| Field | Purpose |
|------|------|
| Apex Logger Config | Optionally links the cleanup rule to a specific Apex Logger configuration record. |
| Batch Delete Email Addresses | Stores the email addresses that should receive batch delete notifications. |
| Send Batch Delete Emails | Determines whether notification emails should be sent when cleanup runs. |

---

## Validation Rules

| Name | Purpose |
|------|------|
| If_Send_Emails_Have_Email_Addresses | Ensures email addresses are provided if batch delete emails are enabled. |
