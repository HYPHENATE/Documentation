# TagController

## API Name
`TagController`

## Description

`TagController` is the core Apex controller for the SimpleTags package.

It provides the main runtime operations used by internal tagging components, including:

- checking whether a user can view or manage tags
- retrieving existing tags for a record
- adding tag links
- removing tag links
- searching for available tags that are not already assigned

This class is the primary service layer used by the internal LWC components and is also reused by the Experience Cloud helper class.

---

## Sharing Model
`with sharing`

## Tested By
`TagController_Test`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Permission checks | Determines whether the current user can view tags only or can fully manage them |
| Existing tag retrieval | Loads existing tags for a record and returns them as JSON |
| Category-aware responses | Can return tag data grouped by category or as a flat list |
| Tag creation | Creates `Tag_Link__c` records dynamically for supported objects |
| Tag removal | Deletes an existing tag link |
| Tag searching | Returns only active tags that are not already linked to the current record |

---

## AuraEnabled Methods

| Method | Returns | Purpose |
|------|------|------|
| `getUserPermissions(String objectName)` | `String` | Returns a JSON payload describing whether the current user can view and/or manage tags |
| `addtagtorecord(String tagId, String recordId, String objectName)` | `String` | Creates a new `Tag_Link__c` record for the supplied record and tag |
| `getExistingTags(String recordId, String objectName, Boolean displayCategories, String category)` | `String` | Returns existing tag data for the current record, either grouped by category or as a flat list |
| `searchTags(String recordId, String objectName, String searchTerm, String category)` | `List<Tag__c>` | Searches for active tags that are not already linked to the record |
| `removeTagLink(String tagId)` | `String` | Deletes a tag link record |

---

## Internal Methods

| Method | Purpose |
|------|------|
| `userCanView` | Confirms whether the current user has read access to the required objects and fields |
| `userCanWorkWithTags` | Confirms whether the current user can read, create, and delete tag links |
| `getExistingTagsQuery` | Queries `Tag_Link__c` records for the current record |
| `generateCategoryMapOfExistingTags` | Builds a category-based structure from existing tag links |
| `handleCategorisedTagLinks` | Adds a tag link to the appropriate category group |
| `handleUnCategorisedTagLinks` | Adds uncategorised tag links to the fallback group |
| `generateCategoryExistingTagsResponse` | Generates a JSON response grouped by category |
| `generateNoCategoryExistingTagsResponse` | Generates a flat JSON response |
| `filterTags` | Filters searched tags so only those valid for the current object are returned |

---

## JSON Response Behaviour

### Permissions Response

`getUserPermissions` returns a JSON object containing:

- `canView`
- `canManage`

### Existing Tags Response

When `displayCategories = true`, the response contains:

- `categories[]`
  - `name`
  - `icon`
  - `tags[]`

When `displayCategories = false`, the response contains:

- `tags[]`

This makes the method flexible enough to support both grouped and simple UI presentations.

---

## Security and Access

| Area | Detail |
|------|------|
| Object mapping | Uses `TagHelper.getCorrectObjectName()` to resolve the correct `Tag_Link__c` field for a record type |
| CRUD/FLS checks | Delegates permission checks to reusable methods in `TagHelper` |
| DML mode | Uses `insert as user` and `delete as user` for tag link changes |
| Query shape | Existing tag retrieval is dynamic because the target field on `Tag_Link__c` varies by object |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `TagHelper` | Metadata mapping and CRUD/FLS checks |
| `Tag_Link__c` | Stores record-to-tag relationships |
| `Tag__c` | Source of active and searchable tags |
| `Tag_Category__c` | Used when returning grouped category responses |
| Custom Labels | Used for success and error messages |

---

## Typical Usage

This class is used when an internal component needs to:

1. check whether the user can manage tags
2. load the current tag state for a record
3. search for new tags
4. add or remove tag links

It is the main orchestration class for internal tag management.

---

## Related Classes

- [TagExperienceCloudHelper](/classes/tag-experience-cloud-helper)
- [TagHelper](/classes/tag-helper)
- [TagBrowserController](/classes/tag-browser-controller)
