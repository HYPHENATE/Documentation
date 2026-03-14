
# Tag Browser Modal

The **Tag Browser Modal** component is an internal helper component used to provide a searchable, filterable interface for browsing and updating tags on a record.

This component is designed to be embedded inside other Lightning Web Components rather than being placed directly on a Lightning page. It presents users with a modal-style experience for viewing all available tags, filtering them by category, searching by name, and saving changes back to the current record.

The component supports:

- searching tags by name
- filtering tags by category
- selecting and deselecting tags
- enforcing an optional selection limit
- saving updated tag selections through Apex
- displaying toast messages for validation and error handling

Because it is not exposed in App Builder, this component is primarily intended for use within the broader **SimpleTags** user experience.

---

## API Name
`tagBrowserModal`

## Description
Internal helper component used to browse, filter, and update tags within a modal interface.

---

## Exposure

This component is **not exposed directly in Lightning App Builder** and is intended for use **within other Lightning Web Components**.

```text
isExposed = false
```

This means the component is normally launched by a parent component that controls when the modal is shown and what data is passed into it.

---

## Public Properties

| Name | API Name | Data Type | Required | Description |
|--------------|--------------|--------------|--------------|--------------|
| Record Id | `recordId` | String | Yes | The Salesforce record Id that tag changes should be saved against. |
| Tags | `tags` | Array | Yes | Collection of tag objects available for display and selection in the modal. |
| Categories | `categories` | Array | No | Collection of category options used to populate the category filter picklist. |
| Selected Items | `selectedItems` | Array | No | Collection of currently selected tag IDs used to initialise the component state. |
| Selection Limit | `selectionLimit` | Number / String | No | Optional limit on the maximum number of tags that may be selected. |
| Show Modal | `showModal` | Boolean | No | Controls whether the component is visible. Defaults to `false`. |

---

## Expected Data Structure

### Tags

The `tags` input is expected to contain objects similar to the following:

```json
{
  "tagId": "a0123456789ABC",
  "tagName": "Programme Area",
  "category": "Classification",
  "selected": true
}
```

| Property | Description |
|--------------|--------------|
| `tagId` | Unique identifier for the tag |
| `tagName` | Display label shown in the table |
| `category` | Category name used for filtering |
| `selected` | Boolean value indicating whether the tag is currently selected |

### Categories

The `categories` input should follow the standard Lightning combobox option structure:

```json
[
  { "label": "All Programme Tags", "value": "Programme" },
  { "label": "Supporter Interest", "value": "Supporter Interest" }
]
```

### Selected Items

The `selectedItems` input should be an array of tag IDs:

```json
["a0123456789ABC", "a0123456789DEF"]
```

---

## Behaviour Notes

| Area | Detail |
|--------------|--------------|
| Modal Visibility | The component only renders when `showModal` is set to `true`. |
| Searching | Users can search tags by name using the search input. |
| Category Filtering | Users can restrict the visible tag list using the category combobox. |
| Reset | The reset action clears search terms, category filters, and temporary selection changes. |
| Save Behaviour | Changes are persisted by calling the Apex method `TagBrowserController.saveTagList`. |
| Selection Limits | If `selectionLimit` is set and exceeded, the component blocks save and displays an error toast. |
| Toast Messaging | Validation and save errors are surfaced using Lightning toast notifications. |
| Saving State | A spinner is shown while the save operation is in progress. |

---

## Events

The component dispatches custom events that allow a parent component to react to user actions.

| Event | Description |
|--------------|--------------|
| `close` | Fired when the modal is cancelled or closed without saving. |
| `save` | Fired after a successful save operation so the parent component can refresh its state. |

---

## Example Usage

A developer can embed this component inside a parent LWC and control its visibility and data inputs.

### Example HTML

```html
<template>
    <c-tag-browser-modal
        record-id={recordId}
        tags={availableTags}
        categories={categoryOptions}
        selected-items={selectedTagIds}
        selection-limit="5"
        show-modal={showTagBrowser}
        onclose={handleCloseTagBrowser}
        onsave={handleSaveTagBrowser}>
    </c-tag-browser-modal>
</template>
```

### Example JavaScript

```javascript
import { LightningElement, api, track } from 'lwc';

export default class CustomTagContainer extends LightningElement {
    @api recordId;

    @track showTagBrowser = false;
    @track selectedTagIds = ['a01XXXXXXX1'];
    @track availableTags = [
        { tagId: 'a01XXXXXXX1', tagName: 'Programme Area', category: 'Classification', selected: true },
        { tagId: 'a01XXXXXXX2', tagName: 'Campaign Type', category: 'Fundraising', selected: false }
    ];

    categoryOptions = [
        { label: 'Classification', value: 'Classification' },
        { label: 'Fundraising', value: 'Fundraising' }
    ];

    handleCloseTagBrowser() {
        this.showTagBrowser = false;
    }

    handleSaveTagBrowser() {
        this.showTagBrowser = false;
        // refresh record tags here
    }
}
```

---

## Save Logic

When the user clicks **Save**, the component sends the selected tag IDs to Apex using:

```javascript
saveChanges({
   recordId: this.recordId,
   tagIds: this.newSelectedItems
})
```

If the save is successful, the component:

1. Resets its internal filter and selection state
2. Hides the saving spinner
3. Dispatches the `save` event to the parent component

If an error occurs, the component displays a toast notification.

---

## Filtering Logic

The component supports three filtering modes:

| Filter Type | Behaviour |
|--------------|--------------|
| Search Only | Filters tags where `tagName` contains the entered search term |
| Category Only | Filters tags where `category` matches the selected category |
| Search + Category | Filters tags where both conditions are true |

This gives users a quick way to browse large tag sets when many tags are available.

---

## Example Interface Elements

The component includes the following interface controls:

- search input for tag names
- category filter dropdown
- reset button
- table of available tags
- checkbox-button selection control
- save and cancel actions
- loading spinner during save

---

## Example Markup

```html
<template>
    <template if:true={showModal}>
        <lightning-card title={label.modalTitle}>
            <lightning-button-group slot="actions">
                <lightning-button label={label.cancelButtonLabel}
                                    data-id="cancelBtn"
                                    onclick={handleCloseModal}
                                    aria-label={label.ariaLabelCancelButton}
                                    disabled={isSaving}>
                </lightning-button>
                <lightning-button label={label.saveButtonLabel}
                                    data-id="saveBtn"
                                    variant="brand"
                                    onclick={handleSaveModal}
                                    aria-label={label.ariaLabelSaveButton}
                                    disabled={isSaving}>
                </lightning-button>
            </lightning-button-group>
            <!-- additional modal content omitted for brevity -->
        </lightning-card>
    </template>
</template>
```

---

## Developer Notes

| Topic | Detail |
|--------------|--------------|
| Parent Control | A parent component should manage when the modal opens and closes. |
| Initial Selection | Use `selectedItems` to preselect tags already assigned to the record. |
| Tag Updates | The component tracks changes separately in `newSelectedItems` before saving. |
| Reusability | This component is designed to be reused in any interface that needs a full tag browsing experience. |
| Apex Dependency | Saving depends on the `TagBrowserController.saveTagList` Apex method being available. |

---

## Related Components

- Internal Component
- Experience Cloud Component
- Read Only Component
- Flow Dynamic Picklist
