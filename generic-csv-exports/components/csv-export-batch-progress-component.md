# CSV Export Batch Progress Component

## API Name
`cSVExportBatchProgressComponent`

## Builder Name
`CSV Export Batch Progress Component`

## Description

This Lightning Web Component displays live batch progress for a `CSV_Export__c` record. It is intended for record pages where users need immediate feedback after triggering an import or export that runs asynchronously.

The component checks whether the current record type has any batch-enabled mappings, subscribes to the `/event/CSVExport_Event__e` channel when needed, and then updates the progress bar and status text as platform events arrive.

---

## Targets

- `lightning__RecordPage`

---

## Public Properties

| Name | API Name | Data Type | Required | Description |
|------|------|------|------|------|
| Record Id | `recordId` | String | Yes | The current `CSV_Export__c` record ID used to filter incoming platform events. |

---

## Behaviour Notes

| Area | Detail |
|------|------|
| Visibility | The component only displays itself when the Apex controller confirms that batch mode is configured for the current record type. |
| Event filtering | Incoming platform events are ignored unless their `CSVExportID__c` matches the current record. |
| Completion handling | The component shows a completion banner when the job status is `Completed`. |
| Error handling | The component shows the platform-event message when the job status is `Error`. |

---

## Example Usage

```html
<c-c-s-v-export-batch-progress-component record-id={recordId}></c-c-s-v-export-batch-progress-component>
```

---

## Developer Notes

| Topic | Detail |
|------|------|
| Event channel | The component subscribes to `/event/CSVExport_Event__e` using `lightning/empApi`. |
| Apex dependency | It calls `CSVExport_BatchProgressController.isCSVExportBatchEnabled` before subscribing. |
