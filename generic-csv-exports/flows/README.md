# Flows

The package includes one main packaged flow:

- `CSV_Export_AU`

This is an active after-save record-triggered flow on `CSV_Export__c` that decides whether the package should run the import or export invocable path based on the current status value.
