# Installation

## Salesforce Requirements  
There are no Salesforce requirements for this installation, the package is designed to work in old and new environments.

## Prerequisites  
- Enable Path https://help.salesforce.com/s/articleView?id=sf.path_enable.htm&type=5   
- ApexTools (introduced v1.6.1) 

## Installation
Install the package using the appropriate link below  

> [![Install (Production)](https://img.shields.io/badge/Install-Production-blue)](https://login.salesforce.com/packaging/installPackage.apexp?p0=04tQB0000028ih3YAA)
> [![Install (Sandbox)](https://img.shields.io/badge/Install-Sandbox-lightblue)](https://test.salesforce.com/packaging/installPackage.apexp?p0=04tQB0000028ih3YAA)

## Installation Permissions
Always set this to be Administrators only then post installation during configuration you can apply permission sets to users.

## Important Upgrade Instructions  

### Upgrading from <=1.6.0 to >=1.6.1 
- If you are upgrading from version 1.6 or lower you now have to have installed Apex Tools

### Upgrading from < v1 to 1.6.0 
Due to a known issue with Unlocked packages when upgrading from v1 you need to perform the following steps as a part of the upgrade.  
- Go to Tag Object  
- Go to Fields & Relationships  
- Select Status  
- Add a new Picklist Value Requested  
- Update the Order 
    - Requested  
    - Inactive 
    - Active  
- Set default to Inactive