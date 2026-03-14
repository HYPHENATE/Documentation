# QueryBuilder

## API Name
`QueryBuilder`

## Description

Simplifies making dynamic queries by handling FieldSets, and sorting out sets of fields to remove duplicates

---

## Sharing Model
`inherited sharing`

## Tested By
`QueryBuilderTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Primary purpose | Simplifies making dynamic queries by handling FieldSets, and sorting out sets of fields to remove duplicates |
| Utility behaviour | Provides reusable helper behaviour for Apex development and framework support. |
| Callable methods | Exposes 6 callable method(s) for package or implementation use. |

---

## Public/Internal Methods

| Method | Purpose |
|------|------|
| `addFieldSet` | Supports internal or reusable behaviour within the class. |
| `setOrderByClause` | Stores configuration or context used later in processing. |
| `setPaginationClause` | Stores configuration or context used later in processing. |
| `setWhereClause` | Stores configuration or context used later in processing. |
| `addFields` | Supports internal or reusable behaviour within the class. |
| `getQuery` | Returns or loads data used by the class. |

---

## Important Notes

| Topic | Detail |
|------|------|
| Class Type | This Apex file is implemented as a `class`. |
| Package Role | `QueryBuilder` is part of the ApexTools reusable framework and should be understood in the context of the wider package design. |
| Security Context | This class declares an explicit sharing model and should be used consistently with the package security standards. |
| Documentation Depth | This page is a generated overview and may be expanded later with deeper implementation notes if needed. |

---

## Related Classes

- [DescribeCache](./DescribeCache.md)
- [SObjectIndex](./SObjectIndex.md)
- [TypeLoader](./TypeLoader.md)
- [JSONParser](./JSONParser.md)
