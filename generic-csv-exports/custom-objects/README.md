# Data Model

Generic CSV Exports uses a mix of runtime records, custom metadata, and platform events.

The core packaged objects visible in source include:

- `CSV_Export__c`
- `CSVExport_Event__e`
- `CSV_Export_File__mdt`
- `CSV_Export_File_Line__mdt`
- `CSV_Import_Mapping__mdt`
- `CSV_Import_Mapping_Header__mdt`
- `CSV_Import_Mapping_Filter__mdt`

Together these objects define what should be exported or imported, how that job should be shaped, and how progress can be tracked.
