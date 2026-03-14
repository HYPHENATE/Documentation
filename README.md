# Hyphen8 Accelerators Documentation

This site is the central documentation hub for the Salesforce accelerator packages held in this repository.

It brings together package-level guidance for shared technical foundations, reusable accelerators, and larger business-process solutions so teams can review architecture, installation steps, configuration notes, permissions, and support guidance in one place.

## What This Site Covers

The documentation is organised by package. Each package section is intended to give a consistent view of:

- what the package is for
- who it is aimed at
- how it is installed or deployed
- what the main data model and runtime components are
- what permissions, flows, or supporting assets matter

Some packages currently have deeper technical coverage than others. `Apex Tools`, `Simple Tags`, and `Dynamic Checks` are the strongest examples of the fuller documentation standard, while several larger packages are currently documented at a first-pass overview level and may be expanded further after review.

## How To Use This Site

Use the left-hand sidebar to browse packages alphabetically.

Within each package, start with:

1. `Introduction`
2. `Key Benefits`
3. `Installation` or deployment guidance
4. package-specific sections such as data model, classes, components, flows, and permissions

If you are reviewing a package for implementation, the most useful path is usually:

1. read the package introduction
2. check dependencies and install or deploy guidance
3. review the permissions model
4. review the relevant data model, automation, and UI sections

## Documentation Approach

This Docsify site is generated from markdown files stored in the repository under [`Documentation`](/d:/Accelerators/Documentation).

The documentation process in this repo uses:

- a reusable documentation template in [`Documentation/.template`](/d:/Accelerators/Documentation/.template)
- a package mapping file in [`docs-packages.json`](/d:/Accelerators/docs-packages.json)
- a canonical documentation prompt in [`prompt.md`](/d:/Accelerators/prompt.md)

That structure is there to keep formatting, naming, and package coverage as consistent as possible across the whole accelerator portfolio.

## Notes

- This site is intended as an internal or controlled documentation hub for this repository.
- Search-engine indexing is intentionally discouraged for the published Docsify site.
- Release-note handling is still being refined separately from the rest of the documentation standard.
