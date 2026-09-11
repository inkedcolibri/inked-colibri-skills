# Layout Variables Scheme (Base)

Official base layout boilerplate. Spacing tokens reference the Sizes scale; dimension tokens provide useful block widths.

```json
{
  "variables": {
    "Layout/Spacing/Small": {
      "type": "number",
      "value": "Sizes/1",
      "description": "Use for padding or gap at block level"
    },
    "Layout/Spacing/Medium": {
      "type": "number",
      "value": "Sizes/3",
      "description": "Use for padding or gap at group level"
    },
    "Layout/Spacing/Large": {
      "type": "number",
      "value": "Sizes/5",
      "description": "Use for padding or gap at section level"
    },
    "Layout/Dimensions/Block-1": {
      "type": "number",
      "value": 160,
      "description": "Layout dimension for Block-1"
    },
    "Layout/Dimensions/Block-2": {
      "type": "number",
      "value": 320,
      "description": "Layout dimension for Block-2"
    },
    "Layout/Dimensions/Block-3": {
      "type": "number",
      "value": 480,
      "description": "Layout dimension for Block-3"
    },
    "Layout/Dimensions/Block-4": {
      "type": "number",
      "value": 640,
      "description": "Layout dimension for Block-4"
    },
    "Layout/Dimensions/Block-5": {
      "type": "number",
      "value": 800,
      "description": "Layout dimension for Block-5"
    },
    "Layout/Dimensions/Block-6": {
      "type": "number",
      "value": 960,
      "description": "Layout dimension for Block-6"
    },
    "Layout/Dimensions/Block-7": {
      "type": "number",
      "value": 1120,
      "description": "Layout dimension for Block-7"
    },
    "Layout/Dimensions/Block-8": {
      "type": "number",
      "value": 1280,
      "description": "Layout dimension for Block-8"
    },
    "Layout/Dimensions/Block-9": {
      "type": "number",
      "value": 1440,
      "description": "Layout dimension for Block-9"
    },
    "Layout/Dimensions/MinWidth": {
      "type": "number",
      "value": 320,
      "description": "Minimum viewport/section width"
    },
    "Layout/Dimensions/MaxWidth": {
      "type": "number",
      "value": 1920,
      "description": "Max grid width, 12 columns"
    }
  }
}
```

## Recommended usage

- Use `Layout/Spacing/*` for padding, margin, and gap.
- Use `Layout/Dimensions/*` for section widths, container thresholds, and grid widths.
- Keep everything connected to the same `Sizes/...` source of truth.
