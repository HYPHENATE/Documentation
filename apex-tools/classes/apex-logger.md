# ApexLogger

## API Name
`ApexLogger`

## Description

ApexLogger logs Apex_Log__c records based on custom metadata configuration

---

## Sharing Model
`without sharing`

## Tested By
`ApexLoggerTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Primary purpose | ApexLogger logs Apex_Log__c records based on custom metadata configuration |
| Logging support | Supports package logging, processing visibility, or operational troubleshooting. |
| Callable methods | Exposes 20 callable method(s) for package or implementation use. |

---

## Public/Internal Methods

| Method | Purpose |
|------|------|
| `setSaveResults` | Stores configuration or context used later in processing. |
| `setDeleteResults` | Stores configuration or context used later in processing. |
| `setRecordsProcessed` | Stores configuration or context used later in processing. |
| `setClassName` | Stores configuration or context used later in processing. |
| `setFlowInput` | Stores configuration or context used later in processing. |
| `processFlowInput` | Runs a main processing step for this class. |
| `saveFlowLogs` | Supports internal or reusable behaviour within the class. |
| `getLogs` | Returns or loads data used by the class. |
| `processSaveResults` | Runs a main processing step for this class. |
| `processDeleteResults` | Runs a main processing step for this class. |
| `buildApexErrorLog` | Constructs data, queries, records, or processing state. |
| `setConfig` | Stores configuration or context used later in processing. |
| `setConfigForFlow` | Stores configuration or context used later in processing. |
| `isValidLogger` | Checks whether a condition is true. |
| `buildLog` | Constructs data, queries, records, or processing state. |
| `buildLogForFlow` | Constructs data, queries, records, or processing state. |
| `saveLogs` | Supports internal or reusable behaviour within the class. |
| `buildErrorString` | Constructs data, queries, records, or processing state. |

---

## Important Notes

| Topic | Detail |
|------|------|
| Class Type | This Apex file is implemented as a `class`. |
| Package Role | `ApexLogger` is part of the ApexTools reusable framework and should be understood in the context of the wider package design. |
| Security Context | This class runs without sharing, so its use should be reviewed carefully in relation to data access and explicit access-mode design. |
| Documentation Depth | This page is a generated overview and may be expanded later with deeper implementation notes if needed. |

---

## Related Classes

- [ApexLoggerInvocable](./ApexLoggerInvocable.md)
- [ApexLoggerBatchDelete](./ApexLoggerBatchDelete.md)
