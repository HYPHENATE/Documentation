# CSV Export AU

## API Name
`CSV_Export_AU`

## Flow Type
`Record-Triggered Flow`

## Description

`CSV Export AU` is the packaged after-save flow that routes a `CSV_Export__c` record into either the import or export runtime path.

It is the automation bridge between the user-managed runtime record and the package Apex layer. The flow does not do the heavy lifting itself; instead, it evaluates the current status and then calls the appropriate invocable action.

---

## Launch Context

| Area | Detail |
|------|------|
| Trigger | After update on `CSV_Export__c`. |
| Users | Admins or operational users who update export records into an active processing status. |
| Entry Criteria | `Status__c` changes to `Import` or `Export`. |

---

## Flow Steps

### Step 1 - Start On CSV Export Update

The flow runs after a `CSV_Export__c` record is updated and only continues when the status changes into one of the processing values.

### Step 2 - Evaluate The Status

The `STATUS CHECK` decision determines whether the current run should follow the import path or the export path.

### Step 3 - Call The Correct Invocable

If the status is `Import`, the flow calls `CSVExport_ImportInvocable`. If the status is `Export`, it calls `CSVExport_ExportInvocable`. In both cases it passes the current record ID and the record type developer name.

---

## Inputs and Outputs

| Name | Direction | Type | Purpose |
|------|------|------|------|
| `recordId` | Input | Record Id | Identifies the `CSV_Export__c` record being processed. |
| `developerName` | Input | Text | Tells the invocable which metadata definitions to load for the current record type. |

---

## Data Impact

| Area | Detail |
|------|------|
| Objects | `CSV_Export__c` plus whichever objects are targeted by the configured import or export metadata. |
| Actions | Calls Apex invocables that either generate files or link records. |

---

## Operational Notes

| Topic | Detail |
|------|------|
| Status-driven routing | The flow uses the runtime record status as the switch between import and export logic. |
| Metadata-driven runtime | The record type developer name is critical because the Apex layer uses it to look up the matching metadata configuration. |

---

## Related Automation

- [CSVExport ExportInvocable](/generic-csv-exports/classes/csvexport-export-invocable)
- [CSVExport ImportInvocable](/generic-csv-exports/classes/csvexport-import-invocable)
