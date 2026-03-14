# ApexTools Coding Standards

This document sets out the coding standards for `ApexTools`.

It serves two purposes:

- to reflect the style and structure already used across the package
- to remind developers of the secure coding and maintainability standards expected for future work

This is not intended to be a generic Apex style guide.  
It is specifically aimed at people contributing to `ApexTools` or building extensions that follow the same patterns.

---

## Core Principles

Code added to `ApexTools` should aim to be:

- clear to read
- safe by default
- bulk-safe
- testable
- well documented
- explicit about security context
- consistent with the existing package structure

Where there is a trade-off between cleverness and maintainability, prefer maintainability.

---

## 1. Document Classes and Methods Clearly

`ApexTools` already uses header comments and method descriptions extensively, and that should continue.

### Class Header Standard

Each significant class should include a header block similar to:

```apex
/**
 * @description  : Short explanation of what the class does
 * @author       : name@example.com
 * @created      : DD/MM/YYYY
**/
```

If a class has been materially changed, an additional `@last modified` note can be added where helpful, but the format should stay lightweight and readable.

### Method Documentation Standard

Public, global, protected, and non-trivial private methods should include a short description of:

- what the method does
- important parameters
- return value, where useful

Example:

```apex
/**
* @description Return a set of pick list values
* @param sObjectType
* @param fieldName
* @return List<String>
**/
```

### Documentation Expectations

- Document intent, not the obvious mechanics of each line.
- Be especially clear on utility classes, dynamic behaviour, metadata-driven logic, and security-sensitive code.
- If a method has side effects, say so.
- If a class is only present to support tests, say that explicitly.

---

## 2. Use Explicit Sharing and Access Context

Every class should explicitly declare its execution context.

Use one of:

- `with sharing`
- `without sharing`
- `inherited sharing`

Do not leave sharing unspecified.

### General Guidance

- Use `with sharing` when business logic should respect the caller's record-level access.
- Use `inherited sharing` when the class should follow the context of the calling code and remain flexible for reuse.
- Use `without sharing` only where there is a clear and justified reason, such as platform utility behaviour, administrative actions, or framework code that must run outside record-sharing rules.

If `without sharing` is used, the reason should be obvious from the class purpose or explained in comments.

---

## 3. Prefer Modern Data Access Controls

This package is being updated to use modern Apex data-access controls.

### Query Standard

For new code, prefer:

- `WITH USER_MODE` where queries should respect user permissions
- `WITH SYSTEM_MODE` where system-level access is explicitly intended and appropriate

`WITH SECURITY_ENFORCED` should be treated as legacy usage within older package code, not the target pattern for new work.

### DML Standard

For DML, be explicit about the intended access context by using:

- `insert as user`
- `update as user`
- `delete as user`
- `Database.insert(records, AccessLevel.USER_MODE)`
- `Database.update(records, AccessLevel.SYSTEM_MODE)`

Choose the access level deliberately rather than relying on implicit defaults.

### Design Rule

Developers should always be able to answer:

- should this operation respect the running user's CRUD/FLS and sharing context?
- or is this framework operation intentionally running in system context?

If the answer is not clear, the code probably needs refactoring or additional documentation.

---

## 4. Treat Security as a Design Requirement

Security should not be something added later.

When writing Apex for this package, always consider:

- record access
- object permissions
- field permissions
- safe handling of dynamic SOQL
- safe handling of dynamic type loading
- safe handling of external input

### Secure Coding Expectations

- Do not assume caller access is appropriate unless the class is explicitly designed that way.
- Be cautious with `without sharing`, dynamic DML, and dynamic SOQL.
- Validate all externally supplied values before using them in queries or DML.
- Limit dynamic behaviour to controlled and well-documented cases.
- Prefer allowlisted metadata-driven patterns over arbitrary user-supplied class names or field names.

---

## 5. Bulkify Everything

All package code should be safe to run against:

- one record
- many records
- batch contexts
- Flow-driven collections

### Required Practices

- Never assume a trigger or invocable method will receive only one record.
- Avoid SOQL and DML inside loops unless there is a very specific and documented reason.
- Build collections first, then query or perform DML once where possible.
- Design utility code to accept collections, not just single records.

### Expected Patterns

- use `List`, `Set`, and `Map` heavily
- collect IDs before querying
- process results in bulk
- use batchable or queueable patterns for larger workloads where appropriate

---

## 6. Keep Triggers Thin

Trigger logic should stay minimal.

In `ApexTools`, the preferred pattern is:

- one trigger per object
- trigger delegates immediately to a handler framework
- object-specific behaviour lives in handler classes
- trigger routing is configuration-driven where possible

Example:

```apex
trigger ContactTrigger on Contact (
    before insert, before update, before delete,
    after insert, after update, after delete, after undelete
) {
    (new MetaTriggerManager(Contact.SObjectType)).handle();
}
```

### Trigger Rules

- Do not put substantial business logic directly in triggers.
- Do not duplicate object event routing logic across multiple triggers.
- Keep trigger code readable enough that another developer can understand the entry point immediately.

---

## 7. Use Metadata-Driven Patterns Where They Add Value

`ApexTools` makes extensive use of custom metadata to control framework behaviour.

This is a preferred pattern when:

- administrators or implementers may need to adjust behaviour without code changes
- behaviour differs by object, role, variant, or process type
- the same framework needs to be reused across multiple org scenarios

Examples in this package include:

- trigger routing
- logging configuration
- sharing configuration
- test record generation
- sandbox data setup

### Guidance

- Use metadata when configurability improves reuse and maintainability.
- Do not introduce metadata purely for the sake of abstraction.
- Keep metadata models understandable and purposeful.

---

