# EVTEventETicketController

## API Name
`EVTEventETicketController`

## Description

`EVTEventETicketController` validates an event registration and generates the payload used to render downloadable e-tickets.

It checks whether the registration exists, whether the registration is paid, and whether the event is still valid for attendance before returning QR-code ready ticket data.

---

## Sharing Model
`without sharing`

## Tested By
`EVTEventETicketControllerTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Registration lookup | Retrieves the registration and related event and ticket details. |
| Validation | Confirms that the registration is paid and the event is not complete or cancelled. |
| E-ticket payload generation | Returns ticket details, QR-code URLs, and per-ticket references. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `getETicketDetails(String registrationId)` | `String` | Returns the validation state and ticket data for the e-ticket page. |

---

## Runtime Notes

| Area | Detail |
|------|------|
| QR code generation | Uses the external QR server URL to generate a code for the registration link. |
| Multi-ticket handling | Returns one ticket entry per reserved seat rather than a single aggregate line. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `Event_Registration__c` | Supplies the registration, event, and ticket details. |
| Custom labels | Supply the package's validation and status messages. |

---

## Typical Usage

This class is called by `eVTEventETicket` when the page receives a `registrationId` parameter.

---

## Related Classes

- [EVTEventMyTicketsController](/event-management/classes/evt-event-my-tickets-controller)
