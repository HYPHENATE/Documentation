# Configuration

Configuration in this package is primarily metadata-driven.

## Step 1 - Review Export File Metadata

Use `CSV_Export_File__mdt` and `CSV_Export_File_Line__mdt` to define the file structure, header, output fields, and line ordering for export scenarios.

## Step 2 - Review Import Mapping Metadata

Use `CSV_Import_Mapping__mdt`, `CSV_Import_Mapping_Header__mdt`, and `CSV_Import_Mapping_Filter__mdt` to define how import jobs should identify and link records.

## Step 3 - Configure Export Record Usage

Confirm the record types and statuses used on `CSV_Export__c`, since the packaged flow routes processing based on the current status and record type developer name.

## Step 4 - Validate With Example Metadata

The package includes example metadata based on opportunity exports and imports. Use those as starting references before introducing production-specific mappings.
