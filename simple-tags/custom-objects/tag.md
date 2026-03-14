# Tag

## API Name

`Tag__c`

## Description

The **Tag** object represents an individual classification that can be applied to records within the tagging framework.

Tags allow records across Salesforce to be labelled with meaningful attributes that support improved reporting, filtering, and operational visibility. This can help organisations identify trends, categorise activities, and analyse data more effectively.

Each tag belongs to a **Tag Category**, which provides structure and governance for the tagging system.

Tags can optionally be configured to be available only for specific Salesforce objects. This ensures that users are only presented with relevant tagging options when working with different types of records.

The tagging framework also supports a **request workflow**, allowing users to request new tags when an appropriate classification does not yet exist. Requested tags can then be reviewed and approved before becoming active.

For example, a non-profit organisation might use tags to identify:

- Programme themes
- Campaign classifications
- Funding types
- Supporter interests
- Operational activities

Tags are ultimately applied to records through the **Tag Link** object, which stores the relationship between a tag and a record.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Name | Name | Text | 80 |
| Available Objects | Available_Objects__c | Long Text Area | 32768 |
| Status | Status__c | Picklist | Active / Inactive / Requested |
| Requested Record | Requested_Record__c | Hyperlink | |
| Requested Record Id | Requested_Record_Id__c | Text | 18 |
| Tag Category | Tag_Category__c | Lookup | Tag_Category__c |

---

## Field Details

| Field | Purpose |
|------|------|
| Name | The label used to identify the tag within the system. |
| Available Objects | Defines which Salesforce objects the tag can be applied to. This helps ensure that tags are only available where they are relevant. |
| Status | Indicates whether the tag is currently active, inactive, or pending approval as a requested tag. |
| Requested Record | Provides a link to the record associated with a tag request, giving context for why the tag was requested. |
| Requested Record Id | Stores the ID of the record associated with the request for reference and automation purposes. |
| Tag Category | Associates the tag with a Tag Category to maintain structure and organisation within the tagging framework. |

---

## List Views

| Name | Fields | Filter |
|--------------|--------------|--------------|
| All | Name | No Filter |
| Active Tags | Name, Available Objects, Requested Record, Created By | Status = Active |
| Inactive Tags | Name, Available Objects, Requested Record, Created By | Status = Inactive |
| Requested Tags | Name, Available Objects, Requested Record, Created By | Status = Requested |