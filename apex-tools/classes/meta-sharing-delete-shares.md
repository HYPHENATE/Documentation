# MetaSharingDeleteShares

## API Name
`MetaSharingDeleteShares`

## Description

Class to hold invocable method for deleting shares

---

## Sharing Model
`without sharing`

## Tested By
`MetaSharingDeleteSharesTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Primary purpose | Class to hold invocable method for deleting shares |
| Sharing support | Supports dynamic sharing, share record creation, deletion, or related configuration handling. |
| Callable methods | Exposes 2 callable method(s) for package or implementation use. |

---

## AuraEnabled / Invocable Methods

| Method | Returns | Purpose |
|------|------|------|
| `runMetaSharingDeleteHandler` | `List<MetaSharingDeleteOutput>` | Exposes package functionality to Flow or invocable automation. |

---

## Public/Internal Methods

| Method | Purpose |
|------|------|
| `isConfigValid` | Checks whether a condition is true. |

---

## Important Notes

| Topic | Detail |
|------|------|
| Class Type | This Apex file is implemented as a `class`. |
| Package Role | `MetaSharingDeleteShares` is part of the ApexTools reusable framework and should be understood in the context of the wider package design. |
| Security Context | This class runs without sharing, so its use should be reviewed carefully in relation to data access and explicit access-mode design. |
| Documentation Depth | This page is a generated overview and may be expanded later with deeper implementation notes if needed. |

---

## Related Classes

- [MetaSharingHandler](./MetaSharingHandler.md)
- [MetaSharingDeleteHandler](./MetaSharingDeleteHandler.md)
- [ShareObjectCreate](./ShareObjectCreate.md)
- [ShareObjectDelete](./ShareObjectDelete.md)
