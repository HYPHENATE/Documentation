# EVT Event My Tickets

## API Name
`eVTEventMyTickets`

## Builder Name
`eVTEventMyTickets`

## Description

This exposed Experience Cloud component renders the attendee-facing `My Tickets` view.

It loads the current user's registrations, displays the relevant event details, and exposes the download path for valid paid tickets.

---

## Targets

- `lightningCommunity__Page`
- `lightningCommunity__Default`

---

## Behaviour Notes

| Area | Detail |
|------|------|
| Data source | Calls `EVTEventMyTicketsController.getMyTickets` during `connectedCallback`. |
| Empty state | Uses `hasTickets` to determine whether to show results or an empty-state experience. |
| Ticket access | Surfaces the e-ticket link only when the registration status allows it. |

---

## Related Components

- [EVT Event E-Ticket](/event-management/components/evt-event-e-ticket)
