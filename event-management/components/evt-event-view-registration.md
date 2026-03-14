# EVT Event View Registration

## API Name
`eVTEventViewRegistration`

## Description

`eVTEventViewRegistration` is an internal registration modal component used by the event detail page.

It retrieves the flow API name configured on the selected event, passes the event and ticket details into that flow, and manages the registration modal lifecycle in the frontend.

This component is not directly exposed to Experience Builder. It is embedded inside the event detail view and used as the modal wrapper around the registration flow.

---

## Exposure

This component is intended to be embedded inside other LWCs rather than placed directly on a page.

---

## Public Properties

| Name | API Name | Data Type | Required | Description |
|------|------|------|------|------|
| Render Registration Modal | `renderRegistrationModal(...)` | Method | Yes | Opens the modal and seeds it with the selected event and ticket information. |

---

## Behaviour Notes

| Area | Detail |
|------|------|
| Flow selection | Calls `EVTViewRegistrationController.getEventRegistrationForm` to identify the correct flow. |
| Input variables | Passes `eventId`, `eventTicketId`, and `numberOfTickets` into the flow. |
| Guest handling | Supports both guest and logged-in journeys through the configured flow. |

---

## Related Components

- [EVT Event View](/event-management/components/evt-event-view)
