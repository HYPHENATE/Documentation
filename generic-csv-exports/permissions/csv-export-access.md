# CSV Export Access

## API Name
`CSV_Export_Access`

## Description

`CSV Export Access` is the packaged permission set that gives users access to the CSV Export app, the runtime `CSV_Export__c` object, the platform event used for progress monitoring, and the Apex classes that drive import and export processing.

It is the main permission set to assign to admins or operational users who need to create export records, trigger processing, and monitor results.

---

## Access Summary

| Area | Detail |
|------|------|
| App visibility | Grants visibility to the `CSV_Export` app. |
| Apex classes | Grants access to the packaged batch, helper, invocable, and controller classes. |
| Custom metadata | Grants read access to the metadata types used for export and import configuration. |
| Tab access | Makes the `CSV_Export__c` tab visible. |

---

## Object Permissions

| Object | Read | Create | Edit | Delete | Notes |
|------|------|------|------|------|------|
| `CSV_Export__c` | Yes | Yes | Yes | Yes | Users can create and manage the runtime export records. |
| `CSVExport_Event__e` | Yes | Yes | No | No | Supports batch progress monitoring through the platform event stream. |
| `Opportunity` | Yes | No | Yes | No | Supports the packaged example mapping that links opportunities to export records. |

---

## Field Permissions

| Field | Access | Purpose |
|------|------|------|
| `CSV_Export__c.ExportBatchId__c` | Read/Edit | Stores the current export batch job ID when batch processing is used. |
| `CSV_Export__c.Export_Date__c` | Read/Edit | Captures the operational export date. |
| `CSV_Export__c.ImportBatchId__c` | Read/Edit | Stores the current import batch job ID when batch processing is used. |
| `CSV_Export__c.Status__c` | Read/Edit | Lets users move the export record into the statuses that trigger package automation. |
| `Opportunity.CSV_Export__c` | Read/Edit | Supports the packaged example import-linking pattern. |

---

## Operational Notes

| Topic | Detail |
|------|------|
| Record types | The permission set includes visibility to the packaged `Example` record type on `CSV_Export__c`. |
| Target users | Best suited to admins, operations users, or integration owners who run or monitor CSV jobs. |
| Metadata setup | This permission set does not replace admin setup work; metadata still needs to be created or adapted for each real use case. |
