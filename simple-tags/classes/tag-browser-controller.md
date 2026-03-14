# TagBrowserController

## API Name
`TagBrowserController`

## Description

`TagBrowserController` supports the “browse all tags” experience in SimpleTags.

It is responsible for loading all available tags for a record’s object type, identifying which of those tags are already selected, and saving bulk changes when a user confirms a new selection.

This class is especially useful for modal-style interfaces where users need to browse, filter, and update many tags at once.

---

## Sharing Model
`with sharing`

## Tested By
`TagBrowserControllerTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Available tag retrieval | Loads all valid tags for a supported object |
| Existing tag detection | Queries which tags are already linked to the record |
| Response generation | Produces a JSON payload containing tags, categories, and selected item IDs |
| Bulk save orchestration | Compares the selected tag list with existing tag links and inserts/deletes the differences |
| Category metadata | Tracks category icons for grouped UI display |

---

## AuraEnabled Methods

| Method | Returns | Purpose |
|------|------|------|
| `saveTagList(String recordId, List<String> tagIds)` | `String` | Saves a complete set of selected tags for a record by inserting and deleting the required tag links |
| `getListOfAllAvailableTags(String recordId, String objectName, Boolean displayCategories, String category)` | `String` | Returns all valid tags for the record and indicates which are currently selected |

---

## Public/Internal Methods

| Method | Purpose |
|------|------|
| `getAllTagsQuery` | Loads active tags that are valid for the supplied object |
| `getExistingTagsQuery` | Loads existing tag links for the record |
| `generateTagResponse` | Builds the JSON response consumed by the browser UI |
| `getProcessingList` | Calculates which tag links need to be inserted or deleted |
| `insertDeleteRecord` | Executes the insert and delete operations |
| `handleCategorisedTags` | Adds a tag into a named category bucket |
| `handleUncategorisedTags` | Adds a tag into the fallback uncategorised bucket |

---

## Response Shape

The JSON response produced by `generateTagResponse()` contains:

- `tags[]`
  - `tagName`
  - `tagId`
  - `selected`
  - `category`
- `categories[]`
  - `label`
  - `value`
- `selectedItems[]`

This structure is designed to support UI controls such as:

- searchable tables
- category filters
- modal browsers
- bulk save actions

---

## Save Behaviour

When `saveTagList()` runs, the class:

1. resolves the correct `Tag_Link__c` field from metadata
2. loads the existing tag links for the record
3. compares the incoming selection to what already exists
4. inserts any new links
5. deletes any links no longer selected

This means the caller only needs to send the final selected list.

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `TagHelper` | Resolves the correct tag-link field for the current object |
| `Tag__c` | Source of available tags |
| `Tag_Link__c` | Existing and newly created record-tag relationships |
| `Tag_Category__c` | Category labels and icons for grouped display |

---

## Important Notes

| Topic | Detail |
|------|------|
| Object validity | Tags are included only if they are active and valid for the current object |
| Category status | Categorised tags are returned only when the category is active |
| Uncategorised tags | Tags without a category are grouped under `Uncategorised` |
| DML mode | Uses `insert as user` and `delete as user` |

---

## Related Classes

- [TagController](/classes/tag-controller)
- [TagExperienceCloudHelper](/classes/tag-experience-cloud-helper)
- [TagHelper](/classes/tag-helper)
