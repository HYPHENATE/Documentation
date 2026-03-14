# ApexLoggerBatchDelete

## API Name
`ApexLoggerBatchDelete`

## Description

Scheduled Batch Class to delete Apex_Log__c records based on Apex_Log__c.Expiry_Date__c

---

## Sharing Model
`without sharing`

## Tested By
`ApexLoggerBatchDeleteTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Primary purpose | Scheduled Batch Class to delete Apex_Log__c records based on Apex_Log__c.Expiry_Date__c |
| Logging support | Supports package logging, processing visibility, or operational troubleshooting. |
| Callable methods | Exposes 6 callable method(s) for package or implementation use. |

---

## Public/Internal Methods

| Method | Purpose |
|------|------|
| `setQuery` | Stores configuration or context used later in processing. |
| `start` | Supports internal or reusable behaviour within the class. |
| `execute` | Supports internal or reusable behaviour within the class. |
| `sendEmail` | Supports internal or reusable behaviour within the class. |
| `finish` | Supports internal or reusable behaviour within the class. |

---

## Important Notes

| Topic | Detail |
|------|------|
| Class Type | This Apex file is implemented as a `class`. |
| Package Role | `ApexLoggerBatchDelete` is part of the ApexTools reusable framework and should be understood in the context of the wider package design. |
| Security Context | This class runs without sharing, so its use should be reviewed carefully in relation to data access and explicit access-mode design. |
| Documentation Depth | This page is a generated overview and may be expanded later with deeper implementation notes if needed. |

---

## Related Classes

- [ApexLogger](./ApexLogger.md)
- [ApexLoggerInvocable](./ApexLoggerInvocable.md)
