# Custom Objects

Add one markdown file per object, metadata type, or setting.

Suggested naming pattern:

- `my-object.md`
- `my-metadata-type.md`
- `my-setting.md`

Use the richer object-page structure already established in `Documentation/simple-tags/custom-objects`.

Suggested content for each page:

- Title
- API Name
- Description
- Fields table
- Field Details table
- List Views or related admin views where relevant

Keep the tone descriptive and operational. These pages should explain what the object is for in business terms, not just restate field names.

For standard custom object pages, use a structure like:

```md
# Object Name

## API Name
`Object_API_Name__c`

## Description

Explain what the object represents, why it exists, and how it fits into the package workflow.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Example Field | Example_Field__c | Text | 255 |

---

## Field Details

| Field | Purpose |
|------|------|
| Example Field | Explain how the field is used in practice. |

---

## List Views

| Name | Fields | Filter |
|------|------|------|
| All | Name | No Filter |
```

If the object does not have list views or that information is not important, omit that section rather than inventing content.
