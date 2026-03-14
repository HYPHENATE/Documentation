# Test Custom Share

## API Name
`TestCustomShare__c`

## Description

The **Test Custom Share** object is a package test-support object used to validate sharing behaviour.
It is not intended as a business object for production processes. Instead, it provides a controlled custom sharing model that helps the package's sharing framework be tested reliably.

This object should be retained because it supports the package's automated tests.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Comments | Comments__c | Text | 255 |
| IsParticipantActive | IsParticipantActive__c | Checkbox | True / False |
| ParticipantId | ParticipantId__c | Lookup | User |
| TestShareObject | TestShareObject__c | Lookup | TestShareObject__c |
| TestShareObjectChild | TestShareObjectChild__c | Lookup | TestShareObjectChild__c |

---

## Field Details

| Field | Purpose |
|------|------|
| Comments | Stores optional notes used in test scenarios. |
| IsParticipantActive | Indicates whether the related participant should be treated as active in test logic. |
| ParticipantId | Links the test share record to a User record. |
| TestShareObject | Links the record to the parent test sharing object. |
| TestShareObjectChild | Links the record to the child test sharing object. |
