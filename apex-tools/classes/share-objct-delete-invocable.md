# ShareObjectDeleteInvocable

## API Name
`ShareObjectDeleteInvocable`

## Description

Invocable method to call ShareObjectDelete and delete '__share' records

---

## Sharing Model
`without sharing`

## Tested By
`No dedicated test class found`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Primary purpose | Invocable method to call ShareObjectDelete and delete '__share' records |
| Sharing support | Supports dynamic sharing, share record creation, deletion, or related configuration handling. |
| Callable methods | Exposes 1 callable method(s) for package or implementation use. |

---

## AuraEnabled / Invocable Methods

| Method | Returns | Purpose |
|------|------|------|
| `shareObjectDelete` | `void` | Exposes package functionality to Flow or invocable automation. |

---

## Important Notes

| Topic | Detail |
|------|------|
| Class Type | This Apex file is implemented as a `class`. |
| Package Role | `ShareObjectDeleteInvocable` is part of the ApexTools reusable framework and should be understood in the context of the wider package design. |
| Security Context | This class runs without sharing, so its use should be reviewed carefully in relation to data access and explicit access-mode design. |
| Documentation Depth | This page is a generated overview and may be expanded later with deeper implementation notes if needed. |

---

## Related Classes

- [MetaSharingHandler](./MetaSharingHandler.md)
- [MetaSharingDeleteHandler](./MetaSharingDeleteHandler.md)
- [ShareObjectCreate](./ShareObjectCreate.md)
- [ShareObjectDelete](./ShareObjectDelete.md)
