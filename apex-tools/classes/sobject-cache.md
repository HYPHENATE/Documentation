# SObjectCache

## API Name
`SObjectCache`

## Description

For retrieving and caching objects by name. On the first request, your object will be queried. On subsequent requests, it will be returned from the cache. So, you can freely call getObject() inside a loop (as long as the parameters don't change each time). NamedSObjectCache is particularly useful for metadata objects e.g. Record Types, or Case Milestone Types, etc.

---

## Sharing Model
`inherited sharing`

## Tested By
`SObjectCacheTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Primary purpose | For retrieving and caching objects by name. On the first request, your object will be queried. On subsequent requests, it will be returned from the cache. So, you can freely call getObject() inside a loop (as long as the parameters don't change each time). NamedSObjectCache is particularly useful for metadata objects e.g. Record Types, or Case Milestone Types, etc. |
| Utility behaviour | Provides reusable helper behaviour for Apex development and framework support. |
| Callable methods | Exposes 5 callable method(s) for package or implementation use. |

---

## Public/Internal Methods

| Method | Purpose |
|------|------|
| `getRecordType` | Returns or loads data used by the class. |
| `getNameKey` | Returns or loads data used by the class. |

---

## Important Notes

| Topic | Detail |
|------|------|
| Class Type | This Apex file is implemented as a `class`. |
| Package Role | `SObjectCache` is part of the ApexTools reusable framework and should be understood in the context of the wider package design. |
| Security Context | This class declares an explicit sharing model and should be used consistently with the package security standards. |
| Documentation Depth | This page is a generated overview and may be expanded later with deeper implementation notes if needed. |

---

## Related Classes

- [DescribeCache](./DescribeCache.md)
- [QueryBuilder](./QueryBuilder.md)
- [SObjectIndex](./SObjectIndex.md)
- [TypeLoader](./TypeLoader.md)
- [JSONParser](./JSONParser.md)
