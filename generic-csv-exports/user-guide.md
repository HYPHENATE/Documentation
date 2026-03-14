# User Guide

Users generally interact with this package through the `CSV_Export__c` record and its associated automation.

In a typical export scenario, a user creates or updates a CSV Export record, sets the correct record type or configuration, and moves the status into a state that triggers the packaged automation.

The package then routes the request through a record-triggered flow and the relevant invocable Apex method for export or import processing.

Because the package is configuration-heavy, day-to-day users often rely on admins or technical owners to set up the metadata correctly before operational users begin running exports.
