# EVT Event E-Ticket

## API Name
`eVTEventETicket`

## Builder Name
`eVTEventETicket`

## Description

This exposed Experience Cloud component renders the e-ticket experience for a registration.

It reads the `registrationId` from the current page URL, asks Apex to validate the registration, and then displays the ticket payload returned by the controller.

---

## Targets

- `lightningCommunity__Page`
- `lightningCommunity__Default`

---

## Behaviour Notes

| Area | Detail |
|------|------|
| URL dependency | Reads `registrationId` from `CurrentPageReference`. |
| Validation | Displays an error state when the registration is unpaid or the event is no longer valid. |
| Ticket rendering | Displays one rendered entry per ticket and surfaces QR-code data from Apex. |

---

## Related Components

- [EVT Event My Tickets](/event-management/components/evt-event-my-tickets)
