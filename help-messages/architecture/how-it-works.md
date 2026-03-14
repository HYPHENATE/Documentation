# How Help Messages Works

Help Messages uses a metadata-driven pattern to decide what guidance should appear on a record page.

At a high level, the package combines a configurable message object, an optional filter object, a record-page component, and Apex logic that evaluates the current record before returning only the relevant messages.

## Step 1 - Load The Record Context

The `helpMessage` Lightning Web Component loads on a Lightning record page and receives the current `recordId` and `objectApiName`.

## Step 2 - Retrieve Candidate Messages

`HelpMessageController` queries `Help_Message__c` for the current object type and limits visibility based on whether the current user should only see published content or can also see drafts.

## Step 3 - Evaluate Filters

Messages marked as valid for all records are returned immediately. Messages marked as filter-driven are passed to `HelpMessageHelper`, which dynamically queries the record and evaluates each related `Help_Message_Filter__c` condition.

## Step 4 - Return UI Payload

The controller returns a JSON payload containing the matching messages and the record fields the component should watch for changes.

## Step 5 - Render And Maintain The Experience

The component displays the messages on the record page and refreshes when watched record fields change or when an editor publishes or unpublishes a message.

## Architecture Overview

The package separates message configuration from message delivery. Admins manage reusable guidance records, while the Apex layer decides what applies to the current record and the component focuses on display and editor actions.

## Why This Approach Works

This approach keeps the package flexible. Organisations can tailor guidance by object, stage, status, or other field values without needing a custom component for every process variation.
