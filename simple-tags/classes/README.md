# Apex Classes

This section documents the Apex classes used within the **SimpleTags** package.

The package uses a small set of focused Apex classes to support:

- core tag retrieval and management
- Experience Cloud access patterns
- tag browsing and bulk save behaviour
- tag request submission
- Flow and invocable automation support
- metadata-driven object configuration
- reusable security and object-mapping helpers

Test classes are **not documented as separate pages** in this section. Instead, each production class includes a **Test Class** reference showing which test class validates it.

---

## Class Overview

| Class | Purpose | Tested By |
|------|------|------|
| [TagController](/classes/tag-controller) | Core controller for retrieving, searching, adding, and removing tags on records | `TagController_Test` |
| [TagExperienceCloudHelper](/classes/tag-experience-cloud-helper) | Experience Cloud wrapper around the core controller methods | `TagExperienceCloudHelperTest` |
| [TagBrowserController](/classes/tag-browser-controller) | Supports browsing all available tags and saving tag selections in bulk | `TagBrowserControllerTest` |
| [TagRequestHelper](/classes/tag-request-helper) | Handles requested tag submission and toast-style response payloads | `TagRequestHelper_Test` |
| [TagRequestedInvocable](/classes/tag-requested-invocable) | Invocable class used to create tag links for approved requested tags | `TagRequestInvocableTest` |
| [TagHelper](/classes/tag-helper) | Reusable helper methods for metadata lookup and CRUD/FLS checks | `TagHelperTest` |
| [TagComponentHelper](/classes/tag-component-helper) | Dynamic picklist provider used by Flow and component configuration | `TagComponentHelperTest` |

---

## Design Notes

A few important design choices appear across the Apex layer:

| Area | Detail |
|------|------|
| Metadata-driven object support | `Tag_Meta__mdt` is used to resolve which field on `Tag_Link__c` should be used for each supported object |
| JSON responses | Several controller methods return JSON strings for easy consumption by LWCs |
| User-mode operations | Queries and DML frequently use `WITH USER_MODE` and `insert/delete as user` to respect runtime access |
| Layered access | Experience Cloud methods call a dedicated helper which then delegates into the shared core controller logic |
| Requested tags | Requested tags are created separately from active tag links, allowing review and approval workflows |