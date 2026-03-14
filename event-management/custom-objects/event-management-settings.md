# Event Management Settings

## API Name
`Event_Management_Settings__c`

## Description

The **Event Management Settings** custom setting controls package-level behaviour for view tracking.

Rather than hardcoding that logic into the controllers, the package reads these settings to decide whether every visit should be logged or whether only unique visits should be stored.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Register Unique Views | `Register_Unique_Views__c` | Checkbox |  |
| Register Views | `Register_Views__c` | Checkbox |  |

---

## Field Details

| Field | Purpose |
|------|------|
| Register Unique Views | Enables logging of unique views, typically marking repeat visits separately. |
| Register Views | Enables logging of all views regardless of whether the visitor has already seen the event page. |
