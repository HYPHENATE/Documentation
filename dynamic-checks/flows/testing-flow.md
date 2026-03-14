# TestingFlow

## API Name
`TestingFlow`

## Flow Type
`Autolaunched Flow`

## Description

`TestingFlow` is a packaged autolaunched flow included primarily for test support and to validate the package's flow-launch behaviour.

The source metadata explicitly describes it as part of the Checks component test suite and notes that it should not be deleted. In practice, it is less a business-process flow and more a reference/support artifact that proves the `CheckLaunchFlow` integration path works.

---

## Launch Context

| Area | Detail |
|------|------|
| Trigger | Can be launched when a completed `Check__c` record is configured to start a flow through the package's post-completion automation settings. |
| Users | End users do not launch this directly. It is started by the package automation path. |
| Entry Criteria | A check must complete, have flow launching enabled, and reference `TestingFlow` as its configured flow API name. |

---

## Flow Steps

### Step 1 - Start

The flow starts in autolaunched mode and runs without a screen interface.

### Step 2 - Decision

The packaged definition contains a simple decision element used to support the flow structure required by the test scenario.

---

## Inputs and Outputs

| Name | Direction | Type | Purpose |
|------|------|------|------|
| `checkId` | Input and Output | `String` | Receives the completed check ID and can expose it back for validation or downstream use. |
| `parentId` | Input and Output | `String` | Receives the parent business record ID related to the completed check. |

---

## Data Impact

| Area | Detail |
|------|------|
| Objects | No core object changes are documented in the packaged definition; the flow is primarily present for test-support behaviour. |
| Actions | Demonstrates that the package can successfully create and start an autolaunched flow interview from completed checks. |

---

## Operational Notes

| Topic | Detail |
|------|------|
| Status | The flow is active in the packaged metadata. |
| Run mode | The flow is configured to run in `SystemModeWithoutSharing`. |
| Admin guidance | This flow is not the main model for a production business automation. Most organisations will point checks at their own autolaunched flows instead. |

---

## Related Automation

- [CheckLaunchFlow](/dynamic-checks/classes/check-launch-flow)
