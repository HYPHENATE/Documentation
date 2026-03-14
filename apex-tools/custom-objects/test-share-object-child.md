# Test Share Object Child

## API Name
`TestShareObjectChild__c`

## Description

The **Test Share Object Child** object is a package test-support object used to validate child-level sharing behaviour.
It provides a related child record model so that parent-child sharing configurations can be tested properly.

This object is included to support the package test framework and should be retained.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| BooleanField | BooleanField__c | Checkbox | True / False |
| DateField | DateField__c | Date |  |
| NumberField | NumberField__c | Number | 18,2 |
| TestShareObject | TestShareObject__c | Lookup | TestShareObject__c |

---

## Field Details

| Field | Purpose |
|------|------|
| BooleanField | Provides a simple boolean value for test scenarios. |
| DateField | Provides a date value for sharing and data-processing tests. |
| NumberField | Provides a numeric value for test scenarios. |
| TestShareObject | Links the child test record to its parent test sharing object. |

---

## Sharing Reasons

| Name | Label |
|--------------|--------------|
| TestRowCause__c | TestRowCause |
