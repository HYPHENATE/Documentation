# Installation

## Install Package

- Production: [Install Help Messages](https://login.salesforce.com/packaging/installPackage.apexp?p0=04tQB000001gIXpYAM)
- Sandbox: [Install Help Messages](https://test.salesforce.com/packaging/installPackage.apexp?p0=04tQB000001gIXpYAM)

## Prerequisites

- My Domain should be enabled in the target org.
- Decide which users will manage messages and which users only need to view them.

## Installation Steps

1. Install the package in the target org using the production or sandbox link above.
2. Assign `Help Message Editor` to users who will create, publish, or maintain messages.
3. Assign `Help Message Viewer` to users who should only see messages on records.
4. Add the `helpMessage` component to the relevant Lightning record pages.

## Post-Install Outcome

After installation, the org will have the packaged objects, component, path, permission sets, and support metadata needed to start configuring contextual help messages.
