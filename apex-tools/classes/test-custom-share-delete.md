# TestCustomShareDelete

## API Name
`TestCustomShareDelete`

## Description

DO NOT DELETE - Test class used in testing framework to run custom share deletion code

---

## Sharing Model
`inherited sharing`

## Tested By
`No dedicated test class found`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Primary purpose | DO NOT DELETE - Test class used in testing framework to run custom share deletion code |
| Sharing support | Supports dynamic sharing, share record creation, deletion, or related configuration handling. |
| Test utility support | Supports reusable test setup, metadata-driven test data, or package testing helpers. |
| Callable methods | Exposes 9 callable method(s) for package or implementation use. |

---

## Public/Internal Methods

| Method | Purpose |
|------|------|
| `setSharingMeta` | Stores configuration or context used later in processing. |
| `setChildSharingMeta` | Stores configuration or context used later in processing. |
| `setUserIdsToProcess` | Stores configuration or context used later in processing. |
| `setRecordIdsToProcess` | Stores configuration or context used later in processing. |
| `setCustomValues` | Stores configuration or context used later in processing. |
| `buildQuery` | Constructs data, queries, records, or processing state. |
| `getQuery` | Returns or loads data used by the class. |
| `runQuery` | Executes a main task or batch/process action. |
| `deleteShareRecords` | Deletes or removes records or framework state. |

---

## Important Notes

| Topic | Detail |
|------|------|
| Class Type | This Apex file is implemented as a `class`. |
| Package Role | `TestCustomShareDelete` is part of the ApexTools reusable framework and should be understood in the context of the wider package design. |
| Security Context | This class declares an explicit sharing model and should be used consistently with the package security standards. |
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
