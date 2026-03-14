# MetaTriggerManager

## API Name
`MetaTriggerManager`

## Description

Use custom metadata to specify trigger handler classes to run, making the actual triggers into one-line pieces of code. Example: trigger ContactTrigger on Contact (before insert, before update, before delete, after insert, after update, after delete, after undelete) { (new MetaTriggerManager(Contact.sObjectType)).handle(); } Write your trigger handler by implementing the interfaces such as AfterInsert, then link it to the trigger by creating a Trigger_Handler__mdt custom metadata record for each event when your handler needs to run.

---

## Sharing Model
`with sharing`

## Tested By
`MetaTriggerManagerTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Primary purpose | Use custom metadata to specify trigger handler classes to run, making the actual triggers into one-line pieces of code. Example: trigger ContactTrigger on Contact (before insert, before update, before delete, after insert, after update, after delete, after undelete) { (new MetaTriggerManager(Contact.sObjectType)).handle(); } Write your trigger handler by implementing the interfaces such as AfterInsert, then link it to the trigger by creating a Trigger_Handler__mdt custom metadata record for each event when your handler needs to run. |
| Trigger framework support | Supports trigger routing, trigger contracts, or trigger execution control. |
| Callable methods | Exposes 4 callable method(s) for package or implementation use. |

---

## Public/Internal Methods

| Method | Purpose |
|------|------|
| `handle` | Handles a framework event or delegated execution path. |
| `handleInstance` | Handles a framework event or delegated execution path. |
| `isTriggersDeactivated` | Checks whether a condition is true. |

---

## Important Notes

| Topic | Detail |
|------|------|
| Class Type | This Apex file is implemented as a `class`. |
| Package Role | `MetaTriggerManager` is part of the ApexTools reusable framework and should be understood in the context of the wider package design. |
| Security Context | This class declares an explicit sharing model and should be used consistently with the package security standards. |
| Documentation Depth | This page is a generated overview and may be expanded later with deeper implementation notes if needed. |

---

## Related Classes

- [BeforeInsert](./BeforeInsert.md)
- [BeforeUpdate](./BeforeUpdate.md)
- [BeforeDelete](./BeforeDelete.md)
- [AfterInsert](./AfterInsert.md)
- [AfterUpdate](./AfterUpdate.md)
- [AfterDelete](./AfterDelete.md)
- [AfterUndelete](./AfterUndelete.md)
