# HelpMessageController

## API Name
`HelpMessageController`

## Description

`HelpMessageController` is the main Apex controller for the **Help Messages** package.

It retrieves the messages relevant to the current record, determines whether the current user should see draft content, handles editor-only publish actions, and returns the JSON payload consumed by the `helpMessage` Lightning component.

---

## Sharing Model
`with sharing`

## Tested By
`HelpMessageController_Test`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Message retrieval | Queries `Help_Message__c` records for the current object type and relevant statuses. |
| Editor access detection | Determines whether the current user has the `Help_Message_Editor` permission set. |
| Filter-aware processing | Sends filter-driven messages to `HelpMessageHelper` for evaluation. |
| Status management | Allows editor actions to publish or unpublish messages. |
| JSON response generation | Returns the message payload and watched field list needed by the LWC. |

---

## AuraEnabled Methods

| Method | Returns | Purpose |
|------|------|------|
| `changeMessageStatus(String recordId, String status)` | `String` | Publishes or unpublishes a message and returns a JSON response message. |
| `canViewRecordActions()` | `String` | Returns whether the current user should see editor actions in the component. |
| `getHelpMessages(Id recordId)` | `String` | Returns the JSON payload containing matching help messages and watched fields. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `Help_Message__c` | Stores the configured messages returned to the UI. |
| `HelpMessageHelper` | Evaluates filter-driven messages. |
| `PermissionSetAssignment` | Used to determine whether the current user is an editor. |
| `helpMessage` | Consumes the JSON payload returned by this controller. |

---

## Typical Usage

This class is called by the `helpMessage` LWC whenever a record page needs to display or refresh contextual guidance.
