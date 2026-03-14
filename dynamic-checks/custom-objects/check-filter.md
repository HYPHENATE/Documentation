# Check Filter

`Check_Filter__c` defines record-level conditions used to decide whether a filtered template header should apply.

## Purpose

It allows Dynamic Checks to show the right checklist at the right time rather than displaying every category on every record.

## Key Responsibilities

- stores the record field to inspect
- stores the comparison operator
- stores the comparison value
- links the condition back to a `Check_Template_Header__c`

## How It Works

When a template header is configured for filtered usage, `ChecksFilter` reads the related filter rows, queries the required record fields, and evaluates the configured conditions using the header's filter type.

## Typical Use

Use filters when a checklist should only appear for some records, such as a record type, stage, status, or amount threshold.
