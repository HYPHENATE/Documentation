# User Guide

Users generally interact with this package through the `CSV_Export__c` record and its associated automation.

In a typical export scenario, an admin or configured user creates a `CSV_Export__c` record, chooses the correct record type, and updates the `Status__c` field to `Export`. The packaged flow then calls the export invocable, which reads the matching `CSV_Export_File__mdt` and `CSV_Export_File_Line__mdt` records, queries the target data, and generates a CSV file against the export record.

In an import scenario, the same runtime record is moved to `Import`. The flow then calls the import invocable, which reads the configured `CSV_Import_Mapping__mdt` and `CSV_Import_Mapping_Filter__mdt` metadata, builds the matching SOQL query, and links the qualifying records back to the current export record through the configured mapping field.

Where metadata enables batch processing, users can monitor progress on the export record page through the packaged `cSVExportBatchProgressComponent`. That component subscribes to `CSVExport_Event__e` events so users can see processed item counts, final completion, and any runtime error messages without opening Apex Jobs directly.

Because the package is configuration-heavy, day-to-day users often rely on admins or technical owners to set up the metadata correctly before operational users begin running exports or imports.
