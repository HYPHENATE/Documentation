# Flows

This section documents the packaged Flow content included in **Dynamic Checks**.

The package currently includes one notable flow:

- [TestingFlow](/dynamic-checks/flows/testing-flow)

Unlike a business-process package where flows drive the main user journey, the packaged flow here mainly exists to support test coverage and demonstrate the post-completion flow-launch pattern used by `CheckLaunchFlow`.

---

## Flow Overview

| Flow | Type | Purpose |
|------|------|------|
| [TestingFlow](/dynamic-checks/flows/testing-flow) | Autolaunched Flow | Test-support flow used by the package to validate flow-launch behaviour from completed checks. |

---

## Design Notes

| Area | Detail |
|------|------|
| Packaged intent | The included flow is not the primary business automation for the package. It exists mainly as a support artifact. |
| Launch pattern | Real org implementations can point completed checks at their own autolaunched flows using the template configuration fields. |
| Integration point | `CheckLaunchFlow` is the class that starts configured flows when qualifying checks are completed. |
