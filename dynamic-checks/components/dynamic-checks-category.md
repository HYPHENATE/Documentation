# Dynamic Checks Category

The **Dynamic Checks Category** component is the internal section renderer for one checklist category.

It displays the category name, description, completion state, and child check items, and it gives users a collapsible section-level view of progress within the broader checklist experience.

This component is intended to be used inside the main container rather than placed directly on a page.

---

## API Name
`dynamicChecksCategory`

## Description
Internal component used to render one checklist category and its child checks.

---

## Exposure

This component is **not exposed directly in Lightning App Builder**.

```text
isExposed = false
```

It is intended to be embedded by `dynamicChecksContainer`.

---

## Public Properties

| Name | API Name | Data Type | Required | Description |
|------|------|------|------|------|
| Category | `category` | Object | Yes | A `CheckCategory` wrapper containing the category metadata and child checks to render. |
| Expand Default | `expandDefault` | Boolean | No | Controls whether the category starts expanded or collapsed. |

---

## Expected Data Structure

The `category` input is expected to be a `CheckCategory` wrapper with values such as:

- `categoryName`
- `categoryDescription`
- `categoryOrder`
- `ownerEditOnly`
- `checks[]`

Each child entry in `checks[]` is expected to be a `Check` wrapper containing the live `Check__c` row and related display metadata.

---

## Behaviour Notes

| Area | Detail |
|------|------|
| Expand and collapse | Users can toggle the category open or closed using the section header action. |
| Progress calculation | Completion percentage is calculated by inspecting the child checks in the wrapper. |
| Custom answer handling | For custom display types, completion is based on whether the saved value appears in the wrapper's valid answer list. |
| Visual state | The component renders either a progress ring or a completed state depending on the completion outcome. |
| Event bubbling | Child `checkupdated` events are converted into a parent-facing `childcheckupdated` event. |

---

## Events

| Event | Description |
|------|------|
| `childcheckupdated` | Fired when a child check changes so the container can reload checklist data. |

---

## Example Usage

This component is normally embedded by the main container and receives one category wrapper at a time for rendering.

```html
<c-dynamic-checks-category
    category={category}
    expand-default={expandAllSections}
    onchildcheckupdated={handleChildCheckUpdated}>
</c-dynamic-checks-category>
```

---

## Developer Notes

| Topic | Detail |
|------|------|
| Data source | Expects the wrapper structure returned by `ChecksContainerController` and `ChecksHelper`. |
| Child composition | Renders `dynamicCheck` for each child checklist item in the category. |
| Progress logic | Recomputes completion state from client-side wrapper data rather than re-querying the server. |

---

## Related Components

- [Dynamic Checks Container](/dynamic-checks/components/dynamic-checks-container)
- [Dynamic Check](/dynamic-checks/components/dynamic-check)
