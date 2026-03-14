# MetaSharingHandler

## API Name
`MetaSharingHandler`

## Description

Dynamic Apex Sharing handler class

---

## Sharing Model
`without sharing`

## Tested By
`No dedicated test class found`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Primary purpose | Dynamic Apex Sharing handler class |
| Sharing support | Supports dynamic sharing, share record creation, deletion, or related configuration handling. |
| Callable methods | Exposes 14 callable method(s) for package or implementation use. |

---

## Public/Internal Methods

| Method | Purpose |
|------|------|
| `setParentId` | Stores configuration or context used later in processing. |
| `setRecordIdsToShare` | Stores configuration or context used later in processing. |
| `isConfigRoleValid` | Checks whether a condition is true. |
| `buildRecordQueries` | Constructs data, queries, records, or processing state. |
| `processSharing` | Runs a main processing step for this class. |
| `insertShareRecords` | Performs insert behaviour or related write operations. |
| `getIsSuccess` | Returns or loads data used by the class. |
| `getErrorMessage` | Returns or loads data used by the class. |
| `runNow` | Executes a main task or batch/process action. |
| `runInBatch` | Executes a main task or batch/process action. |
| `buildQueries` | Constructs data, queries, records, or processing state. |
| `buildWhereClause` | Constructs data, queries, records, or processing state. |
| `buildCustomShareClass` | Constructs data, queries, records, or processing state. |

---

## Important Notes

| Topic | Detail |
|------|------|
| Class Type | This Apex file is implemented as a `class`. |
| Package Role | `MetaSharingHandler` is part of the ApexTools reusable framework and should be understood in the context of the wider package design. |
| Security Context | This class runs without sharing, so its use should be reviewed carefully in relation to data access and explicit access-mode design. |
| Documentation Depth | This page is a generated overview and may be expanded later with deeper implementation notes if needed. |

---

## Related Classes

- [MetaSharingDeleteHandler](./MetaSharingDeleteHandler.md)
- [ShareObjectCreate](./ShareObjectCreate.md)
- [ShareObjectDelete](./ShareObjectDelete.md)
