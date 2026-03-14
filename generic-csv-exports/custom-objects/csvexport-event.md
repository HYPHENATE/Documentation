# CSVExport Event

## API Name
`CSVExport_Event__e`

## Description

The **CSVExport Event** platform event carries progress updates from the batch import and export processes to the record page user experience.

When a batch job starts, runs, completes, or errors, the package publishes this event with the current job details. The packaged Lightning Web Component listens to the `/event/CSVExport_Event__e` channel and uses the payload to update the progress bar and any completion or error messages.

---

## Fields

| Name | API Name | Data Type | Length/Options |
|------|------|------|------|
| BatchJobID | `BatchJobID__c` | Text | 255 |
| CSVExportID | `CSVExportID__c` | Text | 255 |
| Items Processed | `Items_Processed__c` | Number | 18,0 |
| Items To Process | `Items_To_Process__c` | Number | 18,0 |
| Job Status | `Job_Status__c` | Text | 255 |
| Job Type | `Job_Type__c` | Text | 255 |
| Message | `Message__c` | Text | 255 |

---

## Field Details

| Field | Purpose |
|------|------|
| BatchJobID | Identifies the async Apex job emitting the progress update. |
| CSVExportID | Identifies the `CSV_Export__c` record the event belongs to. |
| Items Processed | Tracks how many items the batch has processed so far. |
| Items To Process | Tracks the total number of items expected in the batch. |
| Job Status | Carries the current lifecycle status such as in progress, completed, or error. |
| Job Type | Distinguishes between import and export work. |
| Message | Carries the error or informational message shown to the user when needed. |
