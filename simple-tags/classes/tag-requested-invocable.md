# TagRequestedInvocable

## API Name
`TagRequestedInvocable`

## Description

`TagRequestedInvocable` is the Flow-facing automation class used to create tag links for requested tags once they are ready to be applied to a record.

It accepts a collection of request inputs, resolves the correct `Tag_Link__c` relationship field using metadata, creates the tag link records, and inserts them.

This class is particularly useful in approval or review processes where a requested tag has been activated and now needs to be linked back to the record it was requested from.

---

## Sharing Model
`without sharing`

## Tested By
`TagRequestInvocableTest`

---

## Invocable Method

| Method | Purpose |
|------|------|
| `linkRequestedTag(List<Request> requests)` | Creates one or more `Tag_Link__c` records for requested tags |

---

## Request Variables

The inner `Request` class defines the invocable inputs:

| Variable | Type | Purpose |
|------|------|------|
| `tagId` | `Id` | The tag record to link |
| `requestedRecordId` | `Id` | The record that should receive the tag link |
| `requestedObjectAPIName` | `String` | The object name used to look up the correct `Tag_Link__c` field |

---

## How It Works

For each request, the class:

1. looks up `Tag_Meta__mdt` using `requestedObjectAPIName`
2. gets the configured `Field_API_Name__c`
3. creates a `Tag_Link__c`
4. sets `Tag__c`
5. dynamically sets the correct lookup field for the requested record
6. inserts all generated links

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `Tag_Meta__mdt` | Maps supported object names to the correct `Tag_Link__c` field |
| `Tag_Link__c` | Stores the new record-tag relationship |

---

## Typical Usage

This class is a good fit for Flow automation such as:

- when a requested tag is approved
- when an admin activates a requested tag
- when the package needs to automatically link the new tag back to the originating record

---

## Important Notes

| Topic | Detail |
|------|------|
| Metadata-driven | The relationship field is not hardcoded; it is resolved from `Tag_Meta__mdt` |
| Batch-style processing | Accepts a list of requests so it can be used efficiently from Flow |
| DML mode | Inserts links using `insert as user` |

---

## Related Classes

- [TagRequestHelper](/classes/tag-request-helper)
- [TagHelper](/classes/tag-helper)
