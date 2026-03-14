# ShareObjectDelete

## API Name
`ShareObjectDelete`

## Description

Generic class to delete '__share' records in a non-shared context

---

## Sharing Model
`without sharing`

## Tested By
`ShareObjectDeleteTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Primary purpose | Generic class to delete '__share' records in a non-shared context |
| Sharing support | Supports dynamic sharing, share record creation, deletion, or related configuration handling. |
| Callable methods | Exposes 4 callable method(s) for package or implementation use. |

---

## Public/Internal Methods

| Method | Purpose |
|------|------|
| `setTargetObjectType` | Stores configuration or context used later in processing. |
| `setRowCause` | Stores configuration or context used later in processing. |
| `deleteShare` | Deletes or removes records or framework state. |
| `getShareRecords` | Returns or loads data used by the class. |

---

## Important Notes

| Topic | Detail |
|------|------|
| Class Type | This Apex file is implemented as a `class`. |
| Package Role | `ShareObjectDelete` is part of the ApexTools reusable framework and should be understood in the context of the wider package design. |
| Security Context | This class runs without sharing, so its use should be reviewed carefully in relation to data access and explicit access-mode design. |
| Documentation Depth | This page is a generated overview and may be expanded later with deeper implementation notes if needed. |

---

## Related Classes

- [MetaSharingHandler](./MetaSharingHandler.md)
- [MetaSharingDeleteHandler](./MetaSharingDeleteHandler.md)
- [ShareObjectCreate](./ShareObjectCreate.md)
