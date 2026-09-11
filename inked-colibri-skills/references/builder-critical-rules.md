# Builder — Critical Rules (expanded)

These rules come from the official AI_PROMPT for the JSON ⇄ Component builder. Violating them causes crashes or silent property drops.

## 1. `layout` is always a string

**Wrong**
```json
{ "layout": { "type": "frame", "layout": "vertical", "paddingTop": 0 } }
```

**Right**
```json
{ "layout": "vertical", "paddingTop": 0, ... }
```

Valid values: `"horizontal"`, `"vertical"`, `"grid"`.

## 2. Never use `"auto"` for layout sizing

Valid values only: `"hug"`, `"fill"`, `"fixed"`.

## 3. Coordinates and dimensions are numbers

`x`, `y`, `width`, `height` must be numbers.
Variable paths are **not** allowed here.

**Wrong:** `"height": "Header/Dimensions/Height"`
**Right:** `"height": 80` or use `minHeight` / `maxHeight` with a path.

## 4. Size binding only via min/max

To bind a variable to height/width use:
```json
"minHeight": "Some/Path",
"maxHeight": "Some/Path"
```
or a literal number on `height` / `width`.

## 5. Do not invent `instanceOf`

Only use `"type": "instance"` + `instanceOf` when you are certain the component already exists in the user's file.
Otherwise build from primitives (frame + text + rectangle, etc.).

## 6. Text nodes and fill

When using `textStyle`, do **not** also set `fill`, `fontSize`, `fontFamily`, etc.
The style carries those values.

## 7. Do not mix sizing systems

Pick either:
- `layoutSizingHorizontal` / `layoutSizingVertical`

or

- `primaryAxisSizingMode` / `counterAxisSizingMode`

Never both on the same node.

## 8. Grid

Use `"layout": "grid"`.
Children can use `gridRowSpan`, `gridColumnSpan`, `gridChildHorizontalAlign`, etc.

## 9. Unknown properties are ignored

Only emit properties listed in the schema. Extra keys are silently dropped.

## 10. Number vs string is the binding switch

- Number → literal pixel / numeric value
- String → treated as a variable or style path (must exist in a supplied reference)

Never put a path string on a property that expects a number (except the documented binding properties).

## 11. Rich text

Use `segments` array when a single text node needs mixed styles (partial bold, different colors, etc.).

## 12. Per-side strokes

Use `strokeTopWeight`, `strokeBottomWeight`, `strokeLeftWeight`, `strokeRightWeight` instead of a single `strokeWidth` when sides differ.

## 13. Groups and boolean operations

- `"type": "group"` — no auto-layout, children use explicit x/y
- `"type": "boolean"` + `booleanOperation`: `"union"` | `"subtract"` | `"intersect"` | `"exclude"`

## 14. RTC color bindings include the collection prefix

Builder binding properties for RTC colors must use the full Figma path
including the collection name:

- `fillVar`, `strokeVar`, `paintStyleVar`, `strokeStyleVar` → `RTC/<path>`

**Wrong:** `"fillVar": "primary-shades-dark/primary-85"`
**Right:** `"fillVar": "RTC/primary-shades-dark/primary-85"`

A missing `RTC/` prefix causes the binding to resolve against no collection
and the paint is silently dropped. This is a common cause of "my colors
didn't apply" reports.

Manager mode does **not** use this prefix — Manager variable keys are bare
paths. Only Builder bindings require `RTC/`.
