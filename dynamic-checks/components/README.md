# Components

This section documents the main Lightning Web Components used by the **Dynamic Checks** package.

The package uses a compact component hierarchy:

- one exposed record-page container
- one internal category renderer
- one internal checklist-item component

The source also includes older `check`, `checksCategory`, and `checksContainer` bundles, but the primary current experience is built around the `dynamicChecksContainer` component family documented here.

---

## Component Overview

| Component | Purpose | Exposure |
|------|------|------|
| [Dynamic Checks Container](/dynamic-checks/components/dynamic-checks-container) | Main record-page component that loads checklist data and renders categories for the current record | `lightning__RecordPage` |
| [Dynamic Checks Category](/dynamic-checks/components/dynamic-checks-category) | Internal section component that renders one checklist category, progress state, and child checks | Internal only |
| [Dynamic Check](/dynamic-checks/components/dynamic-check) | Internal checklist-item component used to complete checks, select custom values, and save comments | Internal only |

---

## Design Notes

| Area | Detail |
|------|------|
| Container-first design | The exposed component handles page context and server calls, while child components focus on rendering and user interaction. |
| Wrapper-based state | The LWC layer expects the `CheckCategory` and `Check` wrapper payloads returned by Apex rather than querying metadata directly. |
| LDS updates | Individual checks are updated client-side using Lightning Data Service rather than custom Apex save methods. |
| Event bubbling | Child components dispatch events upward so the container can refresh checklist state after changes. |
