# Tag Link

## API Name

`Tag_Link__c`

## Description

The **Tag Link** object represents the relationship between a **Tag** and a Salesforce record.

This object is the core of the tagging framework, as it stores the actual tagging relationship and enables records across Salesforce to be classified using tags.

A Tag Link record is created whenever a tag is applied to a supported record. The object contains lookups to the tagged record and the associated **Tag**, allowing tags to behave like structured Salesforce data that can be used in reporting, automation, and integrations.

Tag Links also define which Salesforce objects support tagging. By adding lookup fields to specific objects (such as Account, Campaign, or custom objects), administrators can enable tagging for those records. Once configured, users can apply relevant tags to those records using the tagging components provided in the package.

Because tagging relationships are stored as records, organisations can create **custom report types** that include tag data, enabling richer reporting and insights than standard Salesforce tagging features.

For example, non-profit organisations might use Tag Links to:

- Classify accounts by programme involvement
- Identify campaigns by strategic theme
- Categorise operational records for reporting
- Track supporter interests or engagement areas

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Name | Name | Auto Number | TLID-{000000000} |
| Tag Name | TagName__c | Formula | Displays the associated Tag Name |
| Status | Status__c | Picklist | Active / Inactive / Requested |
| Account | Account__c | Lookup | Account |
| Tag | Tag__c | Master Detail | Tag__c |

---

## Field Details

| Field | Purpose |
|------|------|
| Name | System-generated identifier for the Tag Link record. |
| Tag Name | Formula field that displays the name of the associated tag for easier visibility in lists and reports. |
| Status | Indicates whether the tagging relationship is currently active, inactive, or pending approval. |
| Account | Lookup to the record being tagged. Additional lookup fields can be added to enable tagging for other objects. |
| Tag | Master-detail relationship to the Tag that is being applied to the record. |

---

## List Views

| Name | Fields | Filter |
|--------------|--------------|--------------|