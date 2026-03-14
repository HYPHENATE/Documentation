# How Generic CSV Exports Works

Generic CSV Exports combines configuration metadata, a runtime export record, record-triggered automation, and Apex processing classes.

The package is designed so that the shape of an export or import job comes from metadata rather than hardcoded field lists.

## Step 1 - Create Or Update A CSV Export Record

The process begins with a `CSV_Export__c` record, which acts as the operational control record for an export or import job.

## Step 2 - Trigger Packaged Automation

The active `CSV Export AU` record-triggered flow runs after update on `CSV_Export__c` when the status changes to `Import` or `Export`.

## Step 3 - Route To The Correct Invocable

The flow checks the current status and then calls either `CSVExport_ImportInvocable` or `CSVExport_ExportInvocable`.

## Step 4 - Use Metadata To Shape Processing

The invocable classes and helper layer retrieve the relevant custom metadata, such as export file definitions, file lines, and import mappings, based on the export record's record type or developer name.

## Step 5 - Run The Data Job

The package then uses helper and batch classes to process the import or export job and track its progress.

## Architecture Overview

The package separates operational execution from file-definition logic. The `CSV_Export__c` record controls when a job should run, while custom metadata controls what the job should do.

## Why This Approach Works

This approach allows teams to extend the framework to new CSV scenarios without rewriting the core processing pattern every time.
