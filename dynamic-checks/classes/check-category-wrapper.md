# CheckCategory

## API Name
`CheckCategory`

## Description

`CheckCategory` is the wrapper class used to group related checks into one category for the Lightning UI.

It carries the category name, description, order, owner-edit setting, and child `Check` wrappers needed to render one section of the **Dynamic Checks** experience.

---

## Sharing Model
`Inherits caller context`

## Tested By
`ChecksHelperTest` (indirect coverage)

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Category grouping | Holds the checks that belong together under one configured checklist header. |
| Display metadata | Exposes the category label and description used by the UI. |
| Ordering | Carries the configured category order so sections render consistently. |
| Editability context | Exposes whether the category is subject to owner-only edit rules. |

---

## Public Properties

| Property | Type | Purpose |
|------|------|------|
| `categoryId` | `String` | Placeholder for a category identifier when needed by the UI. |
| `categoryName` | `String` | Category label shown to end users. |
| `categoryDescription` | `String` | Longer descriptive text shown in the category section. |
| `categoryOrder` | `Integer` | Display order used to sort categories on the record page. |
| `checks` | `List<Check>` | Child checklist items belonging to the category. |
| `ownerEditOnly` | `Boolean` | Indicates whether only the parent record owner should edit checks in this category. |

---

## Runtime Notes

| Area | Detail |
|------|------|
| UI payload role | This wrapper becomes one section in the `dynamicChecksCategory` component hierarchy. |
| Wrapper population | `ChecksHelper` creates and populates these wrappers when processing applicable template headers. |
| Completion display | The category component uses the child checks in this wrapper to calculate section completion progress. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `Check` | Provides the child checklist items rendered within the category. |
| `ChecksHelper` | Creates and populates wrapper instances. |
| `dynamicChecksCategory` | Consumes the wrapper data on the client side. |

---

## Typical Usage

This wrapper is returned to the main container component whenever the record page needs to render one checklist category and its checks.

---

## Related Classes

- [Check](/dynamic-checks/classes/check-wrapper)
- [ChecksHelper](/dynamic-checks/classes/checks-helper)
