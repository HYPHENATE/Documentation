# SendEmail

## API Name
`SendEmail`

## Description

Class with invocable method to send Emails from Flows

---

## Sharing Model
`without sharing`

## Tested By
`SendEmailTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Primary purpose | Class with invocable method to send Emails from Flows |
| Email handling | Supports email delivery, configuration, or email-related platform actions. |
| Callable methods | Exposes 9 callable method(s) for package or implementation use. |

---

## AuraEnabled / Invocable Methods

| Method | Returns | Purpose |
|------|------|------|
| `sendEmail` | `List<ProcessEmailResult>` | Exposes package functionality to Flow or invocable automation. |

---

## Public/Internal Methods

| Method | Purpose |
|------|------|
| `generateEmailKey` | Supports internal or reusable behaviour within the class. |
| `generateEmailMessage` | Supports internal or reusable behaviour within the class. |
| `buildEmailMessage` | Constructs data, queries, records, or processing state. |
| `processSendErrors` | Runs a main processing step for this class. |
| `isLogErrors` | Checks whether a condition is true. |
| `processResults` | Runs a main processing step for this class. |
| `getTemplateSets` | Returns or loads data used by the class. |
| `getTemplates` | Returns or loads data used by the class. |

---

## Important Notes

| Topic | Detail |
|------|------|
| Class Type | This Apex file is implemented as a `class`. |
| Package Role | `SendEmail` is part of the ApexTools reusable framework and should be understood in the context of the wider package design. |
| Security Context | This class runs without sharing, so its use should be reviewed carefully in relation to data access and explicit access-mode design. |
| Documentation Depth | This page is a generated overview and may be expanded later with deeper implementation notes if needed. |

---

## Related Classes

- [SendEmailV2](./SendEmailV2.md)
- [EmailResultsMetadataDeployCallback](./EmailResultsMetadataDeployCallback.md)
