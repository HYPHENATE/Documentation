# Apex Classes

The package uses focused controllers and service classes for event landing pages, event views, registrations, favourites, tickets, and attendee-facing interactions.

Representative classes include:

- `EVTLandingController`
- `EVTViewController`
- `EVTViewRegistrationController`
- `EVTFavouriteManagement`
- `EVTEventMyTicketsController`
- `EVTEventETicketController`

Most of these classes are controller-style entry points for LWCs and Experience Cloud pages. They query the event data model, transform it into JSON responses, and keep the presentation layer thin.
