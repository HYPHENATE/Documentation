# ChecksFilter

`ChecksFilter` evaluates whether a filtered checklist header should apply to a record.

## Purpose

It reads the filter configuration rows attached to a header, queries the required fields on the target record, and then checks whether the record matches the configured conditions.

## Supported Behavior

- `AND` and `OR` style logic
- equality and inequality checks
- greater-than and less-than style numeric comparisons
- support for relationship field traversal in field references

## Operational Role

This class is what makes the package adaptable across processes. Without it, checklist categories would need to appear for every record of a given object.
