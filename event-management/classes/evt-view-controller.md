# EVTViewController

## API Name
`EVTViewController`

## Description

`EVTViewController` is the main controller behind the event detail page. It retrieves the selected event, enriches it with speaker, ticket, and logging preferences, and returns a JSON payload that the frontend renders.

It also handles event-view logging so the package can track engagement against the event record.

---

## Sharing Model
`without sharing`

## Tested By
`EVTViewControllerTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Event detail retrieval | Queries the event, tickets, confirmed roles, and favourites for the current user. |
| JSON response shaping | Builds the payload consumed by the event detail LWC. |
| View tracking | Logs visits into `Event_Views__c` based on package settings. |
| Experience support | Adds location text, time ranges, ticket availability, and speaker details. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `logEventVisit(String recordId, Boolean isRepeat)` | `void` | Logs an event view when package settings allow it. |
| `getEvent(String eventId)` | `String` | Returns the event detail JSON payload for the selected event. |

---

## Runtime Notes

| Area | Detail |
|------|------|
| Settings dependency | Uses `Event_Management_Settings__c.getOrgDefaults()` to decide how visits should be logged. |
| Ticket logic | Calculates whether tickets are available, sold out, or coming soon from the underlying ticket dates and counts. |
| Frontend payload | Returns a JSON object rather than a typed Apex DTO so the LWC can render directly from parsed data. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `Event__c` | Supplies the main event data. |
| `Event_Role__c` | Supplies confirmed speakers or other roles. |
| `Event_Ticket__c` | Supplies ticket availability and pricing. |
| `Event_Favourite__c` | Indicates whether the current user has favourited the event. |
| `Event_Views__c` | Stores engagement tracking records. |

---

## Typical Usage

This class is called by `eVTEventView` when a user opens an event detail page in the experience site.

---

## Related Classes

- [EVTViewRegistrationController](/event-management/classes/evt-view-registration-controller)
- [EVTFavouriteManagement](/event-management/classes/evt-favourite-management)
