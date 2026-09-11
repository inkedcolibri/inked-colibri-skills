# Builder — Supported Features & Known Limits

Based on the current Component Builder pipeline (`src/builder/pipeline.ts`) and the fidelity report (`doc/json-component-plugin-fidelity-report.md`).

Use this to stay inside what the plugin can actually Process today. Prefer the **Safe to emit** list. Treat **Use carefully** and **Avoid / not reliable yet** as secondary.

---

## Safe to emit (well supported)

### Structure & types
- `type`: `frame`, `text`, `rectangle`, `ellipse`, `line`, `vector`, `component`, `instance`, `group`, `boolean`, `image`
- `name`, `children`, `content` (text)
- Component-set wrapper: `setName`, `setLayout`, `setSpacing`, `setColumns`, `components`
- `instanceOf` / `ref` only when the component is known to exist

### Layout
- `layout`: `"horizontal"` | `"vertical"` | `"grid"` (string only)
- `layoutSizingHorizontal` / `layoutSizingVertical`: `"hug"` | `"fill"` | `"fixed"`
- `primaryAxisSizingMode` / `counterAxisSizingMode` (also accepted; prefer layoutSizing* when possible — do not mix both systems on one node)
- `primaryAxisAlignItems` / `counterAxisAlignItems`
- `layoutPositioning`: `"auto"` | `"absolute"`
- `itemSpacing` (number or variable path string)
- `spacingVar` (binds item spacing)
- `paddingLeft` / `paddingRight` / `paddingTop` / `paddingBottom` (number or path)
- `paddingVar` (binds all four sides)
- `minWidth` / `maxWidth` / `minHeight` / `maxHeight` (number or path) — preferred way to bind size
- `width` / `height` / `x` / `y` as **numbers only**

### Grid (when `layout: "grid"`)
- `gridRowCount`, `gridColumnCount`
- `gridRowGap`, `gridColumnGap`
- `gridRowsSizing`, `gridColumnsSizing` (arrays of `{ type: "FLEX" | "FIXED", value?: number }`)
- `gridAutoTracks`, `gridItemsPositioning`
- `strokesIncludedInLayout`
- Child placement: `gridRowSpan`, `gridColumnSpan`, `gridChildHorizontalAlign`, `gridChildVerticalAlign`, etc.

**Note:** Grid *column* track sizing has had a property-name bug in some builds (`gridColumnsSizing` vs real API `gridColumnSizes`). Prefer simple grids or verify after Process if column sizes matter.

### Fills, strokes, radius
- `paintStyleVar` (paint style path → fill)
- `fillVar` (color variable path — **must be `RTC/<path>` for RTC colors**)
- `fill` (hex fallback)
- `strokeStyleVar` / `strokeVar` / `stroke` (hex)
- `strokeWidth`
- Per-side: `strokeTopWeight`, `strokeBottomWeight`, `strokeLeftWeight`, `strokeRightWeight`
- `cornerRadius` (number or path) / `cornerRadiusVar`
- `opacity` (node-level 0–1)
- `fillOpacity` / `strokeOpacity` (supported in schema and newer pipeline paths; still treat as "prefer solid 1.0" if round-trip is critical)

**RTC note:** RTC color variables live in a collection named `RTC`. Builder
binding properties (`fillVar`, `strokeVar`, `paintStyleVar`,
`strokeStyleVar`) must include the collection prefix: `RTC/<path>`.
Manager variable keys do not include it.

### Text
- `textStyle` (or `styleVar`) — path to text style
- When **not** using textStyle: `fontSize`, `fontFamily`, `fontStyle`, `fontWeight`, `letterSpacing`, `lineHeight`, `textAlign`, `textAlignVertical`, `textDecoration`, `textCase`
- `segments` for rich text (partial styling)
- Do **not** set `fill` on a text node that already has `textStyle`

### Effects & other
- `effectStyleVar`
- `booleanOperation` for `"type": "boolean"`
- `vectorPaths` for vectors
- `imageHash` + optional `scaleMode` for images (only use a real hash; never invent)

### Binding helpers
- Number = literal
- String on padding / spacing / radius / min-max size / fillVar etc. = variable or style path (must exist in a supplied reference)

---

## Use carefully (partial or evolving support)

| Feature | Status |
|---------|--------|
| `layoutWrap` / `counterAxisAlignContent` / `counterAxisSpacing` | Present in pipeline; not fully covered in older fidelity notes — test after Process |
| Gradients | Pipeline has gradient helpers; fidelity report still lists incomplete round-trip for some gradient cases. Prefer solid fills + paint styles when possible |
| `fillOpacity` / `strokeOpacity` | Wired in newer code; older export paths could drop them — emit only when needed |
| Multiple fills/strokes | Pipeline historically focused on first paint; layered fills may collapse |
| Per-corner radius (`topLeftRadius` …) | Uniform `cornerRadius` is reliable; individual corners are a known gap |
| `visible: false` | Not consistently serialized — hidden layers may come back visible |
| Instance `componentProperties` (variant props) | Limited; prefer building variants as separate components in a set |

---

## Avoid or do not rely on yet

Do **not** depend on these for generated JSON that must Process cleanly today:

- Multi-layer fills/strokes as arrays (use one solid or one paint style)
- Full gradient fidelity as the primary design method
- `strokeAlign` (INSIDE/OUTSIDE/CENTER) as a required visual
- `rotation` as a required layout transform
- Masks (`isMask` / `maskType`)
- Ad-hoc effects that are not effect styles (`effectStyleVar` is the safe path)
- `blendMode` (node or paint)
- Image crop transforms / non-default scale modes as critical
- Invented `instanceOf` names
- Variable paths on `width` / `height` / `x` / `y`
- `"auto"` as a sizing value (use `"hug"` / `"fill"` / `"fixed"`)
- Nesting layout props inside a `layout` object
- Bare RTC paths (missing the `RTC/` collection prefix) on Builder bindings

---

## Generation policy for this skill

1. Prefer properties from **Safe to emit**.
2. Use **Use carefully** only when the user's request clearly needs them, and prefer simpler alternatives first.
3. Never emit properties from **Avoid** as the only way to achieve a design.
4. Always follow the Critical Rules in `builder-critical-rules.md` — those prevent crashes regardless of fidelity gaps.
5. When reference exports are missing, fall back to raw values (hex, numbers, font props) instead of guessing paths.
6. For RTC colors in Builder mode, always emit `RTC/<path>` (collection-prefixed). In Manager mode, emit bare paths.

---

## Source notes

- Pipeline: `colibri-mod/src/builder/pipeline.ts` (modular builds)
- Fidelity report: `doc/json-component-plugin-fidelity-report.md` (from figma2json package)
- Schema/rules: `prompt/AI_PROMPT.md`

Update this file when the Builder pipeline gains reliable support for previously limited features.
