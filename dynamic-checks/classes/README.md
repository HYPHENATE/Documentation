# Apex Classes

This section documents the main production Apex classes used by the **Dynamic Checks** package.

The package uses a small set of focused runtime classes to support:

- loading and creating live checks for a record
- evaluating metadata-driven filter criteria
- exposing checklist data to Lightning Web Components
- launching post-completion flows
- shaping UI-friendly wrapper payloads
- centralising package constants

Test classes are not documented as separate pages in this section. Instead, each production class includes the most relevant test coverage reference where practical.

---

## Class Overview

| Class | Purpose | Tested By |
|------|------|------|
| [ChecksContainerController](/dynamic-checks/classes/checks-container-controller) | Aura-enabled entry point that loads checklist categories and checks for the current record | `ChecksContainerControllerTest` |
| [ChecksHelper](/dynamic-checks/classes/checks-helper) | Core orchestration class that determines valid checklist categories, creates missing checks, and builds wrapper payloads | `ChecksHelperTest` |
| [ChecksFilter](/dynamic-checks/classes/checks-filter) | Evaluates `Check_Filter__c` conditions against a target record to decide whether filtered headers apply | `ChecksHelperTest` |
| [CheckLaunchFlow](/dynamic-checks/classes/check-launch-flow) | Trigger handler that launches configured autolaunched flows when completed checks require follow-on automation | `CheckLaunchFlowTest` |
| [Check](/dynamic-checks/classes/check-wrapper) | Wrapper class that packages a `Check__c` record with extra UI metadata such as help text and custom answer details | Indirectly covered by `ChecksHelperTest` |
| [CheckCategory](/dynamic-checks/classes/check-category-wrapper) | Wrapper class that groups checks into UI categories with description, order, and owner-edit settings | Indirectly covered by `ChecksHelperTest` |
| [ChecksConstants](/dynamic-checks/classes/checks-constants) | Shared constant values for record applicability, filter logic, operators, and delimiters | `ChecksConstantsTest` |

---

## Design Notes

| Area | Detail |
|------|------|
| Metadata-driven runtime | `Check_Template_Header__c`, `Check_Template__c`, and `Check_Filter__c` drive what checklist content appears for each record. |
| Wrapper-based UI payloads | Apex returns `CheckCategory` and `Check` wrapper objects so the LWC layer can render the experience without rebuilding package logic client-side. |
| Record creation strategy | Missing `Check__c` rows are created on demand when a record qualifies for a checklist category. |
| Filter evaluation | Record-level applicability is determined dynamically from filter metadata rather than hardcoded business rules. |
| Flow integration | Completed checks can trigger autolaunched flows through the `CheckLaunchFlow` handler when templates are configured to do so. |
