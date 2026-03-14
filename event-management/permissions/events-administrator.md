# Events Administrator

## API Name
`Events_Administrator`

## Description

`Events Administrator` is the packaged permission set for staff who configure and manage the event data model in Salesforce.

It grants access to the Event Management app, the core custom objects, and the fields required to administer events, tickets, registrations, roles, favourites, and engagement tracking.

---

## Access Summary

| Area | Detail |
|------|------|
| App visibility | Grants visibility to the `Event_Management` app. |
| Custom settings | Grants access to `Event_Management_Settings__c` so teams can control visit-logging behaviour. |
| Core objects | Grants create, read, edit, and delete access across the event management objects. |
| Tab access | Makes the `Event__c` tab visible for administrators. |

---

## Object Permissions

| Object | Read | Create | Edit | Delete | Notes |
|------|------|------|------|------|------|
| `Event__c` | Yes | Yes | Yes | Yes | Core event setup and lifecycle management. |
| `Event_Ticket__c` | Yes | Yes | Yes | Yes | Ticket availability, pricing, and registration limits. |
| `Event_Registration__c` | Yes | Yes | Yes | Yes | Attendee registrations and payment status. |
| `Event_Role__c` | Yes | Yes | Yes | Yes | Speakers and other event roles. |
| `Event_Favourite__c` | Yes | Yes | Yes | Yes | Favourite tracking for logged-in users. |
| `Event_Views__c` | Yes | Yes | Yes | Yes | View logging and engagement tracking. |

---

## Field Access Highlights

| Field Area | Detail |
|------|------|
| Event content | Includes edit access for event descriptions, images, dates, times, location, type, and status. |
| Ticket setup | Includes edit access for availability windows, pricing, limits, and descriptions. |
| Registration details | Includes edit access for attendee contact details, ticket quantities, cost, and status. |
| Derived metrics | Summary fields such as total seats, registered counts, and page-visit totals are readable but not editable. |

---

## Operational Notes

| Topic | Detail |
|------|------|
| Intended users | Best suited to internal admins or event operations users rather than public-facing attendees. |
| Experience users | Public users typically interact through LWCs and flows instead of this permission set directly. |
| Settings management | View-tracking behaviour can be controlled through the packaged custom setting once access is assigned. |
