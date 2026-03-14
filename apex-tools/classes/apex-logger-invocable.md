# ApexLoggerInvocable

## API Name
`ApexLoggerInvocable`

## Description

Class with invocable method to be called from flows to allow flow error logging

---

## Sharing Model
`without sharing`

## Tested By
`ApexLoggerInvocableTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Primary purpose | Class with invocable method to be called from flows to allow flow error logging |
| Logging support | Supports package logging, processing visibility, or operational troubleshooting. |
| Callable methods | Exposes 1 callable method(s) for package or implementation use. |

---

## AuraEnabled / Invocable Methods

| Method | Returns | Purpose |
|------|------|------|
| `logFlowErrorToApexLog` | `List<ApexLoggerFlowLogOutput>` | Exposes package functionality to Flow or invocable automation. |

---

## Important Notes

| Topic | Detail |
|------|------|
| Class Type | This Apex file is implemented as a `class`. |
| Package Role | `ApexLoggerInvocable` is part of the ApexTools reusable framework and should be understood in the context of the wider package design. |
| Security Context | This class runs without sharing, so its use should be reviewed carefully in relation to data access and explicit access-mode design. |
| Documentation Depth | This page is a generated overview and may be expanded later with deeper implementation notes if needed. |

---

## Related Classes

- [ApexLogger](./ApexLogger.md)
- [ApexLoggerBatchDelete](./ApexLoggerBatchDelete.md)
