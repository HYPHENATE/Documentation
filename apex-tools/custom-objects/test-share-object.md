# Test Share Object

## API Name
`TestShareObject__c`

## Description

The **Test Share Object** object is a package test-support object used to validate standard and custom sharing behaviour.
It exists to provide a predictable object that the sharing framework can work with during automated tests.

This object is not intended as an end-user business object and should not be removed.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| KeyReference | KeyReference__c | Text | 255 |

---

## Field Details

| Field | Purpose |
|------|------|
| KeyReference | Stores a simple reference value used in sharing-related test scenarios. |

---

## Sharing Reasons

| Name | Label |
|--------------|--------------|
| TestRowCause__c | TestRowCause |
