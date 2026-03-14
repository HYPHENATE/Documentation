# Event Registration Flow

## API Name
`Event_Registration_Flow`

## Flow Type
`Screen Flow`

## Description

`Event Registration Flow` is the main attendee registration flow packaged with Event Management. It collects attendee details, validates ticket availability, creates `Event_Registration__c` records, and then routes the registrant to the correct confirmation experience.

It supports both guest and logged-in users and can be referenced from the `Registration_Form_API_Name__c` field on `Event__c`.

---

## Launch Context

| Area | Detail |
|------|------|
| Trigger | Launched from the registration modal component rather than directly from a record page. |
| Users | Guest users and authenticated users registering for event tickets. |
| Entry Criteria | Requires `eventId`, `eventTicketId`, and `numberOfTickets` input variables. |

---

## Flow Steps

### Step 1 - Load Event And Ticket Context

The flow starts by retrieving the selected event and ticket so it can validate availability and display the right registration experience.

### Step 2 - Branch For Guest Or Logged-In Users

The flow checks `$User.UserType` to decide whether it should show the guest registration screen or the logged-in registration screen.

### Step 3 - Validate Existing Registrations And Limits

The flow checks prior registrations for the same email address, calculates the attendee's existing ticket count, and ensures the requested ticket quantity does not exceed the allowed limit or remaining stock.

### Step 4 - Create The Registration

The flow creates the `Event_Registration__c` record with the attendee details, ticket count, cost, newsletter preference, and the correct starting status.

### Step 5 - Show The Correct Confirmation Experience

Depending on whether payment is required and whether the event is virtual, the flow shows a payment message, virtual-event guidance, or an e-ticket download path.

---

## Inputs and Outputs

| Name | Direction | Type | Purpose |
|------|------|------|------|
| `eventId` | Input | String | Identifies the selected event. |
| `eventTicketId` | Input | String | Identifies the selected ticket type. |
| `numberOfTickets` | Input | Number | Captures how many tickets the attendee wants to register. |
| `eventRegistrationId` | Output | String | Returns the created registration ID for follow-on messaging or download links. |

---

## Data Impact

| Area | Detail |
|------|------|
| Objects | Reads `Event__c`, `Event_Ticket__c`, and existing `Event_Registration__c` records; creates new `Event_Registration__c` records. |
| Actions | Validates ticket availability, registration limits, and final confirmation path. |

---

## Operational Notes

| Topic | Detail |
|------|------|
| Payment logic | Uses ticket cost formulas to decide whether the attendee should see a payment-required message or a direct e-ticket confirmation. |
| Guest support | Includes separate screens for guest and logged-in users to streamline data capture. |
| Reusability | Because the flow API name is stored on the event record, teams can clone and swap flows per event if needed. |

---

## Related Automation

- [EVTViewRegistrationController](/event-management/classes/evt-view-registration-controller)
