# Send Email Setting

## API Name
`SendEmailSetting__c`

## Description

The **Send Email Setting** object stores configuration used by the ApexTools email utilities.
It currently supports control of whether email send failures should create Apex Log records.

This gives administrators a simple way to decide whether email issues should be captured in the package logging framework.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Log Errors | Log_Errors__c | Checkbox | True / False |

---

## Field Details

| Field | Purpose |
|------|------|
| Log Errors | Controls whether failed email operations should create Apex Log records. |
