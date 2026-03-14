# Event Ticket

## API Name
`Event_Ticket__c`

## Description

The **Event Ticket** object stores the ticket types available for an event, including pricing, availability windows, and registration limits.

These records are what the attendee-facing event page uses to show ticket options and what the registration flow uses to validate whether a user can still register.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Available From Date/Time | `Available_From_Date_Time__c` | DateTime |  |
| Closing Date / Time | `Closing_Date_Time__c` | DateTime |  |
| Cost | `Cost__c` | Currency | 18,2 |
| Description | `Description__c` | HTML | 32768 |
| Event | `Event__c` | Master Detail |  |
| Max Per Registration | `Max_Per_Registration__c` | Number | 18,0 |
| Number Available | `Number_Available__c` | Number | 18,0 |
| Registered | `Registered__c` | Summary |  |

---

## Field Details

| Field | Purpose |
|------|------|
| Available From Date/Time | Defines when the ticket becomes available to reserve. |
| Closing Date / Time | Defines when registration for the ticket closes. |
| Cost | Stores the per-ticket price used in the registration and e-ticket experiences. |
| Description | Describes the ticket type to attendees. |
| Event | Links the ticket to its parent event. |
| Max Per Registration | Limits how many tickets a single registration can request. |
| Number Available | Sets the ticket inventory available for the event. |
| Registered | Rolls up how many seats have already been taken. |
