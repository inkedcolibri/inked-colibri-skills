---
name: inked-colibri-skills
description: Generate JSON for Inked Colibri — Manager (variables and styles with binding) and Builder (complete component structures as cmp.json). Use when the user asks for variables, styles, size schemes, typography, layout, design system JSON, components, headers, buttons, cards, component sets, cmp.json, or any Figma design JSON that the plugin can execute.
---

# Inked Colibri Skills

One skill, two modes:

| Mode | When to use | Output |
|------|-------------|--------|
| **Manager** | Variables, styles, size/typography/layout schemes, binding | Flat JSON with `"variables"` and/or `"textStyles"` |
| **Builder** | Components, headers, buttons, cards, sets, full UI blocks | Valid `cmp.json` for the Component Builder |

Detect intent from the user request. Apply only the rules of the matching mode. Never mix the two JSON formats in one response unless the user explicitly asks for both.

---

## Mode detection

**Manager** triggers on:
- variables, styles, size scheme, typography, layout, binding, Token Commander style requests, "generate variables", "create text styles"

**Builder** triggers on:
- component, header, button, card, nav, component set, cmp.json, "create a … component", "build me a …", structure for Process button

If ambiguous, prefer Manager for pure token requests and Builder for anything that should become Figma nodes.

---

# MANAGER MODE

Generate production-ready flat JSON that the Manager can execute immediately.

## Core rules (Manager)

- Output **flat** JSON only. Never nest objects under a path.
- Top-level keys are only `"variables"` and/or `"textStyles"`.
- Every variable entry must contain:
  - `"type"`: one of `"string"`, `"number"`, `"color"`, `"boolean"`
  - `"value"`: a literal **or** a path string that references another variable
  - `"description"`: short human-readable note (required)
- Paths use `/` separators and become Figma collection hierarchy.
- Prefer variable-path references over hard-coded numbers so the system stays linked to the size scale.
- Recommended generation order:
  1. Size (base Schema + alias Sizes layer)
  2. Typography (Type variables + textStyles)
  3. Layout
  4. Layout Extended (only when breakpoints/containers are needed)

## When generating (Manager)

1. Start from the official boilerplates in `references/` unless the user explicitly wants a different scale.
2. If the user asks to change the scale (Tesla → Fibonacci, Material, custom), keep the same path structure and only replace values/references.
3. Always keep descriptions.
4. When producing textStyles, every property (`fontFamily`, `fontWeight`, `fontSize`, `letterSpacing`, `lineHeight`) must be a variable path reference, not a raw value.
5. Output only valid JSON. Do not wrap in markdown fences unless the user asks for explanation + JSON.

## Manager reference files

- `references/core-rules.md` — Variable Prompt for AI + best practices
- `references/size-scheme.md` — Size base + alias layers
- `references/typography-scheme.md` — Type variables + textStyles
- `references/layout-scheme.md` — base Layout spacing + dimensions
- `references/layout-extended.md` — breakpoints, container, grid
- `references/rtc-color-system.md` — Reactive Color Variable (RTC) path structure: base, shades, shades-dark, alpha

## Color variables (Manager)

When creating or binding colors, follow `references/rtc-color-system.md`:

- Base: `X` (solid source)
- Light: `X-shades/X-N` (toward white)
- Dark: `X-shades-dark/X-N` (toward black)
- Alpha: `X-alpha/X-N` (opacity) — never confuse with shades
- Numbered external scales (e.g. 50–900) need an explicit mapping; do not copy the scale number into `N`
- Do not invent semantic names or shade levels not present in the task or reference exports

**Manager uses bare paths — no collection prefix.** The prefix rule applies to Builder only. See §1a in `references/rtc-color-system.md`.

## Manager anti-patterns

- Nested objects
- Missing `description`
- Hard-coded numbers where `Sizes/...` should be used
- Inventing new top-level keys
- Mixing raw values into textStyles properties
- Confusing shade paths with alpha paths
- Copying external scale numbers (e.g. Tailwind 400) directly into RTC shade levels
- Adding an `RTC/` prefix in Manager JSON (that creates a nested `RTC/RTC/...` hierarchy)

---

# BUILDER MODE

Generate valid `cmp.json` that the Component Builder can Process into real Figma nodes without crashing or silently dropping properties.

## Critical rules (Builder) — never violate

1. `layout` is always a **string** (`"horizontal"` | `"vertical"` | `"grid"`). Never an object.
2. Sizing values are only `"hug"` | `"fill"` | `"fixed"`. There is no `"auto"`.
3. `x`, `y`, `width`, `height` are always **numbers**. Variable paths are forbidden on them.
4. Variable binding for size works only via `minHeight` / `maxHeight` / `minWidth` / `maxWidth` (or use a literal number).
5. Never invent `instanceOf` or `ref` unless the component is known to exist in the user's file. Prefer building from primitives.
6. Text nodes: use either `textStyle` **or** individual font properties — never both. Do not put `fill` on a text node when using `textStyle`.
7. Do not mix `layoutSizingHorizontal`/`layoutSizingVertical` with `primaryAxisSizingMode`/`counterAxisSizingMode` on the same node.
8. Only use properties defined in the schema. Unknown properties are silently ignored.
9. Number = literal value. String = variable or style path. Never mix on the same property.
10. Only bind a path if a reference export was supplied in the conversation **and** a confident semantic match exists. Otherwise use raw values.

