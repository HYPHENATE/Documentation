# TagHelper

## API Name
`TagHelper`

## Description

`TagHelper` provides reusable helper methods used across the SimpleTags Apex layer.

Its main responsibilities are:

- resolving supported object mappings from metadata
- returning configured object options
- checking CRUD and field-level access

Because many other classes rely on metadata-driven object support and security checks, this helper acts as a foundational utility class within the package.

---

## Sharing Model
`with sharing`

## Tested By
`TagHelperTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Metadata lookup | Resolves the correct `Tag_Link__c` field API name for a supported object |
| Object option generation | Returns a JSON list of configured object names for UI use |
| CRUD/FLS support | Provides reusable access-check methods for read, create, update, and delete evaluation |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `getCorrectObjectName(String objectName)` | `String` | Looks up the correct `Tag_Link__c` field API name from `Tag_Meta__mdt` |
| `availableObjectList()` | `String` | Returns a JSON array of available object labels/values based on metadata |
| `isAccessible(String sobjectName, List<String> fields)` | `Boolean` | Confirms object and field read access |
| `isCreateable(String sobjectName, List<String> fields)` | `Boolean` | Confirms object and field create access |
| `isUpdateable(String sobjectName, List<String> fields)` | `Boolean` | Confirms object and field update access |
| `isDeletable(String sobjectName)` | `Boolean` | Confirms object delete access |

---

## Internal Methods

| Method | Purpose |
|------|------|
| `areFieldsAccessible` | Reusable helper for field-level read checks |
| `areFieldsCreateable` | Reusable helper for field-level create checks |
| `areFieldsUpdateable` | Reusable helper for field-level update checks |

---

## Metadata Usage

`getCorrectObjectName()` queries `Tag_Meta__mdt` by `MasterLabel` and returns `Field_API_Name__c`.

That mapping is central to the package because it allows Apex to dynamically determine which field on `Tag_Link__c` should be used for each supported object.

Example conceptually:

| Object Label | Returned Field API Name |
|------|------|
| `Account` | `Account__c` |
| `Campaign` | `Campaign__c` |

If no mapping is found, the method returns a configured fallback label value.

---

## Response Behaviour

`availableObjectList()` returns a JSON array containing objects in this form:

- `label`
- `value`

This makes it suitable for use in UI configuration controls.

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `Tag_Meta__mdt` | Stores the object-to-field mapping used throughout the package |
| `Schema.describeSObjects` | Used for CRUD and field-level access checks |
| Custom Labels | Used for fallback messaging when mappings are missing |

---

## Important Notes

| Topic | Detail |
|------|------|
| Central utility | This class is widely reused by controller and automation classes |
| Metadata-driven design | Object support is determined by metadata rather than hardcoded field names |
| Security helper | CRUD/FLS checks are centralised here to avoid duplication |

---

## Related Classes

- [TagController](/classes/tag-controller)
- [TagBrowserController](/classes/tag-browser-controller)
- [TagRequestedInvocable](/classes/tag-requested-invocable)
