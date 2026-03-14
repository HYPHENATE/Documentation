# Configuration

Configuration is intentionally lightweight.

## Step 1 - Assign Permissions

Give editors the `Help Message Editor` permission set and standard end users the `Help Message Viewer` permission set.

## Step 2 - Create A Help Message

Create a `Help_Message__c` record, define the target object, enter the title and message text, and decide whether the message should apply to all records or only filtered records.

## Step 3 - Add Filters If Needed

If the message should only appear in certain situations, add one or more `Help_Message_Filter__c` child records and define the filter type on the parent message.

## Step 4 - Publish The Message

Use the message status to move content from draft to published when it is ready for wider visibility.

## Step 5 - Add The Component To Pages

Place the `helpMessage` LWC on the record pages where users should see the guidance.
