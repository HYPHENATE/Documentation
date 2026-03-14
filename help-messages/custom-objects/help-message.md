# Help Message

## API Name
`Help_Message__c`

## Description

The **Help Message** object stores the contextual guidance content shown on Salesforce record pages.

Each record represents one message that can be shown for a target object. Messages may apply to all records of that object or only appear when configured filter conditions match the current record.

This object is also where editors control message order, draft status, and publication state.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| Help Message Name | Name | Text | 80 |
| Custom Filter Logic | Custom_Filter_Logic__c | Text | 255 |
| Filter Type | Filter_Type__c | Picklist | `AND`, `OR` |
| Is Draft | Is_Draft__c | Formula / Checkbox-style runtime field | Derived from status logic |
| Message Title | Message_Title__c | Text | 255 |
| Message | Message__c | Long Text Area | 32768 |
| Order | Order__c | Number | 18,0 |
| Records Valid For | Records_Valid_For__c | Picklist | `All`, filter-driven options |
| Record SObject Type | Record_SObjectType__c | Text | 255 |
| Status | Status__c | Picklist | Draft / Published / Unpublished |

---

## Field Details

| Field | Purpose |
|------|------|
| Help Message Name | Label used to identify the message record in configuration. |
| Custom Filter Logic | Reserved field for more advanced filter combinations where needed. |
| Filter Type | Determines how child filter rows should be evaluated. |
| Is Draft | Indicates whether the current message should be treated as draft content. |
| Message Title | Short heading shown in the component. |
| Message | Main body text shown to the user. |
| Order | Controls the order messages appear within the component. |
| Records Valid For | Determines whether the message applies to all records or only filtered records. |
| Record SObject Type | Stores the API name of the object the message applies to. |
| Status | Controls whether the message is visible to viewers or only to editors. |

---

## List Views

| Name | Fields | Filter |
|------|------|------|
| All | Standard message fields | Everything |
