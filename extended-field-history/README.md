# Extended Field History

[![Install for Production](https://img.shields.io/badge/Install-Production-1798c1?style=for-the-badge)](https://login.salesforce.com/packaging/installPackage.apexp?p0=04tQB000001LwRpYAK)
[![Install for Sandbox](https://img.shields.io/badge/Install-Sandbox-00a1e0?style=for-the-badge)](https://test.salesforce.com/packaging/installPackage.apexp?p0=04tQB000001LwRpYAK)

Extended Field History is a Salesforce auditing package for tracking changes beyond standard field history tracking limits.

The package uses custom metadata to define which objects and fields should be tracked and stores audit entries in a custom history object that can be surfaced through record pages, reports, and custom interfaces.

At runtime, tracked record changes are converted into `FieldAuditHistory__c` rows through an Apex trigger-handler pattern. That makes the package useful when teams need a configurable audit trail for fields that are not well covered by standard history tracking, want to keep the data for reporting, or need more control over how the audit history is displayed.

The package also includes control settings for whether audit rows can be edited or deleted, a packaged record-page component for viewing recent history, and a report pattern for seeing more than the latest on-screen entries.
