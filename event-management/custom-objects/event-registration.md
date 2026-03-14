# Event Registration

## API Name
`Event_Registration__c`

## Description

The **Event Registration** object stores attendee signups for specific tickets and events. It captures the registrant details, quantity of tickets, cost, newsletter consent, and payment status.

This object is one of the main transactional records in the package and is created by the registration flow that runs behind the attendee experience.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Cost | `Cost__c` | Currency | 18,2 |
| Email | `Email__c` | Email |  |
| Event Ticket | `Event_Ticket__c` | Master Detail |  |
| Event | `Event__c` | Master Detail |  |
| First Name | `First_Name__c` | Text | 255 |
| Last Name | `Last_Name__c` | Text | 255 |
| Number of Tickets | `Number_of_Tickets__c` | Number | 18,0 |
| Signup to Newsletter | `Signup_to_Newsletter__c` | Checkbox |  |
| Status | `Status__c` | Picklist | Pending Payment, Paid, Failed Payment, Cancelled |

---

## Field Details

| Field | Purpose |
|------|------|
| Cost | Stores the total registration cost for the selected ticket quantity. |
| Email | Identifies the attendee and is also used by the package to retrieve a user's tickets later. |
| Event Ticket | Links the registration to the chosen ticket type. |
| Event | Links the registration to the parent event. |
| First Name / Last Name | Capture the attendee or registrant details. |
| Number of Tickets | Stores how many seats were reserved in the registration. |
| Signup to Newsletter | Captures whether the attendee opted into future updates. |
| Status | Tracks whether the registration is paid, pending payment, cancelled, or failed. |
