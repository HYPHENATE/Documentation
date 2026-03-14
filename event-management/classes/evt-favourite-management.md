# EVTFavouriteManagement

## API Name
`EVTFavouriteManagement`

## Description

`EVTFavouriteManagement` manages the favourite-event experience for logged-in users. It supports retrieving a user's favourites list, adding a new favourite, and removing an existing one.

The class returns JSON payloads so the favourites LWCs can stay presentation-focused.

---

## Sharing Model
`without sharing`

## Tested By
`EVTFavouriteManagementTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Favourite retrieval | Returns the current user's saved events. |
| Favourite creation | Adds an event to the current user's favourites. |
| Favourite removal | Deletes a favourite record for the current user and selected event. |
| Payload shaping | Returns success and favourites data in a JSON response. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `getMyFavourites()` | `String` | Returns the current user's favourites list. |
| `addEventToFavourites(String eventId)` | `String` | Creates a favourite for the selected event. |
| `removeEventFromFavourites(String eventId)` | `String` | Removes the current user's favourite for the selected event. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `Event_Favourite__c` | Stores the user's favourite-event preferences. |
| `Event__c` | Supplies the event name and URL information included in the response. |

---

## Typical Usage

This class is used by components such as `eVTEventMyFavourites` and by event-detail interactions that let a user save or unsave an event.

---

## Related Classes

- [EVTViewController](/event-management/classes/evt-view-controller)
