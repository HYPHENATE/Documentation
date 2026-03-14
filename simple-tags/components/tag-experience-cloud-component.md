
# Experience Cloud

This package includes a dedicated **Experience Cloud** component that allows external users with the correct permissions to **view, add, request, and remove tags** from supported records.

This component is intended for use where tagging needs to be exposed beyond internal Salesforce users, such as within partner portals, volunteer portals, supporter journeys, or other Experience Cloud sites.

It provides the same core tagging functionality as the internal **SimpleTags** component, but is designed specifically for use within **Experience Cloud** and can also be used within **Flow screens**.

---

## API Name
`SimpleTags (Experience Cloud)`

## Builder Name
`tagExperienceCloudComponent`

## Description
This is the same as the internal SimpleTags component but is designed to work within Experience Cloud.

---

## Targets

- `lightningCommunity__Page`
- `lightningCommunity__Default`
- `lightning__FlowScreen`

---

## Target Configs

### lightningCommunity__Default

| Name | API Name | Data Type | Default | Required | Description |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Record Id | `recordId` | String |  | No | The Salesforce record Id that the component should load tags for. |
| Component Title | `cardTitle` | String | `Tags` | No | Allows the default title of the component to be overridden. |
| Component Icon | `cardIcon` | String | `standard:catalog` | No | Allows a different Lightning Design System icon to be displayed. Use the format `type:name`. |
| Display Categories | `displayCategories` | Boolean | `true` | No | Controls whether tags are grouped by category or shown as a flat list. |
| Enforce Read Only | `enforceReadOnly` | Boolean | `false` | No | Prevents users from adding or removing tags through the interface. |
| Prevent Request Tag | `preventRequestTag` | Boolean | `false` | No | Removes the ability for users to request a new tag when searching. |
| Tag Record Limit | `selectionLimit` | String |  | No | Maximum number of tags allowed on the record. Leave blank for no limit. |
| Allowed Category | `allowedCategory` | String |  | No | Restricts tags to specific categories (comma-separated). |
| Display View All Tags | `displayViewAllTags` | Boolean | `true` | No | Allows users to browse all available tags for the record/object. |

---

### lightning__FlowScreen

| Name | API Name | Data Type | Default | Required | Description |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Record Id | `recordId` | String |  | No | Input-only value used to identify the record that tags should be loaded for. |
| Component Title | `cardTitle` | String | `Tags` | No | Input-only value that overrides the default component title. |
| Component Icon | `cardIcon` | String | `standard:catalog` | No | Input-only value defining the icon shown on the component. |
| Display Categories | `displayCategories` | Boolean | `true` | No | Determines whether tags are grouped by category. |
| Enforce Read Only | `enforceReadOnly` | Boolean | `false` | No | Prevents edits when set to true. |
| Prevent Request Tag | `preventRequestTag` | Boolean | `false` | No | Removes the ability for users to request tags. |
| Tag Record Limit | `selectionLimit` | String |  | No | Maximum number of tags allowed on the record. |
| Allowed Category | `allowedCategory` | String |  | No | Restricts categories available in the component. |
| Display View All Tags | `displayViewAllTags` | Boolean | `true` | No | Allows browsing of all available tags for the record/object. |

---

## Behaviour Notes

| Area | Detail |
|--------------|--------------|
| Record Context | The component requires a valid `recordId` to retrieve and manage tags. |
| Category Filtering | If `allowedCategory` is provided, only those categories are displayed. |
| Read Only Mode | When `enforceReadOnly` is enabled, tags are visible but not editable. |
| Tag Requests | The tag request option can be disabled using `preventRequestTag`. |
| Tag Limits | If `selectionLimit` is set, users cannot exceed the defined number of tags. |
| Flow Support | The component can be embedded inside a Salesforce Flow screen. |

---

## Example Configuration

| Setting | Example Value |
|--------------|--------------|
| Record Id | `{!recordId}` |
| Component Title | `Programme Tags` |
| Component Icon | `utility:tag` |
| Display Categories | `true` |
| Enforce Read Only | `false` |
| Prevent Request Tag | `false` |
| Tag Record Limit | `5` |
| Allowed Category | `Programme Area,Supporter Interest` |
| Display View All Tags | `true` |

---

## Embedding Within a Custom LWC

Developers may embed this component inside a custom Lightning Web Component when building tailored user experiences.

### Example HTML

```html
<template>
    <c-tag-experience-cloud-component
        record-id={recordId}
        card-title="Programme Tags"
        card-icon="utility:tag"
        display-categories="true"
        enforce-read-only="false"
        prevent-request-tag="false"
        selection-limit="5"
        allowed-category="Programme Area,Supporter Interest"
        display-view-all-tags="true">
    </c-tag-experience-cloud-component>
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
| Record Id | The parent component must provide the correct `recordId`. |
| Attribute Naming | Use kebab-case attributes such as `record-id` and `card-title`. |
| String and Boolean Values | Ensure property values are passed correctly in your implementation. |
| Reuse | This allows the tagging UI to be reused inside custom page layouts. |