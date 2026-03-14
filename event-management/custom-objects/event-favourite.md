# Event Favourite

## API Name
`Event_Favourite__c`

## Description

The **Event Favourite** object stores the events a logged-in user has marked as a favourite.

This supports the package's personalised attendee experience, where a user can save an event from the public-facing pages and later return to a `My Favourites` view.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Event | `Event__c` | Master Detail |  |

---

## Field Details

| Field | Purpose |
|------|------|
| Event | Links the favourite record to the saved event. The creating user effectively becomes the owner of that preference. |
