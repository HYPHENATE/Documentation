# EVTViewRegistrationController

## API Name
`EVTViewRegistrationController`

## Description

`EVTViewRegistrationController` is a lightweight controller used by the registration modal component. Its job is to return the flow API name configured on the selected event.

That keeps the registration component flexible because different events can point to different flows without changing the component code.

---

## Sharing Model
`without sharing`

## Tested By
`EVTViewRegistrationControllerTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Flow lookup | Reads the configured flow API name from the event record. |
| Registration orchestration | Supports the registration modal in choosing which flow to render. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `getEventRegistrationForm(String eventId)` | `String` | Returns the registration flow API name stored on the selected event. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `Event__c` | Stores the `Registration_Form_API_Name__c` value used by the registration modal. |

---

## Typical Usage

This class is called by `eVTEventViewRegistration` immediately after the registration modal opens.

---

## Related Classes

- [EVTViewController](/event-management/classes/evt-view-controller)
