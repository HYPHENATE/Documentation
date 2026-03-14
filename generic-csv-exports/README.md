# Generic CSV Exports

[![Install for Production](https://img.shields.io/badge/Install-Production-1798c1?style=for-the-badge)](https://login.salesforce.com/packaging/installPackage.apexp?p0=04tQB000001N5w5YAC)
[![Install for Sandbox](https://img.shields.io/badge/Install-Sandbox-00a1e0?style=for-the-badge)](https://test.salesforce.com/packaging/installPackage.apexp?p0=04tQB000001N5w5YAC)

Generic CSV Exports is a configurable Salesforce package for exporting and importing CSV-style data using packaged metadata, invocable Apex, and batch processing patterns.

The package is designed to let teams define export file structures and import mappings in metadata rather than rebuilding one-off data utilities each time a new integration or operational data exchange is needed. Instead of writing a bespoke controller for every file shape, admins can configure the runtime object, metadata definitions, and record-triggered automation once and then reuse the pattern.

At a high level, users create or update a `CSV_Export__c` record, the package evaluates the selected status and record type, and then packaged automation runs the relevant import or export process. Export scenarios use `CSV_Export_File__mdt` and `CSV_Export_File_Line__mdt` to define the output file structure, while import scenarios use `CSV_Import_Mapping__mdt` and related metadata to find and link source records.

The package also includes a progress-monitoring pattern for batch jobs. When batch mode is enabled in the metadata, Apex publishes `CSVExport_Event__e` platform events and the packaged Lightning component listens on the record page to show job progress, completion, or error messages.

The repo README indicates that deeper package guidance currently lives in Quip, so this docs set focuses on the in-repo architecture and packaged assets while keeping that external-docs caveat visible.
