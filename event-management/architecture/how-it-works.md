# How Event Management Works

Event Management combines a Salesforce event data model with Apex controllers, registration flows, and Lightning Web Components that power the attendee experience.

## Step 1 - Define Event Records

Teams configure `Event__c` and related ticket, role, registration, and settings records in Salesforce.

## Step 2 - Render Event Experiences

Packaged LWCs and controllers provide landing pages, event detail pages, favourites, ticket views, and registration interactions. Most of the Apex controller layer returns structured JSON payloads that the frontend components render in Experience Cloud.

## Step 3 - Process Registrations

Registration flows and controller logic handle the submission and management of attendee registrations and related ticket allocations. The package supports both guest and logged-in registration paths, and the active flow determines what confirmation experience a registrant sees.

## Step 4 - Track Engagement

The package tracks views, favourites, registrations, and ticket records so teams can measure event activity and manage attendance.

## Architecture Overview

The package separates the administrative event model from the public or user-facing experience layer, while keeping both inside Salesforce. Custom objects store the event setup and engagement data, flows orchestrate registration, and LWCs plus Apex controllers power the attendee journey.

## Why This Approach Works

This approach lets organisations run event operations from Salesforce while still delivering a branded, package-supported front-end experience for attendees without building the entire event platform from scratch.
