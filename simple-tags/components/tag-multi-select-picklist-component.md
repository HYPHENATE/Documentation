
# Flow Dynamic Picklist

The **SimpleTags (Multi-Select Picklist)** component provides a Flow-compatible interface for selecting tags using a **dual listbox**.

This component is designed for use within **Salesforce Flow screens** where users need to select one or more tags from a supplied list of available tags. It supports preselected values, validation, read-only mode, configurable labels, and output collections that make it easier to determine which tags need to be created or removed.

Rather than directly saving tag relationships itself, the component is intended to support **guided automation** by returning the selected tag IDs and the calculated differences between the original and updated selections.

This makes it especially useful in flows that need to:

- present a controlled list of tags to a user
- allow multi-select tag assignment
- compare current and new tag selections
- pass tag changes into downstream create or delete logic

---

## API Name
`SimpleTags (Multi-Select Picklist)`

## Builder Name
`tagMultiSelectPicklistComponent`

## Description
Component to display a multi-select picklist for tags.

---

## Targets

- `lightning__FlowScreen`

---

## Target Configs

### lightning__FlowScreen

| Name | API Name | Data Type | Default | Required | Description |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Available Tags (records) | `availableTags` | `{T[]}` |  | No | Record collection containing the available tags. Records should include at least `Id` and `Name`. |
| Current Tag Ids | `currentTagIds` | `String[]` |  | No | Collection of tag IDs that are currently selected before the user makes any changes. |
| Label | `label` | String | `Tags` | No | Label displayed above the dual listbox. |
| Remove Button Label | `removeButtonLabel` | String | `Remove` | No | Label used for the remove button in the dual listbox. |
| Add Button Label | `addButtonLabel` | String | `Add` | No | Label used for the add button in the dual listbox. |
| Source Label | `sourceLabel` | String | `Available Tags` | No | Label displayed for the list of available tags. |
| Selected Label | `selectedLabel` | String | `Selected Tags` | No | Label displayed for the list of selected tags. |
| Variant | `variant` | String | `label-stacked` | No | Controls the label display style. Supported values include `label-hidden`, `label-stacked`, and `label-inline`. |
| Required | `required` | Boolean | `false` | No | Determines whether at least one tag must be selected before moving forward in the flow. |
| Read Only | `readOnly` | Boolean | `false` | No | Prevents changes to the selected values when set to true. |
| Message When Value Missing | `messageWhenValueMissing` | String |  | No | Validation message shown when the component is required and no value has been selected. |
| Selected Tag Ids (computed) | `selectedTagIds` | `String[]` |  | No | Output-only collection of all currently selected tag IDs. |
| Tag Ids To Save (computed) | `tagsIdsToSave` | `String[]` |  | No | Output-only collection of tag IDs newly selected by the user that should be saved. |
| Tag Ids To Delete (computed) | `tagsIdsToDelete` | `String[]` |  | No | Output-only collection of tag IDs that were previously selected but have now been removed. |

---

## Behaviour Notes

| Area | Detail |
|--------------|--------------|
| Flow Only | This component is exposed only for use within Flow screens. |
| Source Records | The `availableTags` input should be a record collection with `Id` and `Name` values populated. |
| Preselection | Existing selections can be provided using the `currentTagIds` input collection. |
| Validation | If `required` is enabled, the component validates that at least one value has been selected before Flow can continue. |
| Read Only Mode | When `readOnly` is true, the dual listbox is displayed but cannot be edited. |
| Computed Outputs | The component automatically calculates which tag IDs need to be saved and which need to be deleted. |
| Reordering | Reordering is disabled so users can only move values between available and selected lists. |

---

## Input and Output Summary

| Type | Property | Purpose |
|--------------|--------------|--------------|
| Input | `availableTags` | Full list of tags that the user may choose from |
| Input | `currentTagIds` | Existing tag IDs already assigned |
| Output | `selectedTagIds` | Final selected tag IDs after user interaction |
| Output | `tagsIdsToSave` | New tag IDs that should be added |
| Output | `tagsIdsToDelete` | Existing tag IDs that should be removed |

---

## Example Configuration

| Setting | Example Value |
|--------------|--------------|
| Available Tags (records) | `Get_Tags_Collection` |
| Current Tag Ids | `varCurrentTagIds` |
| Label | `Tags` |
| Remove Button Label | `Remove` |
| Add Button Label | `Add` |
| Source Label | `Available Tags` |
| Selected Label | `Selected Tags` |
| Variant | `label-stacked` |
| Required | `true` |
| Read Only | `false` |
| Message When Value Missing | `Please select at least one tag.` |

---

## Example Flow Use Case

A flow might use this component in the following way:

1. Query all active `Tag__c` records to populate `availableTags`
2. Query existing `Tag_Link__c` records for the current record and pass their tag IDs into `currentTagIds`
3. Display the multi-select picklist to the user
4. Use `tagsIdsToSave` to create new `Tag_Link__c` records
5. Use `tagsIdsToDelete` to remove existing `Tag_Link__c` records that are no longer selected

This approach allows the flow to cleanly manage tag changes without needing to manually compare the old and new selections.

---

## Example Screen Configuration

This is an example of how the component might be configured within a Flow screen:

| Setting | Example |
|--------------|--------------|
| Label | `Programme Tags` |
| Source Label | `Available Programme Tags` |
| Selected Label | `Selected Programme Tags` |
| Required | `true` |
| Message When Value Missing | `At least one programme tag must be selected.` |
| Read Only | `false` |

---

## Example Developer Notes

| Topic | Detail |
|--------------|--------------|
| Record Shape | The component expects each input record to include `Id` and `Name`, though it also tolerates lowercase `id` and `name`. |
| Diff Logic | The component calculates `tagsIdsToSave` and `tagsIdsToDelete` by comparing the new selection with `currentTagIds`. |
| Flow Events | Output values are published back to Flow using `FlowAttributeChangeEvent`. |
| Validation Contract | The component implements `validate()` so Flow can enforce required selections during navigation. |

---

## Example Markup

```html
<template>
    <lightning-dual-listbox name="tags"
                            label={label}
                            disable-reordering="true"
                            disabled={readOnly}
                            remove-button-label={removeButtonLabel}
                            add-button-label={addButtonLabel}
                            source-label={sourceLabel}
                            selected-label={selectedLabel}
                            variant={variant}
                            required={required}
                            message-when-value-missing={messageWhenValueMissing}
                            options={options}
                            value={value}
                            onchange={handleChange}>
    </lightning-dual-listbox>
</template>
```