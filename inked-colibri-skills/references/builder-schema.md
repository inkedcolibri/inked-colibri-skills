# Builder — Schema Reference

## Node types

`frame` | `text` | `rectangle` | `ellipse` | `line` | `vector` | `image` | `instance` | `component` | `group` | `boolean`

Default is `frame` if omitted.

## Common properties

| Property | Type | Notes |
|----------|------|-------|
| `name` | string | Figma node name |
| `type` | string | See list above |
| `layout` | `"horizontal"` \| `"vertical"` \| `"grid"` | Enables auto-layout |
| `layoutSizingHorizontal` | `"hug"` \| `"fill"` \| `"fixed"` | |
| `layoutSizingVertical` | `"hug"` \| `"fill"` \| `"fixed"` | |
| `primaryAxisSizingMode` | `"auto"` \| `"fixed"` \| `"fill"` | Prefer layoutSizing* when possible |
| `counterAxisSizingMode` | `"auto"` \| `"fixed"` \| `"fill"` | |
| `primaryAxisAlignItems` | `"min"` \| `"center"` \| `"max"` \| `"space-between"` | |
| `counterAxisAlignItems` | `"min"` \| `"center"` \| `"max"` | |
| `layoutPositioning` | `"auto"` \| `"absolute"` | |
| `constraintH` / `constraintV` | `"min"` \| `"center"` \| `"max"` \| `"stretch"` | |
| `paintStyleVar` | string | Paint style path (fill) |
| `fillVar` | string | Color variable path |
| `strokeVar` / `strokeStyleVar` | string | Stroke binding |
| `paddingVar` | string | One variable for all four sides |
| `paddingLeft` / `Right` / `Top` / `Bottom` | number \| string | |
| `itemSpacing` / `spacingVar` | number \| string | |
| `cornerRadius` / `cornerRadiusVar` | number \| string | |
| `minWidth` / `maxWidth` / `minHeight` / `maxHeight` | number \| string | Preferred way to bind size |
| `textStyle` | string | Text style path |
| `effectStyleVar` | string | |
| `opacity` | number | 0–1 |
| `width` / `height` | number | Literal only |
| `x` / `y` | number | Literal only |
| `content` | string | Text nodes only |
| `children` | array | Same schema |
| `fill` | string | Hex fallback |
| `stroke` | string | Hex fallback |
| `strokeWidth` | number | |
| `strokeTopWeight` etc. | number | Per-side |
| `fillOpacity` / `strokeOpacity` | number | 0–1 |
| `fontSize` / `fontFamily` / `fontStyle` / `fontWeight` | number/string | Only when **not** using textStyle |
| `letterSpacing` / `lineHeight` | number | |
| `textAlign` | `"left"` \| `"center"` \| `"right"` \| `"justified"` | |
| `textAlignVertical` | `"top"` \| `"center"` \| `"bottom"` | |
| `textDecoration` / `textCase` | string | |
| `segments` | array | Rich text |
| `vectorPaths` | array | Vector only |
| `imageHash` | string | Image only — never invent |
| `instanceOf` | string | Only if component exists |
| `booleanOperation` | `"union"` \| `"subtract"` \| `"intersect"` \| `"exclude"` | |
| `nestedInstances` | array | |

## Grid-specific (when `layout: "grid"`)

- `gridRowCount`, `gridColumnCount`
- `gridRowGap`, `gridColumnGap`
- `gridRowsSizing`, `gridColumnsSizing` (arrays of `{ "type": "FLEX" \| "FIXED", "value"?: number }`)
- `gridAutoTracks`, `gridItemsPositioning`
- Child: `gridRowSpan`, `gridColumnSpan`, `gridChildHorizontalAlign`, `gridChildVerticalAlign`, `gridRowAnchorIndex`, `gridColumnAnchorIndex`

## Component set wrapper

```json
{
  "setName": "Button Large",
  "setLayout": "grid",
  "setSpacing": 24,
  "setColumns": 4,
  "components": [ /* component nodes */ ]
}
```

Freeform set: omit `setLayout` / `setSpacing` / `setColumns` and give every child explicit `x`/`y`/`width`/`height`.
