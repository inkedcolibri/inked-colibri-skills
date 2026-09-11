# Core Rules — Variable Prompt for AI

Use this as the shared context so every generation stays compatible with Inked Colibri Token Commander.

## Variable Prompt for AI

```
Context:
The plugin supports two schema types: variables and styles. Each schema is a flat JSON structure that maps to Figma variables and styles.

VARIABLE SCHEMA
- JSON under a "variables" key
- Each key is a Figma variable path (e.g. "Sizes/1" or "Type/Font Family/Primary")
- Each item: "type" (number | string | color | boolean), "value" (literal or another path), optional but recommended "description"
- If value matches another variable path, it is treated as a linked reference (binding)

STYLE SCHEMA
- JSON under a "textStyles" key (or "styles")
- Each key is a style path (e.g. "Primary/Regular/Body")
- Each item is an object of properties such as fontFamily, fontWeight, fontSize, letterSpacing, lineHeight — these should almost always be variable path references

Rules:
- Never nest variables or styles
- Preserve types, references, and valid JSON
- Always include a description on variables
- Prefer path references over hard-coded numbers so the whole system stays linked to the size scale
```

## Best practices

- Keep it flat — no nested objects.
- Make sure the type actually matches the value.
- Add a description to every variable — it makes AI-generated JSON reviewable at a glance.
- Treat AI output as a draft: verify paths and types before executing in Token Commander.
- Execute in order: Size → Typography → Layout → (optional) Extended Layout.

## Binding

When `"value"` is a string that matches an existing variable path, Token Commander creates a variable-to-variable binding. This is the preferred way to keep typography and layout tied to the size scale.
