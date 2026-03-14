
# Tag Configuration Component

The **SimpleTags (Tag Configuration)** component is an administrative helper component used to configure which Salesforce objects a **Tag** can be applied to.

This component is intended to be placed on the **Tag record page** and is designed for internal users who manage and administer tags within the SimpleTags framework.

It provides a simple **dual listbox interface** allowing administrators to select the objects that a tag can be associated with. When selections change, the component automatically updates the **Available_Objects__c** field on the Tag record.

This configuration controls where the tag will be available within the tagging components across the system.

---

## API Name
`SimpleTags (Tag Configuration)`

## Builder Name
`tagObjectAvailableConfigurator`

## Description
This component is only to be used on the Tag record for internal users who can administer tags.

---

## Targets

- `lightning__RecordPage`

---

## Usage Context

This component should only be used on the **Tag (`Tag__c`) record page**.  
It allows administrators to define which objects support the selected tag.

Because this configuration affects the behaviour of the tagging framework, access should typically be restricted to **administrators or tag managers**.

---

## Behaviour Overview

| Area | Detail |
|------|------|
| Record Context | The component automatically loads the current Tag record using `recordId`. |
| Object Discovery | Available Salesforce objects are retrieved from the Apex method `TagHelper.availableObjectList`. |
| Configuration Storage | Selected objects are saved to the `Available_Objects__c` field on the Tag record. |
| Immediate Updates | Changes are saved automatically when the selection changes. |
| Loading State | A spinner is displayed while object options are retrieved. |
| Error Handling | Errors are surfaced using Lightning toast notifications. |

---

## Fields Used

| Field | API Name | Description |
|------|------|------|
| Tag Record Id | `Tag__c.Id` | The record currently being configured. |
| Available Objects | `Tag__c.Available_Objects__c` | Stores a comma-separated list of objects the tag can be used on. |

---

## Expected Data Format

The **Available_Objects__c** field stores object API names in a comma-separated format.

Example:

```
Account,Contact,Opportunity,Campaign
```

The component automatically converts this value into a list for display and reconverts it when saving updates.

---

## Component Interface

The component renders a **Lightning Dual Listbox** that allows administrators to:

- view available objects
- select objects the tag should apply to
- remove objects where the tag should not be available

| Element | Purpose |
|------|------|
| Dual Listbox | Displays available objects and selected objects |
| Spinner | Shown while object metadata is loading |
| Toast Notifications | Used to display configuration errors |

---

## Example Interface Behaviour

1. Administrator opens a **Tag record**.
2. The component loads available Salesforce objects.
3. The currently configured objects are preselected.
4. The administrator moves objects between lists.
5. The component automatically saves the update.

---

## Example Component Markup

```html
<template>
  <lightning-card>
    <div class="slds-var-p-horizontal_small">
      <template if:false={isLoaded}>
        <div class="slds-align_absolute-center" style="height:5rem">
          <lightning-spinner
              alternative-text={label.dualboxLoader} variant="brand">
          </lightning-spinner>
        </div>
      </template>
      <template if:true={isLoaded}>
        <lightning-dual-listbox name="selectObjects"
                            label={label.dualboxTitle}
                            source-label={label.dualboxSourceLabel}
                            selected-label={label.dualboxSelectedLabel}
                            field-level-help={label.dualboxHelpText}
                            options={options}
                            value={values}
                            disabled={disabled}
                            onchange={handleObjectSelection}>
        </lightning-dual-listbox>
      </template>
    </div>
  </lightning-card>
</template>
```

---

## Example Use Case

This component is typically used by administrators when:

- creating a new tag
- modifying existing tag configuration
- restricting tags to specific objects
- expanding tagging to additional Salesforce objects

For example:

| Tag | Available Objects |
|------|------|
| Programme Area | Account, Opportunity |
| Campaign Theme | Campaign |
| Supporter Interest | Contact |

---

## Apex Dependencies

The component relies on the following Apex method:

| Apex Class | Method | Purpose |
|------|------|------|
| `TagHelper` | `availableObjectList()` | Returns the list of Salesforce objects available for tagging. |

---

## Developer Notes

| Topic | Detail |
|------|------|
| Auto Save | Updates are triggered automatically when the selection changes. |
| Field Format | Objects are stored as a comma-separated string. |
| Record Loading | The component retrieves the Tag record using `lightning/uiRecordApi`. |
| Error Handling | Errors are displayed using `ShowToastEvent`. |

---

## Related Components

- Internal Component
- Experience Cloud Component
- Tag Browser Modal
- Flow Dynamic Picklist
- Read Only Component
