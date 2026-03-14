# Apex Classes

Add one markdown file per important production Apex class or logical class group.

Use the richer class-page structure already established in `Documentation/simple-tags/classes`.

Test classes are normally not documented as separate pages. Instead, capture the test class name on the production class page.

Suggested content for each page:

- Title
- API Name
- Description
- Sharing Model
- Tested By
- Key Responsibilities
- Public methods, AuraEnabled methods, invocable methods, or other main entry points as relevant
- Internal methods when they are important to understanding behaviour
- Response behaviour, security model, metadata usage, or runtime notes where relevant
- Dependencies
- Typical usage
- Related classes

Keep the tone descriptive and implementation-aware. These pages should explain what the class does in the package architecture, not just restate method names.

For standard Apex class pages, use a structure like:

```md
# Class Name

## API Name
`ClassName`

## Description

Explain what the class is for, where it sits in the package design, and when it is called.

---

## Sharing Model
`with sharing`

## Tested By
`ClassNameTest`

---

## Key Responsibilities

| Responsibility | Detail |
|------|------|
| Example responsibility | Explain what this part of the class is responsible for. |

---

## Public Methods

| Method | Returns | Purpose |
|------|------|------|
| `exampleMethod()` | `String` | Explain what the method does and why callers use it. |

---

## Dependencies

| Dependency | Purpose |
|------|------|
| `ExampleDependency` | Explain why this dependency matters. |

---

## Typical Usage

Explain how the class is usually invoked in practice.

---

## Related Classes

- [RelatedClass](/classes/related-class)
```

If a section is not relevant for a class, omit it rather than inventing content.
