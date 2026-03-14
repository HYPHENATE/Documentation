# Test Record Generator

## API Name
`Test_Record_Generator__mdt`

## Description

The **Test Record Generator** custom metadata type defines how test records should be created for a particular object.
It allows ApexTools to use configurable generator classes rather than requiring every test to build records manually.

This supports more consistent and reusable test setup across projects and packages.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Apex Class | Apex_Class__c | Text | 255 |
| Parameters | Parameters__c | Long Text Area | 131072 |
| Priority | Priority__c | Number | 18,0 |
| SObject | SObject__c | Text | 255 |
| Variant | Variant__c | Text | 255 |

---

## Field Details

| Field | Purpose |
|------|------|
| Apex Class | Identifies the Apex class used to generate the record. |
| Parameters | Stores JSON parameters used to initialise the generator. |
| Priority | Controls which generator should take precedence when multiple generators exist for the same object and variant. |
| SObject | Identifies the object this generator applies to. |
| Variant | Allows different generator definitions for different record scenarios. |

---

## List Views

| Name | Fields | Filter |
|--------------|--------------|--------------|
| All | MasterLabel, SObject__c, Variant__c, Priority__c, Apex_Class__c | Everything |
