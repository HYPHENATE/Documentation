# ChecksHelper

`ChecksHelper` is the core orchestration class in the package.

## Purpose

It determines which checklist headers apply to a record, creates missing `Check__c` records, and returns wrapper data grouped into categories for the Lightning UI.

## What It Does

- detects the current record object type
- loads existing live checks
- queries relevant template headers and templates
- evaluates filtered headers through `ChecksFilter`
- creates missing `Check__c` records when needed
- builds `CheckCategory` and `Check` wrapper structures
- applies owner-only edit logic

## Important Note

The class includes a fix noted in the source comments to ensure existing checks are queried only for the current record, helping avoid excessive row retrieval in large orgs.
