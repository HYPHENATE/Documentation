# Tag Meta

## API Name

`Tag_Meta__mdt`

## Description

The **Tag Meta** custom metadata type is used to configure how the tagging components interact with Salesforce records.

Rather than hardcoding object-specific logic into Lightning Web Components or Apex, this metadata allows the framework to dynamically determine which fields should be used when retrieving and saving tags for a record.

Each metadata record defines the **API name of the lookup field on the Tag Link object** that represents the relationship to a supported Salesforce object. This allows the tagging framework to support multiple objects without requiring code changes.

When a tagging component loads, it reads the relevant **Tag Meta configuration** to determine:

- Which lookup field on **Tag Link** represents the current record
- How to retrieve existing tag relationships
- How to create or remove tag link records when users add or remove tags

Using custom metadata for this configuration provides several benefits:

- **Flexible configuration** without modifying code
- **Easier deployment between environments**
- **Consistent behaviour across Lightning components and flows**

For example, a metadata record might define that:

- `Account__c` is the lookup field used when tagging **Account** records
- `Campaign__c` is used when tagging **Campaign** records

This allows the same tagging components to work dynamically across multiple objects.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Label | Label | Text | 80 |
| Field API Name | Field_API_Name__c | Text | 255 |

---

## Field Details

| Field | Purpose |
|------|------|
| Label | Identifies the configuration entry used by the tagging framework. Typically represents the object or configuration name. |
| Field API Name | The API name of the lookup field on the **Tag Link** object that links a tag to a specific Salesforce record. This value is used by the components and Apex logic to dynamically retrieve and create tag relationships. |

---

## List Views

| Name | Fields | Filter |
|--------------|--------------|--------------|