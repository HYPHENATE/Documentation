# MetaSharingDeleteHandler

## API Name
`MetaSharingDeleteHandler`

## Description

Dynamic Apex Sharing delete class

---

## Sharing Model
`without sharing`

## Tested By
`No dedicated test class found`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Primary purpose | Dynamic Apex Sharing delete class |
| Sharing support | Supports dynamic sharing, share record creation, deletion, or related configuration handling. |
| Callable methods | Exposes 12 callable method(s) for package or implementation use. |

---

## Public/Internal Methods

| Method | Purpose |
|------|------|
| `setRecordIdsToProcess` | Stores configuration or context used later in processing. |
| `isConfigRoleValid` | Checks whether a condition is true. |
| `buildRecordQueries` | Constructs data, queries, records, or processing state. |
| `processShareQueries` | Runs a main processing step for this class. |
| `deleteShares` | Deletes or removes records or framework state. |
| `getIsSuccess` | Returns or loads data used by the class. |
| `getErrorMessage` | Returns or loads data used by the class. |
| `buildQueries` | Constructs data, queries, records, or processing state. |
| `runNow` | Executes a main task or batch/process action. |
| `runInBatch` | Executes a main task or batch/process action. |
| `runInBatchStandard` | Executes a main task or batch/process action. |
| `runInBatchCustom` | Executes a main task or batch/process action. |

---

## Important Notes

| Topic | Detail |
|------|------|
| Class Type | This Apex file is implemented as a `class`. |
| Package Role | `MetaSharingDeleteHandler` is part of the ApexTools reusable framework and should be understood in the context of the wider package design. |
| Security Context | This class runs without sharing, so its use should be reviewed carefully in relation to data access and explicit access-mode design. |
| Documentation Depth | This page is a generated overview and may be expanded later with deeper implementation notes if needed. |

---

## Related Classes

- [MetaSharingHandler](./MetaSharingHandler.md)
- [ShareObjectCreate](./ShareObjectCreate.md)
- [ShareObjectDelete](./ShareObjectDelete.md)
