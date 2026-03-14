# Permissions Overview

## Overview

Dynamic Checks includes packaged permission sets and a custom permission, which differs from the current `ApexTools` model and is closer to the more role-specific approach used in `Simple Tags`.

The package includes:

- `Dynamic_Checks_Administrators`
- `Dynamic_Checks`
- `Dynamic_Checks_Access`

## Recommended Approach

In most implementations:

- assign `Dynamic_Checks_Administrators` to the people who manage template headers, templates, and filters
- assign `Dynamic_Checks` to end users who need to complete live checks on records
- use the custom permission as part of the component access model

## Notes

For consistency with the current docs site structure, the detailed packaged permissions are documented in separate pages:

- [Dynamic Checks Administrators](/dynamic-checks/permissions/dynamic-checks-administrators)
- [Dynamic Checks](/dynamic-checks/permissions/dynamic-checks)
