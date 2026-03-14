# How Dynamic Checks Works

## Overview

Dynamic Checks separates checklist design from checklist execution.

Admins define reusable checklist templates using custom objects. When a user opens a record with the Dynamic Checks Lightning component, the package evaluates which template headers apply to that record, creates any missing `Check__c` records, and renders the resulting checks back to the user grouped into categories.

## Main Concepts

- `Check_Template_Header__c` groups a set of checklist templates and defines the target object, ordering, and filter behavior.
- `Check_Template__c` defines the individual checklist item, display type, help text, optional comments, and optional flow launch settings.
- `Check_Filter__c` provides record-level criteria used when a template header should only apply to some records.
- `Check__c` stores the live checklist item created for a specific record.

## Request or Data Flow

1. An admin configures template headers, filters, and templates.
2. A user opens a record page containing the `dynamicChecksContainer` component.
3. `ChecksContainerController` calls `ChecksHelper`.
4. `ChecksHelper` identifies the current object and loads the relevant template headers.
5. Headers marked `All` always apply. Headers marked filtered behavior are evaluated through `ChecksFilter`.
6. Missing `Check__c` records are created for applicable templates.
7. The helper returns `CheckCategory` and `Check` wrapper data to the Lightning UI.
8. Users complete checks in the UI, which updates `Check__c` directly.
9. If configured, `CheckLaunchFlow` can launch an autolaunched flow after a check is completed.
