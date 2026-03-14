# {{COMPONENT_LABEL}}

Briefly explain what the component is for, who uses it, and where it usually appears.

---

## API Name
`{{COMPONENT_API_NAME}}`

## Builder Name
`{{BUILDER_NAME}}`

<!-- Remove the Builder Name section if the component is not exposed in a builder context. -->

## Description
{{COMPONENT_DESCRIPTION}}

---

## Targets

- `{{TARGET_NAME}}`

<!-- Use Targets for exposed components. Replace this with an Exposure section for internal-only components. -->

## Exposure

Explain whether the component is exposed directly or intended to be embedded inside other LWCs.

<!-- Keep either Targets or Exposure, depending on the component type. -->

---

## Public Properties

| Name | API Name | Data Type | Required | Description |
|------|------|------|------|------|
| {{PROPERTY_LABEL}} | `{{PROPERTY_API_NAME}}` | {{PROPERTY_TYPE}} | {{PROPERTY_REQUIRED}} | {{PROPERTY_DESCRIPTION}} |

---

## Expected Data Structure

Explain any important object, array, or event payload shapes the component expects.

<!-- Remove this section if the component only accepts simple scalar inputs. -->

---

## Behaviour Notes

| Area | Detail |
|------|------|
| {{BEHAVIOUR_AREA}} | {{BEHAVIOUR_DETAIL}} |

---

## Events

| Event | Description |
|------|------|
| `{{EVENT_NAME}}` | {{EVENT_DESCRIPTION}} |

<!-- Remove the Events section if the component does not dispatch meaningful custom events. -->

---

## Example Usage

Provide a short example showing how the component is configured or embedded.

```html
<c-{{COMPONENT_KEBAB_NAME}}></c-{{COMPONENT_KEBAB_NAME}}>
```

---

## Developer Notes

| Topic | Detail |
|------|------|
| {{DEVELOPER_NOTE_TOPIC}} | {{DEVELOPER_NOTE_DETAIL}} |

---

## Related Components

- [{{RELATED_COMPONENT_LABEL}}](/components/{{RELATED_COMPONENT_SLUG}})

<!-- Remove any section that is not relevant rather than leaving placeholder content behind. -->
