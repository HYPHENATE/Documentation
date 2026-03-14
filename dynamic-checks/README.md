# Dynamic Checks

[![Install (Production)](https://img.shields.io/badge/Install-Production-blue)](https://login.salesforce.com/packaging/installPackage.apexp?p0=04tQB000001N5srYAC)
[![Install (Sandbox)](https://img.shields.io/badge/Install-Sandbox-lightblue)](https://test.salesforce.com/packaging/installPackage.apexp?p0=04tQB000001N5srYAC)

Dynamic Checks is a configurable checklist framework for Salesforce. It lets teams define reusable check templates, decide when those checks should appear on a record, and present them in Lightning components that users can complete as part of day-to-day operational work.

Instead of hardcoding process guidance into one object or one screen, the package stores checklist design in Salesforce data. That makes it easier to roll out repeatable operational controls across multiple teams and objects while still allowing local variation through filters, categories, and optional automation.

## Who This Is For

This package is intended for Salesforce admins, solution architects, and operational teams who need structured task completion on records without building separate custom apps for each process.

## Why This Package Exists

Many nonprofit teams need staff to complete the same sequence of checks at important points in a process, but the right checklist often depends on the record type, stage, owner, or related data.

Examples include:

- grant teams validating applications before review
- fundraising teams checking gift processing or due diligence steps
- programme teams confirming onboarding, safeguarding, or case handover actions
- finance or operations teams tracking approval readiness on key records

Dynamic Checks addresses that by combining:

- template-driven checklist design
- record-level filtering
- Lightning UI for completion and progress tracking
- optional flow launching when a check is completed

## Documentation Structure

Use the supporting folders in this section to review the package by topic:

- architecture pages explain how templates become live checks
- installation and configuration pages describe setup and rollout
- custom object pages explain the data model
- class and component pages explain the runtime behavior
- permissions pages describe admin and end-user access
