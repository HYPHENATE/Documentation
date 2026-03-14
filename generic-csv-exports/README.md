# Generic CSV Exports

[![Install for Production](https://img.shields.io/badge/Install-Production-1798c1?style=for-the-badge)](https://login.salesforce.com/packaging/installPackage.apexp?p0=04tQB000001N5w5YAC)
[![Install for Sandbox](https://img.shields.io/badge/Install-Sandbox-00a1e0?style=for-the-badge)](https://test.salesforce.com/packaging/installPackage.apexp?p0=04tQB000001N5w5YAC)

Generic CSV Exports is a configurable Salesforce package for exporting and importing CSV-style data using packaged metadata, invocable Apex, and batch processing patterns.

The package is designed to let teams define export file structures and import mappings in metadata rather than rebuilding one-off data utilities each time a new integration or operational data exchange is needed.

At a high level, users create or update a `CSV_Export__c` record, the package evaluates the selected status and record type, and then packaged automation runs the relevant import or export process.

The package README indicates that deeper package guidance currently lives in Quip, so this docs set focuses on the in-repo architecture and packaged assets while keeping that external-docs caveat visible.
