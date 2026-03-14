# TagComponentHelper

## API Name
`TagComponentHelper`

## Description

`TagComponentHelper` is a VisualEditor dynamic picklist provider used by the SimpleTags component configuration experience.

It returns active tag categories as picklist rows, allowing builders and admins to choose from real tag category records when configuring components.

This is primarily a design-time helper rather than a runtime business logic class.

---

## Sharing Model
`inherited sharing`

## Tested By
`TagComponentHelperTest`

---

## Class Type

`TagComponentHelper` extends:

`VisualEditor.DynamicPickList`

This means it is intended for use in component metadata where a dynamic picklist data source is required.

---

## Overridden Methods

| Method | Returns | Purpose |
|------|------|------|
| `getDefaultValue()` | `VisualEditor.DataRow` | Returns the default value shown before options are loaded |
| `getValues()` | `VisualEditor.DynamicPickListRows` | Returns the active tag category options |

---

## Behaviour

`getValues()` queries active `Tag_Category__c` records and returns them as rows containing:

- display label = `Name`
- stored value = `Id`

This allows component configuration properties to surface current categories dynamically rather than relying on hardcoded values.

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `Tag_Category__c` | Source of active categories shown in the dynamic picklist |
| `VisualEditor.DynamicPickList` | Base class used for builder-time dynamic option generation |

---

## Typical Usage

This class is used where a component property needs a dynamic datasource such as:

```text
datasource="apex://TagComponentHelper"
```

That allows an admin configuring a component to select from live active tag categories.

---

## Important Notes

| Topic | Detail |
|------|------|
| Design-time helper | This class supports builder configuration, not end-user runtime operations |
| Active only | Only active categories are returned |
| Stored values | The picklist stores the category Id, not just the category name |

---

## Related Classes

- [TagHelper](/classes/tag-helper)
