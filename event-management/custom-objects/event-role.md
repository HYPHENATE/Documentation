# Event Role

## API Name
`Event_Role__c`

## Description

The **Event Role** object stores people associated with an event, such as speakers or other featured roles shown in the attendee experience.

The package uses these records to render the speaker or role area on the event detail page, usually filtered to only confirmed roles.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Bio | `Bio__c` | HTML | 32768 |
| Contact | `Contact__c` | Lookup |  |
| Event | `Event__c` | Master Detail |  |
| Image URL | `Image_URL__c` | URL |  |
| Image | `Image__c` | Text |  |
| Order | `Order__c` | Number | 18,0 |
| Status | `Status__c` | Picklist | Asked, Confirmed, Declined |

---

## Field Details

| Field | Purpose |
|------|------|
| Bio | Stores the speaker or role biography shown to attendees. |
| Contact | Links the role to a Salesforce contact when one is used. |
| Event | Links the role to the parent event. |
| Image URL | Supplies the image displayed in the attendee experience. |
| Order | Supports manual ordering when multiple roles are shown. |
| Status | Determines whether the role is only invited, confirmed, or declined. |
