# Apex Classes

This package contains a focused Apex orchestration layer rather than a large general-purpose library. The main runtime pattern centers on a few key groups:

- invocable classes that start import and export jobs
- helper and batch classes that perform the processing
- constants and data-factory utilities
- progress controllers for user feedback

Key entry points include:

- `CSVExport_ExportInvocable`
- `CSVExport_ImportInvocable`
- `CSVExport_ExportHelper`
- `CSVExport_ImportHelper`
- `CSVExport_ExportBatchable`
- `CSVExport_BatchProgressController`

The packaged docs below focus on the runtime classes that most clearly explain how the package works. Test support such as `CSVExport_DataFactory` and `CSVExport_Test` are intentionally kept as overview mentions rather than separate documentation pages.
