# TestingFlow

## Purpose

`TestingFlow` is an autolaunched flow included for test support. The source metadata description states that it is used as part of the package test suite and should not be deleted.

## Launch Method

It can be launched through the Dynamic Checks flow-launch pattern when a completed check is configured to call it.

## Notes

- active autolaunched flow
- accepts `checkId` and `parentId` as input or output variables
- not intended as the main example of a real business process implementation

For real implementations, organisations would typically point `CheckLaunchFlow` at their own autolaunched flows.
