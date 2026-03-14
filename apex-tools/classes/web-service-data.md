# WebServiceData

## API Name
`WebServiceData`

## Description

Utility class for WebServices - holds Request / Response / JSON Data / Parameters

---

## Sharing Model
`without sharing`

## Tested By
`WebServiceDataTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Primary purpose | Utility class for WebServices - holds Request / Response / JSON Data / Parameters |
| Utility behaviour | Provides reusable helper behaviour for Apex development and framework support. |
| Callable methods | Exposes 13 callable method(s) for package or implementation use. |

---

## Public/Internal Methods

| Method | Purpose |
|------|------|
| `getRequest` | Returns or loads data used by the class. |
| `getResponse` | Returns or loads data used by the class. |
| `getResponseString` | Returns or loads data used by the class. |
| `getJSONBodyString` | Returns or loads data used by the class. |
| `getJSONBody` | Returns or loads data used by the class. |
| `setResponse` | Stores configuration or context used later in processing. |
| `setResponseBody` | Stores configuration or context used later in processing. |
| `setResponseStatusCode` | Stores configuration or context used later in processing. |
| `setResponseString` | Stores configuration or context used later in processing. |
| `setJSONBodyString` | Stores configuration or context used later in processing. |
| `setJSONBody` | Stores configuration or context used later in processing. |
| `setResponseHeaders` | Stores configuration or context used later in processing. |
| `isValidRecordId` | Checks whether a condition is true. |

---

## Important Notes

| Topic | Detail |
|------|------|
| Class Type | This Apex file is implemented as a `class`. |
| Package Role | `WebServiceData` is part of the ApexTools reusable framework and should be understood in the context of the wider package design. |
| Security Context | This class runs without sharing, so its use should be reviewed carefully in relation to data access and explicit access-mode design. |
| Documentation Depth | This page is a generated overview and may be expanded later with deeper implementation notes if needed. |

---

## Related Classes

- [DescribeCache](./DescribeCache.md)
- [QueryBuilder](./QueryBuilder.md)
- [SObjectIndex](./SObjectIndex.md)
- [TypeLoader](./TypeLoader.md)
- [JSONParser](./JSONParser.md)
