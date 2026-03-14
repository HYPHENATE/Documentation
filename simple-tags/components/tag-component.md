
# Internal Component

The **SimpleTags** component is the standard tagging interface designed for **internal Salesforce users**.

This component allows users to **view, add, remove, and request tags** directly from supported records. It is intended to be placed on **Lightning Record Pages** or used within **Salesforce Flow screens** to provide a guided tagging experience.

The component dynamically loads the available tags for the current record and allows users to manage tag relationships through the SimpleTags framework.

---

## API Name
`tagComponent`

## Builder Name
`SimpleTags`

## Description
Standard default component for displaying and managing tags on a record via Flow or Lightning Record Page.

---

## Targets

- `lightning__RecordPage`
- `lightning__FlowScreen`

---

## Target Configs

### lightning__RecordPage

| Name | API Name | Data Type | Default | Required | Description |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Component Title | `cardTitle` | String | `Tags` | No | Allows the default title of the component to be overridden. |
| Component Icon | `cardIcon` | String | `standard:catalog` | No | Allows a different Lightning Design System icon to be displayed. Use the format `type:name`. |
| Display Categories | `displayCategories` | Boolean | `true` | No | Controls whether tags are grouped by category or displayed as a flat list. |
| Enforce Read Only | `enforceReadOnly` | Boolean | `false` | No | Prevents users from adding or removing tags when enabled. |
| Prevent Request Tag | `preventRequestTag` | Boolean | `false` | No | Removes the ability for users to request new tags when searching. |
| Tag Record Limit | `selectionLimit` | String |  | No | Defines the maximum number of tags allowed for the record. Leave blank for no limit. |
| Allowed Category | `allowedCategory` | String |  | No | Restricts the component to specific tag categories. Provide a comma-separated list of category names. |
| Display View All Tags | `displayViewAllTags` | Boolean | `true` | No | Allows users to browse all available tags for the current record or object. |

---

### lightning__FlowScreen

| Name | API Name | Data Type | Default | Required | Description |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Record Id | `recordId` | String |  | No | Input-only value used to identify the record that tags should be loaded for. |
| Object API Name | `objectApiName` | String |  | No | Input-only value used to identify the Salesforce object type for the record. |
| Component Title | `cardTitle` | String | `Tags` | No | Input-only value used to override the component title. |
| Component Icon | `cardIcon` | String | `standard:catalog` | No | Input-only value used to define the component icon. |
| Display Categories | `displayCategories` | Boolean | `true` | No | Controls whether tags are grouped by category. |
| Enforce Read Only | `enforceReadOnly` | Boolean | `false` | No | Prevents tag edits when set to true. |
| Prevent Request Tag | `preventRequestTag` | Boolean | `false` | No | Removes the ability to request tags from the interface. |
| Tag Record Limit | `selectionLimit` | String |  | No | Defines the maximum number of tags allowed for the record. |
| Allowed Category | `allowedCategory` | String |  | No | Restricts the component to specific tag categories. |
| Display View All Tags | `displayViewAllTags` | Boolean | `true` | No | Allows browsing of all available tags for the record or object. |
| Existing Tag Ids | `existingTagIds` | String[] |  | No | Output-only collection containing the IDs of tags currently applied to the record. |

---

## Behaviour Notes

| Area | Detail |
|--------------|--------------|
| Record Context | When placed on a Lightning Record Page, the component automatically detects the record context. |
| Flow Support | When used in Flow, `recordId` and `objectApiName` must be supplied. |
| Category Filtering | If `allowedCategory` is configured, only those categories will be displayed. |
| Read Only Mode | When `enforceReadOnly` is enabled, users can view tags but cannot modify them. |
| Tag Requests | The tag request option can be disabled using `preventRequestTag`. |
| Tag Limits | If `selectionLimit` is configured, users cannot exceed the specified number of tags. |
| Flow Output | The component can return the list of existing tag IDs through the `existingTagIds` output property. |

---

## Example Configuration (Lightning Record Page)

| Setting | Example Value |
|--------------|--------------|
| Component Title | `Record Tags` |
| Component Icon | `utility:tag` |
| Display Categories | `true` |
| Enforce Read Only | `false` |
| Prevent Request Tag | `false` |
| Tag Record Limit | `5` |
| Allowed Category | `Programme Area,Supporter Interest` |
| Display View All Tags | `true` |

---

## Example Use Cases

This component is commonly used for:

- Classifying records within internal Salesforce workflows
- Providing tagging capabilities on Lightning Record Pages
- Capturing classification data through Flow automation
- Managing programme, campaign, or operational tags on records

---

## Embedding Within a Custom LWC

Developers may embed the internal tagging component inside a custom Lightning Web Component when building a tailored user interface.

This allows teams to reuse the tagging functionality while integrating it into a custom layout or workflow.

### Example HTML

```html
<template>
    <c-tag-component
        record-id={recordId}
        card-title="Record Tags"
        card-icon="utility:tag"
        display-categories="true"
        enforce-read-only="false"
        prevent-request-tag="false"
        selection-limit="5"
        allowed-category="Programme Area"
        display-view-all-tags="true">
    </c-tag-component>
</template>
```

### Example JavaScript

```javascript
import { LightningElement, api } from 'lwc';

export default class CustomRecordTagPanel extends LightningElement {
    @api recordId;
}
```

### Developer Notes

| Topic | Detail |
|--------------|--------------|
| Record Id | The parent component must provide the `recordId` for the record being tagged. |
| Attribute Naming | When embedding in HTML, use kebab-case attributes such as `record-id` and `card-title`. |
| Flow Usage | When used inside Flow, both `recordId` and `objectApiName` must be supplied. |
| Reuse | This approach allows the tagging interface to be reused within custom Lightning interfaces without rebuilding the tagging logic. |