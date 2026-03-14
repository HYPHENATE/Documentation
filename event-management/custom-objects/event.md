# Event

## API Name
`Event__c`

## Description

The **Event** object is the hub of the package. It represents the event itself and stores the operational and experience-facing details that drive tickets, registrations, favourites, roles, and page rendering.

This is the record that event managers maintain in Salesforce and that the public-facing components query when rendering event listings and event detail pages.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Banner Image URL | `Banner_Image_URL__c` | URL |  |
| Banner Image | `Banner_Image__c` | Text |  |
| Description | `Description__c` | HTML | 32768 |
| End Date | `End_Date__c` | Date |  |
| End Time | `End_Time__c` | Time |  |
| Image URL | `Image_URL__c` | URL |  |
| Image | `Image__c` | Text |  |
| Is Online | `Is_Online__c` | Checkbox |  |
| Location | `Location__c` | Long Text Area | 32768 |
| No. People Favourited Event | `No_People_Favourited_Event__c` | Summary |  |
| Page Visits Total | `Page_Visits_Total__c` | Summary |  |
| Page Visits Unique | `Page_Visits_Unique__c` | Summary |  |
| Registration Form API Name | `Registration_Form_API_Name__c` | Text | 255 |
| Start Date | `Start_Date__c` | Date |  |
| Start Time | `Start_Time__c` | Time |  |
| Status | `Status__c` | Picklist | Setup, Registration, In Progress, Complete, Cancelled |
| Total Seats Registered | `Total_Seats_Registered__c` | Summary |  |
| Total Seats | `Total_Seats__c` | Summary |  |
| Type | `Type__c` | Picklist | Virtual, Conference, Workshop |

---

## Field Details

| Field | Purpose |
|------|------|
| Banner Image URL | Supplies the main banner image used on the event detail experience. |
| Description | Stores the long-form event content shown to attendees. |
| End Date / End Time | Define when the event finishes. |
| Image URL | Supplies the event card image used on listing and summary views. |
| Is Online | Flags whether the event should be treated as an online or virtual experience. |
| Location | Stores the venue or location text used in the attendee-facing view and map link. |
| Registration Form API Name | Tells the registration component which flow API name to launch for this event. |
| Start Date / Start Time | Define when the event begins. |
| Status | Controls the operational stage of the event and affects what attendees should see. |
| Total Seats / Total Seats Registered | Roll up ticket availability and registrations to support capacity reporting. |
| Type | Helps group and filter events, for example by virtual, conference, or workshop. |

---

## List Views

| Name | Fields | Filter |
|------|------|------|
| All | Name, Start Date, Status, Type | No Filter |
| Setup | Name, Start Date, Status | `Status__c = Setup` |
| Registration | Name, Start Date, Status | `Status__c = Registration` |
| In Progress | Name, Start Date, Status | `Status__c = In Progress` |
| Complete | Name, Start Date, Status | `Status__c = Complete` |
| Cancelled | Name, Start Date, Status | `Status__c = Cancelled` |
