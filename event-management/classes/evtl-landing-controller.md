# EVTLandingController

## API Name
`EVTLandingController`

## Description

`EVTLandingController` powers the landing-page event listing experience. It queries the next available events, groups them into rows, and returns a JSON payload for the landing LWC.

The class is focused on shaping attendee-facing summary data rather than returning raw Salesforce records directly.

---

## Sharing Model
`without sharing`

## Tested By
`EVTLandingControllerTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Event retrieval | Queries the next set of events in `Registration` status. |
| Filtering | Optionally filters the landing page by event type. |
| Payload shaping | Groups results into rows and returns a JSON response for the frontend. |
| Summary enrichment | Adds favourite, low-price, seat-availability, and currency details. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `getLandingEvents(Integer numberOfRecords, String eventType)` | `String` | Returns the landing-page JSON payload for the requested event set. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `Event__c` | Supplies the event details, tickets, and favourites used in the landing-page cards. |
| `Event_Ticket__c` | Supplies pricing for the lowest-ticket calculation. |
| `Event_Favourite__c` | Tells the frontend whether the current user has favourited the event. |

---

## Typical Usage

This class is called by the exposed `eVTLandingComponent` when an Experience Cloud landing page loads.

---

## Related Classes

- [EVTViewController](/event-management/classes/evt-view-controller)
