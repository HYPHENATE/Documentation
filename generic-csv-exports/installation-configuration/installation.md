# Installation

## Install Package

- Production: [Install Generic CSV Exports](https://login.salesforce.com/packaging/installPackage.apexp?p0=04tQB000001N5w5YAC)
- Sandbox: [Install Generic CSV Exports](https://test.salesforce.com/packaging/installPackage.apexp?p0=04tQB000001N5w5YAC)

## Prerequisites

- Decide which admins or users should have access to run and monitor CSV export jobs.
- Review any deeper package notes held in Quip before production rollout, as the repo README points there for additional documentation.

## Installation Steps

1. Install the package in the target org.
2. Assign the packaged `CSV_Export_Access` permission set to the relevant users.
3. Review the packaged metadata examples and confirm whether they match your intended import/export pattern.
4. Add the packaged progress component to the relevant record pages if required.
