# Event View

## API Name
`Event_Views__c`

## Description

The **Event View** object stores view-tracking entries for event pages. The package uses these records to support engagement reporting such as total visits and unique visits.

Whether these records are created for all visits or only unique visits is controlled through the packaged event management settings.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Event | `Event__c` | Master Detail |  |
| Is Repeat | `Is_Repeat__c` | Checkbox |  |

---

## Field Details

| Field | Purpose |
|------|------|
| Event | Links the view record back to the event being viewed. |
| Is Repeat | Distinguishes repeat visits from first-time visits when unique view tracking is enabled. |
