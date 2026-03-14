# CheckLaunchFlow

## API Name
`CheckLaunchFlow`

## Description

`CheckLaunchFlow` is the post-completion automation class for **Dynamic Checks**.

It runs in the `after update` context for `Check__c` and launches a configured autolaunched flow when a check changes from incomplete to complete and the template configuration indicates that follow-on automation should run.

This gives the package an optional bridge between checklist completion and downstream automation without requiring every check to have hardcoded behaviour.

---

## Sharing Model
`without sharing`

## Tested By
`CheckLaunchFlowTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Trigger handling | Implements the `AfterUpdate` interface so the class can be invoked from the ApexTools metadata-driven trigger framework. |
| Completion detection | Compares old and new versions of `Check__c` to find checks that have just been completed. |
| Input parsing | Deserializes any JSON input variable payload stored on the check record. |
| Variable translation | Replaces package placeholders such as `$recordId` and `$parentId` with runtime values from the current check. |
| Flow launching | Creates and starts the configured autolaunched flow interview. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `handleAfterUpdate(List<Check__c> oldList, List<Check__c> newList)` | `void` | Identifies newly completed checks and sends them for flow processing. |

---

## Internal Methods

| Method | Purpose |
|------|------|
| `processChecks` | Iterates through checks that require automation, prepares input variables, and starts the configured flow. |
| `translateVariables` | Replaces placeholder values in the input variable map with the current check ID or parent record ID. |

---

## Runtime Notes

| Area | Detail |
|------|------|
| Trigger path | `CheckTrigger` delegates through `MetaTriggerManager`, and the relevant `Trigger_Handler__mdt` record points `AFTER_UPDATE` events to this class. |
| Completion condition | A flow only launches when `Checked__c` changes from false to true and `Launch_Flow_On_Complete__c` is enabled. |
| Placeholder support | `$recordId` is translated to the `Check__c` ID and `$parentId` is translated to the parent business record ID. |
| Error handling | Invalid JSON input throws `IncorrectParamsException`, while missing or invalid flow names throw `IncorrectFlowException`. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `AfterUpdate` | ApexTools trigger interface implemented by this class. |
| `Check__c` | Provides completion state, flow API name, and stored input variables. |
| `MetaTriggerManager` | Invokes the class through the metadata-driven trigger framework. |
| Salesforce Flow runtime | Creates and starts the autolaunched flow interview. |

---

## Typical Usage

This class runs automatically after a check is completed when the related template is configured to trigger downstream automation, such as a follow-up autolaunched flow.

---

## Related Classes

- [ChecksConstants](/dynamic-checks/classes/checks-constants)
- [Check](/dynamic-checks/classes/check-wrapper)
