# TagRequestHelper

## API Name
`TagRequestHelper`

## Description

`TagRequestHelper` handles requested tag submission.

When a user wants to request a tag that does not already exist, this class creates a `Tag__c` record in a requested state and returns a JSON payload that can be used by the UI to display a toast message.

This allows the package to support a controlled tag-request workflow instead of requiring users to create active tags directly.

---

## Sharing Model
`without sharing`

## Tested By
`TagRequestHelper_Test`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Requested tag creation | Creates a `Tag__c` record with the requested status |
| Request context capture | Stores the source object, source record, and optional category |
| UI response generation | Returns a JSON payload containing toast title, message, and variant |
| Validation | Returns an error response when no tag name is supplied |

---

## AuraEnabled Methods

| Method | Returns | Purpose |
|------|------|------|
| `requestTag(String tagName, String objectName, String recordId, String category)` | `String` | Creates a requested tag and returns a JSON toast-style response |

---

## Internal Methods

| Method | Purpose |
|------|------|
| `generateMessage` | Generates the JSON response sent back to the caller |

---

## Request Behaviour

If a tag name is supplied, the class attempts to create a `Tag__c` record with:

- `Name`
- `Status__c` set from a custom label default
- `Available_Objects__c`
- `Requested_Record_Id__c`
- `Requested_Object__c`
- `Tag_Category__c`

If creation succeeds, the method returns a success response.  
If DML fails, it returns an error response.  
If no tag name is supplied, it returns a validation-style error response.

---

## Response Shape

The returned JSON contains:

- `toastTitle`
- `toastMessage`
- `toastVariant`

This keeps the LWC layer simple because it can display the returned toast payload directly.

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `Tag__c` | Stores the requested tag record |
| Custom Labels | Provide default status and toast messaging content |

---

## Important Notes

| Topic | Detail |
|------|------|
| Sharing model | Runs `without sharing` to support request submission scenarios more flexibly |
| DML mode | Uses `insert as user` when creating the requested tag |
| Workflow role | This class creates the requested tag record, but does not create the final `Tag_Link__c` relationship |

---

## Related Classes

- [TagRequestedInvocable](/classes/tag-requested-invocable)
- [TagExperienceCloudHelper](/classes/tag-experience-cloud-helper)
