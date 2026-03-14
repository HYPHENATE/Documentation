
# Read Only Tags Component

The **Read Only Tags** component is a lightweight Lightning Web Component used to display tags associated with a record without allowing any editing or management actions.

This component is typically used in situations where tags should be **visible but not editable**, such as summary panels, dashboards, embedded components, or custom interfaces built by developers.

Unlike the standard **SimpleTags** component, this component does not interact with the tagging framework directly. Instead, it expects a collection of tag objects to be passed into it and simply renders them as styled tag pills using Salesforce Lightning Design System styles.

This makes it useful for **custom interfaces** where tags have already been retrieved via Apex, Flow, or another parent component.

---

## API Name
`tagReadOnlyTags`

## Description
Lightweight component used for displaying tags in a read-only format.

---

## Exposure

This component is **not exposed directly in Lightning App Builder** and is intended for use **within other Lightning Web Components**.

```
isExposed = false
```

Because of this, the component is normally embedded inside another LWC that handles the retrieval of tags.

---

## Public Properties

| Name | API Name | Data Type | Required | Description |
|--------------|--------------|--------------|--------------|--------------|
| Tags | `tags` | Array | Yes | Collection of tag objects to display. Each tag should contain a tag identifier and display name. |

---

## Expected Tag Structure

The component expects each tag object to follow a structure similar to the example below:

```json
{
  "tagId": "a0123456789ABC",
  "tagName": "Programme Area"
}
```

Only the following properties are required:

| Property | Description |
|--------------|--------------|
| tagId | Unique identifier for the tag |
| tagName | Label displayed in the UI |

---

## Behaviour Notes

| Area | Detail |
|--------------|--------------|
| Read Only | This component only displays tags and does not allow editing or management. |
| Data Source | Tag data must be supplied by a parent component or service. |
| Rendering | Tags are rendered using Salesforce Lightning Design System pill styling. |
| Reusability | Designed to be reused within custom components where tag display is required. |

---

## Example Usage

Developers can embed this component inside another Lightning Web Component and pass the tags array as a property.

### Example HTML

```html
<template>
    <c-tag-read-only-tags tags={recordTags}></c-tag-read-only-tags>
</template>
```

### Example JavaScript

```javascript
import { LightningElement, track } from 'lwc';

export default class CustomRecordSummary extends LightningElement {
    @track recordTags = [
        { tagId: 'a01XXXXXXX1', tagName: 'Programme Area' },
        { tagId: 'a01XXXXXXX2', tagName: 'Campaign Type' }
    ];
}
```

---

## Component Markup

The component renders each tag as a Lightning Design System pill.

```html
<template>
    <template for:each={tags} for:item="tag">
        <span key={tag.tagId} part="pill" class="slds-pill customPill slds-var-m-bottom_xx-small slds-var-p-around_xx-small">
            <span class="slds-pill__label customPillLabel">
                {tag.tagName}
            </span>
        </span>
    </template>
</template>
```

---

## Example Use Cases

This component is commonly used for:

- Displaying tags within custom record summary components
- Showing tag classifications in dashboards or overview panels
- Presenting tags inside Experience Cloud pages without edit permissions
- Embedding tag displays inside bespoke Lightning interfaces