## 8. Use PMD Thoughtfully, Not Blindly

PMD warnings should be taken seriously, but not followed mechanically.

### General Rule

- Code should normally comply with PMD rules.
- Suppressions are allowed when there is a legitimate reason.
- Suppressions should be as narrow as possible.

Examples already used in the package include:

- `PMD.CognitiveComplexity`
- `PMD.ApexCRUDViolation`
- `PMD.ApexSOQLInjection`
- `PMD.AvoidGlobalModifier`
- `PMD.OperationWithLimitsInLoop`

### Suppression Standard

If a rule is suppressed:

- the suppression should be local where possible
- the developer should understand why the warning is being suppressed
- the code should still be reviewed for the underlying risk

Examples:

- suppress `PMD.CognitiveComplexity` only when the logic is genuinely necessary and still understandable
- suppress `PMD.ApexSOQLInjection` only when the query is dynamic but the inputs are controlled and safe
- suppress `PMD.ApexCRUDViolation` only when the security model is intentionally handled through explicit access context or framework design

Do not use `@SuppressWarnings('PMD')` broadly unless there is a very strong reason.

---

## 9. Prefer Readable Dynamic Apex

This package contains dynamic Apex utilities, but dynamic behaviour should still be easy to follow.

### Dynamic SOQL

When writing dynamic queries:

- keep query assembly structured
- avoid concatenating untrusted input
- separate query-building concerns into dedicated methods where possible
- comment on unusual assumptions

### Dynamic Type Loading

When loading classes dynamically:

- prefer class names sourced from trusted metadata
- fail clearly if a configured class cannot be found
- document expected interfaces or base classes

### Reflection and Metadata

Dynamic behaviour is powerful, but it increases maintenance risk.  
Use it where it creates real reuse, not where a static solution would be clearer.

---

## 10. Naming Should Be Descriptive and Predictable

Names should prioritise clarity over brevity.

### Class Naming

- Use names that describe the role of the class clearly.
- For handlers, use names that indicate both object and purpose where relevant.
- For framework support classes, keep names generic but precise.

Examples from this package:

- `MetaTriggerManager`
- `ApexLogger`
- `ShareObjectCreate`
- `PostCopySandboxDataGenerator`
- `TestRecordSource`

### Method Naming

- Methods should read like actions or clear queries.
- Boolean-returning methods should read like checks, for example `isValidLogger`.
- Builder-style methods should use consistent naming such as `setX`, `withX`, or `asVariant`.

### Variable Naming

- Use complete names unless the shorter version is genuinely standard and clearer.
- Avoid vague names such as `obj`, `temp`, or `data` unless the scope is tiny and obvious.

---

## 11. Handle Errors Intentionally

Errors should not disappear silently.

### Expectations

- Catch exceptions only when you can add value.
- Either rethrow, log, convert, or deliberately handle the failure.
- Use package logging where appropriate for operational traceability.
- Prefer specific exception handling patterns over broad silent catches.

### Good Practice in ApexTools

- framework code should fail clearly when metadata or configured classes are invalid
- operational processes should log meaningful error detail where that helps support teams
- helper methods should avoid swallowing exceptions unless there is a documented fallback behaviour

---

## 12. Tests Are Required, Not Optional

Every meaningful code change should include or update tests.

### Test Expectations

- cover the happy path
- cover likely failure paths
- cover security-sensitive or metadata-driven behaviour where practical
- verify outcomes, not just line coverage

### Package-Aligned Practices

- use `TestRecordSource` where it improves consistency
- use temporary metadata in tests when package metadata should not be hardcoded into the test
- create focused test methods with clear setup and assertions

### Good Test Design

- tests should explain the scenario through method names and assertions
- avoid unnecessary data setup
- keep each test focused on one behaviour where possible

---

## 13. Keep Public and Global APIs Stable

Because `ApexTools` is a reusable package, public and global code should be treated carefully.

### Rules

- avoid changing method signatures unless necessary
- avoid renaming public or global types casually
- preserve backwards compatibility where reasonable
- document intentional breaking changes clearly

`global` should be used only where packaging or external access truly requires it.

If `global` is used, the API should be designed deliberately because it is harder to change later.

---

## 14. Format Consistently

The repository already includes Prettier support, including Apex formatting.

### Formatting Rule

Before finalising changes, code should be formatted consistently with the repository tooling.

Relevant scripts include:

```bash
npm run prettier
npm run prettier:verify
```

Formatting should not be debated in code review unless something is genuinely unclear or misleading.

---

## 15. Review Checklist

Before submitting code, developers should check:

- Is the class or method documented clearly?
- Is the sharing model explicit?
- Is query access mode chosen intentionally?
- Is DML access mode chosen intentionally?
- Is the code bulk-safe?
- Are PMD suppressions justified and narrow?
- Is dynamic SOQL or dynamic Apex safe and controlled?
- Are exceptions handled clearly?
- Are tests included or updated?
- Does the code match the package's existing style and naming patterns?

---

## Recommended Defaults

If unsure, use these defaults:

- prefer `with sharing` or `inherited sharing` over `without sharing`
- prefer `WITH USER_MODE` unless system-mode access is intentionally required
- prefer explicit DML access levels rather than implicit behaviour
- prefer metadata-driven configuration for reusable framework behaviour
- prefer thin triggers and handler classes
- prefer readable code over compressed code
- prefer targeted PMD suppressions over broad suppressions
- prefer package logging for operational failures that support teams may need to investigate

---

## Final Note

`ApexTools` is a foundation package.  
That means code quality standards matter more than they might in one-off project code, because every design decision here is likely to be reused.

The goal is not only to make code work.  
The goal is to make it safe, maintainable, understandable, and reusable across implementations.