# CheckLaunchFlow

`CheckLaunchFlow` is the flow-launch integration class for Dynamic Checks.

## Purpose

It runs after update on `Check__c` and launches a configured autolaunched flow when a check is completed and the relevant launch setting is enabled.

## How It Is Triggered

- `CheckTrigger` delegates to `MetaTriggerManager`
- a packaged `Trigger_Handler` custom metadata record points `AFTER_UPDATE` on `Check__c` to `CheckLaunchFlow`

## Variable Translation

Before launching the flow, the class translates:

- `$recordId` to the `Check__c` record ID
- `$parentId` to the parent business record ID

## Risks to Watch

- invalid JSON in `Flow_Input_Variables__c`
- incorrect flow API names
- flows being used for routine actions that do not justify the added complexity
