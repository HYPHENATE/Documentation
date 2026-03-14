# EVT Event View

## API Name
`eVTEventView`

## Builder Name
`eVTEventView`

## Description

This exposed Experience Cloud component renders the main event detail page.

It retrieves the event payload from Apex, logs event visits, renders ticket and speaker data, and opens the registration modal when an attendee chooses a ticket.

---

## Targets

- `lightningCommunity__Page`
- `lightningCommunity__Default`

---

## Public Properties

| Name | API Name | Data Type | Required | Description |
|------|------|------|------|------|
| Record Id | `recordId` | String | Yes | Identifies the `Event__c` record to display. |

---

## Behaviour Notes

| Area | Detail |
|------|------|
| Event retrieval | Calls `EVTViewController.getEvent` during `connectedCallback`. |
| Visit logging | Uses local storage and `EVTViewController.logEventVisit` to distinguish repeat visits. |
| Registration | Delegates checkout and flow rendering to the internal `eVTEventViewRegistration` component. |

---

## Related Components

- [EVT Event View Registration](/event-management/components/evt-event-view-registration)
- [EVT Landing Component](/event-management/components/evt-landing-component)