## Binding policy (Builder)

- Colors → `fillVar` / `paintStyleVar` / `strokeVar` / `strokeStyleVar`
  - RTC paths MUST be prefixed with the collection name: `RTC/<path>`
    - ✅ `RTC/secondary`
    - ✅ `RTC/primary-shades-dark/primary-85`
    - ✅ `RTC/accent-shades/accent-45`
    - ❌ `secondary` (bare — will not bind)
    - ❌ `primary-shades-dark/primary-85` (bare — will not bind)
  - Never invent RTC paths; fall back to hex or a supplied `paintStyleVar`
    path if no confident match exists
- Padding (all sides) → `paddingVar` or per-side `paddingLeft` etc. as path strings
- Gap → `spacingVar` or `itemSpacing` as path string
- Corner radius → `cornerRadiusVar` or `cornerRadius` as path string
- Text → `textStyle` path (then omit individual font props)
- If no reference file is present for a category, use raw values (hex, numbers, font props)

## Root shapes (Builder)

- Single node: `{ "name": "...", "type": "frame", "layout": "horizontal", ... }`
- Array of nodes
- Component set:
  ```json
  {
    "setName": "Button Large",
    "setLayout": "grid",
    "setSpacing": 24,
    "setColumns": 4,
    "components": [ ... ]
  }
  ```

## Key node properties (Builder)

| Property | Notes |
|----------|-------|
| `type` | frame, text, rectangle, ellipse, line, vector, component, instance, group, boolean |
| `layout` | "horizontal" \| "vertical" \| "grid" |
| `layoutSizingHorizontal` / `Vertical` | "hug" \| "fill" \| "fixed" |
| `primaryAxisAlignItems` / `counterAxisAlignItems` | min, center, max, space-between |
| `paintStyleVar` / `fillVar` / `strokeVar` | path strings — RTC must be `RTC/<path>` |
| `paddingVar` / `paddingLeft`… | path or number |
| `spacingVar` / `itemSpacing` | path or number |
| `cornerRadius` / `cornerRadiusVar` | path or number |
| `textStyle` | path — do not also set font* props |
| `content` | text only |
| `children` | array of the same schema |
| `width` / `height` / `x` / `y` | numbers only |

Full property tables, examples, and support limits live in:

- `references/builder-critical-rules.md` — never-violate rules
- `references/builder-schema.md` — property tables
- `references/builder-supported.md` — what the current Builder pipeline actually supports (safe vs avoid)
- `references/builder-examples.md` — button, set, header
- `references/builder-primitives.md` — fresh blocks when no instance exists
- `references/rtc-color-system.md` — RTC color paths for fillVar / strokeVar binding

Prefer properties listed as **Safe to emit** in `builder-supported.md`. Do not rely on features marked avoid/unreliable.

## Pre-return checklist (Builder)

Before emitting JSON, verify:

1. `layout` is a string, never an object.
2. No `"auto"` sizing values.
3. `width` / `height` / `x` / `y` are numbers only.
4. Text nodes use either `textStyle` or individual font props, never both.
5. No `fill` on text nodes that use `textStyle`.
6. Every path used for binding exists in a supplied reference (or fall back to raw).
7. fill-sized children only appear inside auto-layout parents.
8. Output is pure JSON (no markdown fences unless the user asked for explanation + JSON).
9. Every `fillVar` / `strokeVar` / `paintStyleVar` / `strokeStyleVar` that references the RTC collection starts with `RTC/`.

## Builder anti-patterns

- Nesting layout properties inside a `layout` object
- Using `"auto"` for sizing
- Putting variable paths on `width` / `height` / `x` / `y`
- Inventing component names for `instanceOf`
- Mixing bound and raw values on the same property
- Guessing variable or style paths that were not provided
- Emitting an RTC path without the `RTC/` collection prefix
- Using `RTC/` in Manager mode (Manager uses bare paths only)

---

## Output style (both modes)

- Prefer complete, ready-to-paste JSON.
- When the user asks for multiple things, emit them as separate clear blocks in a sensible order.
- Briefly note intentional deviations or fallbacks to raw values.
- If the request is ambiguous between Manager and Builder, ask one short clarifying question or default according to the detection rules above.

## Relationship between modes

Manager creates the variables and styles.
Builder creates components that can bind to those variables and styles.

When both are needed, generate Manager JSON first, then Builder JSON that references the paths just created (or the paths the user already has in their file).

**Path form differs by mode:**

| Mode | RTC path form | Example |
|------|---------------|---------|
| Manager | bare | `primary-shades-dark/primary-85` |
| Builder | prefixed | `RTC/primary-shades-dark/primary-85` |
