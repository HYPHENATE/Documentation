# Apex Classes

This section documents the main production Apex classes used by the **Help Messages** package.

The package uses a small Apex layer to:

- retrieve candidate messages for the current record
- decide whether draft content should be visible
- evaluate filter conditions dynamically
- centralise shared filter and operator constants

---

## Class Overview

| Class | Purpose | Tested By |
|------|------|------|
| [HelpMessageController](/help-messages/classes/help-message-controller) | Main Aura-enabled controller used by the record-page component | `HelpMessageController_Test` |
| [HelpMessageHelper](/help-messages/classes/help-message-helper) | Helper class that evaluates filters against the current record | `HelpMessageController_Test` |
| [HelpMessageConstants](/help-messages/classes/help-message-constants) | Shared constant values for filter logic and operators | `HelpMessageController_Test` |
