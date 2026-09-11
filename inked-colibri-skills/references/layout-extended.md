# Layout Variables (Extended)

Use only after the base Layout scheme is in place. Adds explicit breakpoints, container, and grid controls while still referencing the size scale where possible.

```json
{
  "variables": {
    "Layout/Spacing/Small": {
      "type": "number",
      "value": "Sizes/1",
      "description": "Small spacing token"
    },
    "Layout/Spacing/Medium": {
      "type": "number",
      "value": "Sizes/3",
      "description": "Medium spacing token"
    },
    "Layout/Spacing/Large": {
      "type": "number",
      "value": "Sizes/5",
      "description": "Large spacing token"
    },
    "Layout/Breakpoint/Mobile/Min": {
      "type": "number",
      "value": 0,
      "description": "Mobile minimum breakpoint"
    },
    "Layout/Breakpoint/Mobile/Max": {
      "type": "number",
      "value": 767,
      "description": "Mobile maximum breakpoint"
    },
    "Layout/Breakpoint/Tablet/Min": {
      "type": "number",
      "value": 768,
      "description": "Tablet minimum breakpoint"
    },
    "Layout/Breakpoint/Tablet/Max": {
      "type": "number",
      "value": 1023,
      "description": "Tablet maximum breakpoint"
    },
    "Layout/Breakpoint/Desktop/Min": {
      "type": "number",
      "value": 1024,
      "description": "Desktop minimum breakpoint"
    },
    "Layout/Breakpoint/Desktop/Max": {
      "type": "number",
      "value": 1439,
      "description": "Desktop maximum breakpoint"
    },
    "Layout/Breakpoint/Wide/Min": {
      "type": "number",
      "value": 1440,
      "description": "Wide minimum breakpoint"
    },
    "Layout/Container/MaxWidth": {
      "type": "number",
      "value": 1200,
      "description": "Default container max width"
    },
    "Layout/Container/Padding": {
      "type": "number",
      "value": "Sizes/3",
      "description": "Base container padding"
    },
    "Layout/Grid/Columns": {
      "type": "number",
      "value": 12,
      "description": "Grid column count"
    },
    "Layout/Grid/Gutter": {
      "type": "number",
      "value": "Sizes/3",
      "description": "Grid gutter"
    },
    "Layout/Dimensions/MinWidth": {
      "type": "number",
      "value": 320,
      "description": "Minimum viewport/section width"
    },
    "Layout/Dimensions/MaxWidth": {
      "type": "number",
      "value": 1920,
      "description": "Maximum layout width"
    }
  }
}
```

## When to use

- When the design system needs explicit mobile / tablet / desktop / wide breakpoints.
- When components require different layout behavior across viewports.
- After the core Size + base Layout schemes are already in place.
