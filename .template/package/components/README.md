# Components

Add one markdown file per Lightning Web Component, Flow screen component, helper component, or reusable UI building block.

Use the richer component-page structure already established in `Documentation/simple-tags/components`.

Suggested content for each page:

- Title
- API Name
- Builder Name where relevant
- Description
- Targets or exposure details
- Public properties or target configs
- Expected data structure where relevant
- Behaviour notes
- Events where relevant
- Example usage
- Developer notes
- Related components

Keep the tone descriptive and operational. These pages should explain how the component is used in the package experience, not just list `js-meta.xml` properties.

For standard component pages, use a structure like:

```md
# Component Name

Briefly explain what the component is for and where it is normally used.

---

## API Name
`componentApiName`

## Description
Short component summary.

---

## Exposure

Explain whether the component is exposed in App Builder, Flow, Experience Cloud, or only intended for embedding in another component.

---

## Public Properties

| Name | API Name | Data Type | Required | Description |
|------|------|------|------|------|
| Example Property | `exampleProperty` | String | No | Explain how callers use this property. |

---

## Behaviour Notes

| Area | Detail |
|------|------|
| Example area | Explain runtime behaviour or configuration impact. |

---

## Example Usage

Provide a short example when it helps the reader understand configuration or embedding.
```

If a section does not apply, omit it rather than inventing content.
