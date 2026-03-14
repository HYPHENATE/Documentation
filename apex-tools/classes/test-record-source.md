# TestRecordSource

## API Name
`TestRecordSource`

## Description

Main Test Data creation class To use (With Insert example): TestRecordSource testRecordSource = new TestRecordSource(); Lead testLead = (Lead) testRecordSource.getObject(Lead.SObjectType) .withInsert();

---

## Sharing Model
`inherited sharing`

## Tested By
`TestRecordSourceTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Primary purpose | Main Test Data creation class To use (With Insert example): TestRecordSource testRecordSource = new TestRecordSource(); Lead testLead = (Lead) testRecordSource.getObject(Lead.SObjectType) .withInsert(); |
| Test utility support | Supports reusable test setup, metadata-driven test data, or package testing helpers. |
| Callable methods | Exposes 19 callable method(s) for package or implementation use. |

---

## Public/Internal Methods

| Method | Purpose |
|------|------|
| `getGenerator` | Returns or loads data used by the class. |
| `createGenerator` | Creates records, outputs, or framework structures. |
| `getObjectWithoutInsert` | Returns or loads data used by the class. |
| `getObjectWithInsert` | Returns or loads data used by the class. |
| `getObject` | Returns or loads data used by the class. |
| `asVariant` | Supports internal or reusable behaviour within the class. |
| `useParameters` | Supports internal or reusable behaviour within the class. |
| `withInsert` | Supports internal or reusable behaviour within the class. |
| `withoutInsert` | Supports internal or reusable behaviour within the class. |
| `compare` | Supports internal or reusable behaviour within the class. |
| `getNextMetadataId` | Returns or loads data used by the class. |
| `addTemporaryMetadata` | Supports internal or reusable behaviour within the class. |
| `addTemporaryMetadataFields` | Supports internal or reusable behaviour within the class. |
| `addTemporaryMetadataFromInstance` | Supports internal or reusable behaviour within the class. |
| `getMetadataFields` | Returns or loads data used by the class. |
| `getCustomMetadataValue` | Returns or loads data used by the class. |
| `insertMetadataFieldsFromExample` | Performs insert behaviour or related write operations. |
| `getDeployContainerForMetadataFields` | Returns or loads data used by the class. |

---

## Important Notes

| Topic | Detail |
|------|------|
| Class Type | This Apex file is implemented as a `class`. |
| Package Role | `TestRecordSource` is part of the ApexTools reusable framework and should be understood in the context of the wider package design. |
| Security Context | This class declares an explicit sharing model and should be used consistently with the package security standards. |
| Documentation Depth | This page is a generated overview and may be expanded later with deeper implementation notes if needed. |

---

## Related Classes

- [TestRecordGenerator](./TestRecordGenerator.md)
- [TestFieldFunctions](./TestFieldFunctions.md)
