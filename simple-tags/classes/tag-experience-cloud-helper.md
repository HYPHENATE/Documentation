# TagExperienceCloudHelper

## API Name
`TagExperienceCloudHelper`

## Description

`TagExperienceCloudHelper` is a wrapper class designed for Experience Cloud use cases.

It accepts a `recordId`, derives the underlying object type automatically, and then delegates most of the work to the shared internal classes such as `TagController`, `TagRequestHelper`, and `TagBrowserController`.

This keeps the Experience Cloud interface simpler, because callers do not need to provide `objectName` explicitly.

---

## Sharing Model
`with sharing`

## Tested By
`TagExperienceCloudHelperTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Object resolution | Derives the current object from the supplied `recordId` |
| Delegation | Passes requests into the appropriate core SimpleTags service class |
| Experience Cloud simplification | Removes the need for external callers to provide `objectName` |
| Tag request support | Submits requested tags for external users |
| Tag browser support | Returns all available tags and current selections for browsing interfaces |

---

## AuraEnabled Methods

| Method | Returns | Purpose |
|------|------|------|
| `getUserPermissions(String recordId)` | `String` | Returns can-view/can-manage permissions for the record’s object type |
| `addtagtorecord(String tagId, String recordId)` | `String` | Adds a selected tag to the current record |
| `getExistingTags(String recordId, Boolean displayCategories, String category)` | `String` | Returns tags already linked to the record |
| `searchTags(String recordId, String searchTerm, String category)` | `List<Tag__c>` | Searches for valid tags for the record |
| `removeTagLink(String tagId)` | `String` | Removes an existing tag link |
| `requestTag(String tagName, String recordId, String category)` | `String` | Submits a requested tag |
| `getListOfAllAvailableTags(String recordId, Boolean displayCategories, String category)` | `String` | Returns the full browseable tag payload for the record |

---

## How It Works

The class follows a very lightweight pattern:

1. determine the object API name from `recordId`
2. call the relevant shared service class
3. return the result unchanged

This makes it effectively an Experience Cloud adapter over the core tagging logic.

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `TagController` | Main tag retrieval, search, add, and remove operations |
| `TagRequestHelper` | Requested tag creation |
| `TagBrowserController` | Full browse-all-tags response generation |

---

## Typical Usage

This class is used by Experience Cloud LWCs where the component only has a `recordId` and needs to:

- load existing tags
- search and add tags
- request new tags
- browse all available tags
- remove linked tags

---

## Related Classes

- [TagController](/classes/tag-controller)
- [TagRequestHelper](/classes/tag-request-helper)
- [TagBrowserController](/classes/tag-browser-controller)
