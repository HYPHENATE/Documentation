# EVT Landing Component

## API Name
`eVTLandingComponent`

## Builder Name
`eVTLandingComponent`

## Description

This exposed Experience Cloud component renders the event landing page by querying and displaying a list of events.

It is the main entry component for event discovery and can be configured to show a limited number of records or only a specific event type.

---

## Targets

- `lightningCommunity__Page`
- `lightningCommunity__Default`

---

## Public Properties

| Name | API Name | Data Type | Required | Description |
|------|------|------|------|------|
| Number Of Records | `numberOfRecords` | Number | No | Controls how many events should be requested for the landing page. |
| Type Of Event | `typeOfEvent` | String | No | Filters the landing-page results to a specific event type. |

---

## Behaviour Notes

| Area | Detail |
|------|------|
| Data source | Calls `EVTLandingController.getLandingEvents` on load. |
| Loading state | Shows a loading state until the event payload is returned. |
| Guest support | Works for guest and authenticated users, with favourite details varying by user context. |

---

## Related Components

- [EVT Event View](/event-management/components/evt-event-view)
