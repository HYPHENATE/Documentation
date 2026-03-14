# Tag Category

## API Name
`Tag_Category__c`

## Description

The **Tag Category** object is used to organise tags into logical groupings.  
It provides structure and governance for the tagging framework by allowing tags to be classified under a common theme or purpose.

In many non-profit organisations, tags may be used to classify records across programmes, campaigns, supporters, or operational activities. Tag Categories help ensure these tags remain organised and meaningful by grouping them into clearly defined areas.

For example, categories might represent:

- Programme Areas
- Funding Sources
- Campaign Types
- Supporter Interests
- Operational Classifications

By structuring tags within categories, organisations can maintain a consistent tagging approach while still allowing flexibility as new reporting or classification needs emerge.

Each **Tag Category** can contain multiple **Tags**, which are then applied to records through the **Tag Link** object.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|--------------|--------------|--------------|--------------|
| Name | Name | Text | 80 |
| Description | Description__c | Long Text Area | 32768 |
| Status | Status__c | Picklist | Active / Inactive |
| Display Icon | Display_Icon__c | Text | 255 |

---

## Field Details

| Field | Purpose |
|------|------|
| Name | The label used to identify the category within the tagging framework. |
| Description | Provides additional context about how the category should be used. |
| Status | Determines whether the category is currently available for use. Inactive categories can be retained for historical reporting while preventing new tags from being created under them. |
| Display Icon | Optional icon reference used by Lightning Web Components to visually represent the category in the tagging interface. |

---

## List Views

| Name | Fields | Filter |
|--------------|--------------|--------------|
| All | Name, Description, Status | No Filter |