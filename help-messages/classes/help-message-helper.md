# HelpMessageHelper

## API Name
`HelpMessageHelper`

## Description

`HelpMessageHelper` contains the filtering logic that decides whether a configured help message should appear for the current record.

It dynamically collects the fields needed for evaluation, queries the current record, resolves relationship paths where needed, and applies the configured operator logic to each filter row.

---

## Sharing Model
`with sharing`

## Tested By
`HelpMessageController_Test`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Dynamic record query | Builds a record query using only the fields referenced by the configured filters. |
| Filter evaluation | Applies `AND` or `OR` logic across child `Help_Message_Filter__c` rows. |
| Field resolution | Supports direct and relationship field references. |
| Type detection | Uses field describe metadata to apply comparison logic correctly. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `getSObjectFieldTypeRelationship(SObjectType objectType, List<String> sOQLFields)` | `DisplayType` | Resolves field types across relationship paths. |
| `getHelpFilterMessages(List<Help_Message__c> withFilters, String sObjectType, String recordId)` | `List<Help_Message__c>` | Returns the subset of messages whose filters match the current record. |
| `getSObjectField(SObject record, String sOQLField)` | `Object` | Dynamically retrieves a field value from the current record. |
| `getSObjectFieldType(SObjectType objectType, String sOQLField)` | `DisplayType` | Resolves the display type of a configured field reference. |
| `fieldFilterMatch(SObject record, String filterLogic, List<Help_Message_Filter__c> filters)` | `Boolean` | Applies the configured filter logic across the filter rows. |
| `handleFilterChecks(Help_Message_Filter__c filter, SObject record, DisplayType fieldType)` | `Boolean` | Evaluates one filter row against the current record value. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `Help_Message_Filter__c` | Stores the field, operator, and value conditions to evaluate. |
| `HelpMessageConstants` | Provides the shared operator and filter logic constants. |
| Schema describe APIs | Resolve field types and relationship traversal dynamically. |

---

## Typical Usage

This helper is called by `HelpMessageController` whenever one or more candidate messages are configured with filters rather than applying to all records.
