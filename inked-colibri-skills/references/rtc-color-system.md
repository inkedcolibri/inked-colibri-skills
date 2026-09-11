# Reactive Color Variable System (RTC) — Reference Rules

Use this when generating, mapping, or binding colors in **Manager** (variables/styles) or **Builder** (component fills/strokes).

This is a semantic color system built around source colors. Source color names vary by project (`primary`, `secondary`, `accent`, `text`, `background`, etc.). The **structure** is fixed; the names are not mandatory targets.

---

## 1. Base / Solid Color

A variable without a modifier is the original solid source color.

Examples: `primary`, `secondary`, `accent`, `text`, `background`

Do **not** interpret the base variable as an opacity or shade value.

---

## 1a. Collection prefix — REQUIRED in Builder

The RTC collection in Figma is named `RTC`. Figma variable paths are
`CollectionName/VariableName`, so a valid binding path must include the
collection prefix.

**In Builder mode** (`fillVar`, `strokeVar`, `paintStyleVar`,
`strokeStyleVar`), always emit:

- `RTC/primary`
- `RTC/primary-shades/primary-55`
- `RTC/primary-shades-dark/primary-55`
- `RTC/primary-alpha/primary-15`

**In Manager mode**, the same variables are keyed WITHOUT the prefix:

- `primary`
- `primary-shades/primary-55`
- `primary-shades-dark/primary-55`
- `primary-alpha/primary-15`

The prefix is a Builder-side binding requirement only. Manager JSON must
not include it, or you will create a nested `RTC/RTC/...` hierarchy.

**Rule:** every path shown anywhere else in this document is the *Manager-form*
path. Builder must prepend `RTC/` before emitting it.

---

## 2. Light Shade System

`X-shades/X-N` — source color progressively blended toward **white**.

- `X` = source color
- `N` = shade level (5–100 in steps of 5)

Example: `primary-shades/primary-55` = Primary blended toward white at level 55.

This is a **lightened color**, not transparency.

---

## 3. Dark Shade System

`X-shades-dark/X-N` — source color progressively blended toward **black**.

Example: `primary-shades-dark/primary-55` = Primary blended toward black at level 55.

This is a **darkened color**, not transparency.

Same 5–100 step-5 range.

---

## 4. Alpha / Transparency System

`X-alpha/X-N` — source color at **N% opacity** over whatever is underneath.

Example: `primary-alpha/primary-15` = Primary at 15% opacity.

Fundamentally different from shades. Never treat shades and alpha as interchangeable.

Alpha values: 5–100 in steps of 5.

---

## 5. Four states of the same source color

| State | Manager path | Builder binding path | Meaning |
|-------|--------------|----------------------|---------|
| Base | `X` | `RTC/X` | Solid source |
| Light shade | `X-shades/X-N` | `RTC/X-shades/X-N` | Toward white |
| Dark shade | `X-shades-dark/X-N` | `RTC/X-shades-dark/X-N` | Toward black |
| Alpha | `X-alpha/X-N` | `RTC/X-alpha/X-N` | N% opacity |

---

## 6. Relationship to numbered color scales (e.g. 50–900)

Many systems use scales like `50, 100, … 900` (Tailwind-style is one example).
Lower numbers ≈ lighter; middle (often `500`) ≈ base; higher ≈ darker.

**Example** correspondence (not universal law):

| External scale | Reactive Variable |
|----------------|-------------------|
| 50 | `X-shades/X-15` |
| 100 | `X-shades/X-25` |
| 200 | `X-shades/X-35` |
| 300 | `X-shades/X-45` |
| 400 | `X-shades/X-55` |
| 500 | `X` (base) |
| 600 | `X-shades-dark/X-55` |
| 700 | `X-shades-dark/X-65` |
| 800 | `X-shades-dark/X-75` |
| 900 | `X-shades-dark/X-85` |

---

## 7. Scale numbers ≠ shade percentages

External scale position (e.g. `400`) is **not** the same number as the RTC shade level (e.g. `55`).

Never copy the external number into the Reactive path. Use a defined mapping.

---

## 8. Semantic assignment is project-specific

A project may map external families to semantic sources, e.g.:

- `slate` → `primary`
- `neutral` → `secondary`
- `gray` → `text`

Then:

- `slate/500` → `primary`
- `slate/400` → `primary-shades/primary-55`
- `slate/600` → `primary-shades-dark/primary-55`

These are **examples only**. Do not assume them for every task.

---

## 9. White and black

If the project defines:

- `white` as Background source → `background`
- `black` as Text source → `text`

Treat as semantic base mappings, not automatic shade/alpha.

---

## 10. Do not assume every task is Tailwind mapping

The task may involve Tailwind, other token systems, existing Figma variables, HEX, CSS variables, JSON tokens, or custom scales.

Always:

1. Identify the source color
2. Identify semantic role when available
3. Decide: base / light shade / dark shade / alpha
4. If from a numbered scale, use position → mapping (not raw number copy)
5. Preserve meaning; do not confuse shade % with scale numbers or shades with transparency
6. Emit `RTC/<path>` if the target is Builder; emit `<path>` if the target is Manager

---

## 11. HEX colors

Do not invent a Reactive path from HEX alone when an explicit semantic or scale relationship exists.

If only HEX is given with no semantic/scale info, keep HEX (or follow separate color-analysis rules for that task).

---

## 12. Critical distinction (never mix)

| Concept | Path | Is |
|---------|------|-----|
| Light shade | `X-shades/X-N` | Blend toward white |
| Dark shade | `X-shades-dark/X-N` | Blend toward black |
| Transparency | `X-alpha/X-N` | Opacity N% |

`primary-shades/primary-55` ≠ `primary-alpha/primary-55` ≠ `primary-shades-dark/primary-55`

---

## 13. Source of truth

The Reactive Variable architecture is the source of truth for color paths in this plugin.

External systems are only translation examples.

When mapping or generating:

1. Source color
2. Semantic role (if any)
3. Base vs light vs dark vs alpha
4. Scale position → correct mapping
5. Preserve semantic relationship
6. Never confuse shade % with external scale numbers
7. Never confuse shades with alpha
8. Never treat example Tailwind assignments as universal
9. Builder bindings are always `RTC/<path>` — never bare

---

## 14. Mode-specific path form (quick reference)

| Target | Where it's used | Path form | Example |
|--------|-----------------|-----------|---------|
| Manager | `variables` keys | bare | `primary-shades-dark/primary-85` |
| Builder | `fillVar`, `strokeVar`, `paintStyleVar`, `strokeStyleVar` | prefixed | `RTC/primary-shades-dark/primary-85` |

Do **not** prefix in Manager. Do **not** omit the prefix in Builder.

---

## Usage in this skill

**Manager**
- When creating or documenting color variables, use this path structure **without** the `RTC/` prefix.
- When binding styles to colors, prefer RTC paths over raw hex when the collection exists.

**Builder**
- For `fillVar` / `strokeVar` / related bindings, prefer RTC paths **with** the `RTC/` prefix when reference exports include them.
- If no RTC reference is provided, fall back to raw hex (or paintStyleVar paths the user supplied).
- Never invent shade/alpha levels or semantic names that are not in the conversation or reference files.
