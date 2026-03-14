# Permissions Overview

## Permission Model

Dynamic Checks uses two packaged permission sets and one custom permission:

- `Dynamic_Checks_Administrators`
- `Dynamic_Checks`
- `Dynamic_Checks_Access`

## Recommended Access

- Admin access: `Dynamic_Checks_Administrators`
- End-user access: `Dynamic_Checks`
- Feature access gate: `Dynamic_Checks_Access`

## Notes

Administrators can manage the template and filter objects as well as live checks. End users primarily work with `Check__c` records and read the supporting template configuration needed by the component.
