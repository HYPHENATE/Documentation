# TestCustomShareCreate

## API Name
`TestCustomShareCreate`

## Description

DO NOT DELETE - Test class used in testing framework to run custom share creation code

---

## Sharing Model
`without sharing`

## Tested By
`No dedicated test class found`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Primary purpose | DO NOT DELETE - Test class used in testing framework to run custom share creation code |
| Sharing support | Supports dynamic sharing, share record creation, deletion, or related configuration handling. |
| Test utility support | Supports reusable test setup, metadata-driven test data, or package testing helpers. |
| Callable methods | Exposes 12 callable method(s) for package or implementation use. |

---

## Public/Internal Methods

| Method | Purpose |
|------|------|
| `setSharingMeta` | Stores configuration or context used later in processing. |
| `setChildSharingMeta` | Stores configuration or context used later in processing. |
| `setParentIdField` | Stores configuration or context used later in processing. |
| `setRecordsToShare` | Stores configuration or context used later in processing. |
| `setRecordIdsToShare` | Stores configuration or context used later in processing. |
| `setUserIdsToShareTo` | Stores configuration or context used later in processing. |
| `setUserData` | Stores configuration or context used later in processing. |
| `setTargetObjectType` | Stores configuration or context used later in processing. |
| `setCustomValues` | Stores configuration or context used later in processing. |
| `setShareComments` | Stores configuration or context used later in processing. |
| `createShareRecords` | Creates records, outputs, or framework structures. |
| `getShareRecords` | Returns or loads data used by the class. |

---

## Important Notes

| Topic | Detail |
|------|------|
| Class Type | This Apex file is implemented as a `class`. |
| Package Role | `TestCustomShareCreate` is part of the ApexTools reusable framework and should be understood in the context of the wider package design. |
| Security Context | This class runs without sharing, so its use should be reviewed carefully in relation to data access and explicit access-mode design. |
| Documentation Depth | This page is a generated overview and may be expanded later with deeper implementation notes if needed. |

---

## Related Classes

- [MetaSharingHandler](./MetaSharingHandler.md)
- [MetaSharingDeleteHandler](./MetaSharingDeleteHandler.md)
- [ShareObjectCreate](./ShareObjectCreate.md)
- [ShareObjectDelete](./ShareObjectDelete.md)
- [TestRecordSource](./TestRecordSource.md)
- [TestRecordGenerator](./TestRecordGenerator.md)
- [TestFieldFunctions](./TestFieldFunctions.md)
