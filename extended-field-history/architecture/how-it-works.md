# How Extended Field History Works

The package defines tracked fields in custom metadata, listens for relevant record changes, and writes audit rows into `FieldAuditHistory__c`.

## Step 1 - Configure The Tracking Rules

Admins define which objects and fields should be audited in `ExtendedFieldAuditHistory__mdt`, including whether created values, updated values, or both should be stored.

## Step 2 - Handle Record Changes

The package's trigger-handler pattern runs after inserts and updates on tracked records and determines which configured fields should be evaluated for the current object.

## Step 3 - Create Audit Records

When a tracked value is created or changed, the handler writes a `FieldAuditHistory__c` record containing the record ID, object name, field label, field API name, old value, new value, and change type.

## Step 4 - Protect Or Clean Up History

The package uses `FieldAuditHistoryTrigger` and `ExtendedFieldHistoryControl__c` to block edits or deletes when required, and uses a batch delete path to remove audit rows when the parent record is deleted.

## Step 5 - Surface The Audit Trail

Users review the most recent audit rows through the packaged `extendedFieldHistory` Lightning Web Component, which supports field and user filtering and can link out to the packaged report when more than the on-screen history limit is needed.

## Architecture Overview

The package separates tracking configuration, audit storage, governance controls, and UI presentation. Metadata decides what should be tracked, runtime classes create the history, control records govern whether the audit data can be changed, and the LWC provides a user-facing record view.

## Why This Approach Works

This approach gives organisations a configurable and reportable audit framework without having to hardcode field-specific tracking logic for every object they care about.
