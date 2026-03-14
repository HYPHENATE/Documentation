# EVT Event My Favourites

## API Name
`eVTEventMyFavourites`

## Builder Name
`eVTEventMyFavourites`

## Description

This exposed Experience Cloud component renders a logged-in user's saved favourite events.

It retrieves the favourites list from Apex and lets the user remove events from that list without leaving the page.

---

## Targets

- `lightningCommunity__Page`
- `lightningCommunity__Default`

---

## Behaviour Notes

| Area | Detail |
|------|------|
| Data source | Calls `EVTFavouriteManagement.getMyFavourites` when the component loads. |
| User interaction | Calls `EVTFavouriteManagement.removeEventFromFavourites` when a user removes a favourite. |
| Current behaviour note | The component currently sets `hasFavourites` using a zero-length check, so the runtime truthiness may deserve a later code review if the UI behaves unexpectedly. |

---

## Related Components

- [EVT Event View](/event-management/components/evt-event-view)
