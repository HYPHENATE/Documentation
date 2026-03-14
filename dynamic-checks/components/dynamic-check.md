# Dynamic Check

The **Dynamic Check** component is the internal UI component for one checklist item.

It allows users to complete a binary check, choose a custom answer value, and save optional comments, while keeping the individual record updates local to the checklist item itself.

This component is not intended for direct placement in App Builder. It is designed to sit inside the category renderer as the final interactive layer of the package.

---

## API Name
`dynamicCheck`

## Description
Internal component used to render and update a single checklist item.

---

## Exposure

This component is **not exposed directly in Lightning App Builder**.

```text
isExposed = false
```

It is intended to be embedded by `dynamicChecksCategory`.

---

## Public Properties

| Name | API Name | Data Type | Required | Description |
|------|------|------|------|------|
| Check | `check` | Object | Yes | A `Check` wrapper containing the `Check__c` row and related display metadata for one checklist item. |

---

## Expected Data Structure

The `check` input is expected to contain:

- `check` with the underlying `Check__c` record
- `helpText`
- `notRecordOwner`
- `allowComments`
- `customOptions`
- `customAnswers`

This structure comes from the Apex `Check` wrapper class returned by `ChecksHelper`.

---

## Behaviour Notes

| Area | Detail |
|------|------|
| Binary checks | Standard checks update `Checked__c` using a toggle-style interaction. |
| Custom-value checks | Custom checks render selectable options and save the chosen value to `CheckValue__c`. |
| Comment handling | Comments are edited separately and saved to `CheckComments__c`. |
| Completion logic | For custom display types, completion depends on whether the saved value appears in the configured valid-answer list. |
| Save mechanism | Uses Lightning Data Service `updateRecord` calls rather than custom Apex save methods. |
| Error handling | Dispatches toast messages when update operations fail. |

---

## Events

| Event | Description |
|------|------|
| `checkupdated` | Fired after a successful check, value, or comment update so parent components can refresh state. |

---

## Example Usage

This component is normally rendered inside a category component for each child check wrapper.

```html
<c-dynamic-check
    check={check}
    oncheckupdated={handleCheckUpdated}>
</c-dynamic-check>
```

---

## Developer Notes

| Topic | Detail |
|------|------|
| Record updates | The component updates `Checked__c`, `CheckValue__c`, and `CheckComments__c` independently depending on the user action. |
| Wrapper dependency | Expects `customOptions` and `customAnswers` to arrive pre-computed from Apex. |
| Parent refresh | The component does not reload checklist data itself; it relies on parent components to respond to the update event. |

---

## Related Components

- [Dynamic Checks Category](/dynamic-checks/components/dynamic-checks-category)
- [Dynamic Checks Container](/dynamic-checks/components/dynamic-checks-container)
