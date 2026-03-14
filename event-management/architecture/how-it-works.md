# How Event Management Works

Event Management combines a Salesforce event data model with Apex controllers, registration flows, and Lightning Web Components that power the attendee experience.

## Step 1 - Define Event Records

Teams configure `Event__c` and related ticket, role, registration, and settings records in Salesforce.

## Step 2 - Render Event Experiences

Packaged LWCs and controllers provide landing pages, event detail pages, favourites, ticket views, and registration interactions.

## Step 3 - Process Registrations

Registration flows and controller logic handle the submission and management of attendee registrations and related ticket allocations.

## Step 4 - Track Engagement

The package tracks views, favourites, registrations, and ticket records so teams can measure event activity and manage attendance.

## Architecture Overview

The package separates the administrative event model from the public or user-facing experience layer, while keeping both inside Salesforce.
