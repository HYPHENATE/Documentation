# EVTEventMyTicketsController

## API Name
`EVTEventMyTicketsController`

## Description

`EVTEventMyTicketsController` retrieves the current user's event registrations based on their Salesforce user email address and returns a JSON payload used by the `My Tickets` experience.

The class also shapes attendee-friendly data such as event links, ticket links, status text, and whether the download action should be shown.

---

## Sharing Model
`with sharing`

## Tested By
`EVTEventMyTicketsControllerTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Ticket retrieval | Queries registrations for the current user's email address. |
| Experience shaping | Adds event URLs, e-ticket URLs, event timing, and display flags to the JSON payload. |
| Payment-state handling | Controls whether the download link should be shown based on registration status. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `getMyTickets()` | `String` | Returns the current user's ticket registrations for the attendee-facing `My Tickets` page. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `Event_Registration__c` | Supplies the user's registrations and registration status. |
| `Event__c` | Supplies the event name, status, type, and timing. |

---

## Typical Usage

This class is called by `eVTEventMyTickets` when the attendee-facing tickets page loads.

---

## Related Classes

- [EVTEventETicketController](/event-management/classes/evt-event-e-ticket-controller)
