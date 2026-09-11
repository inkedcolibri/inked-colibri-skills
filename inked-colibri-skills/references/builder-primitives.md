# Builder — Fresh Block Primitives

Use these when no existing component can be instanced. Build everything from frames, text, rectangles, and ellipses.

## Icon (circle)

```json
{
  "name": "Icon",
  "type": "ellipse",
  "width": 24,
  "height": 24,
  "fill": "#ef4444"
}
```

## Logo mark

```json
{
  "name": "Logo Mark",
  "type": "rectangle",
  "width": 32,
  "height": 32,
  "cornerRadius": 8,
  "fill": "#3b82f6"
}
```

## Simple button (raw)

```json
{
  "name": "Button",
  "type": "frame",
  "layout": "horizontal",
  "layoutSizingHorizontal": "hug",
  "layoutSizingVertical": "hug",
  "paddingTop": 8,
  "paddingBottom": 8,
  "paddingLeft": 16,
  "paddingRight": 16,
  "cornerRadius": 6,
  "fill": "#3b82f6",
  "primaryAxisAlignItems": "center",
  "counterAxisAlignItems": "center",
  "children": [
    {
      "name": "Label",
      "type": "text",
      "content": "Action",
      "fontSize": 14,
      "fontFamily": "Inter",
      "fontWeight": 500,
      "fill": "#ffffff"
    }
  ]
}
```

## Toggle

```json
{
  "name": "Toggle",
  "type": "frame",
  "layout": "horizontal",
  "layoutSizingHorizontal": "hug",
  "layoutSizingVertical": "hug",
  "paddingTop": 6,
  "paddingBottom": 6,
  "paddingLeft": 12,
  "paddingRight": 12,
  "cornerRadius": 20,
  "stroke": "#e2e8f0",
  "strokeWidth": 1,
  "itemSpacing": 8,
  "primaryAxisAlignItems": "center",
  "children": [
    {
      "name": "Knob",
      "type": "ellipse",
      "width": 16,
      "height": 16,
      "fill": "#fbbf24"
    },
    {
      "name": "Label",
      "type": "text",
      "content": "Theme",
      "fontSize": 13,
      "fontFamily": "Inter"
    }
  ]
}
```

## Nav item

```json
{
  "name": "Nav Item",
  "type": "frame",
  "layout": "horizontal",
  "layoutSizingHorizontal": "hug",
  "layoutSizingVertical": "hug",
  "paddingTop": 8,
  "paddingBottom": 8,
  "paddingLeft": 12,
  "paddingRight": 12,
  "cornerRadius": 4,
  "children": [
    {
      "name": "Label",
      "type": "text",
      "content": "Navigation",
      "fontSize": 14,
      "fontFamily": "Inter"
    }
  ]
}
```

## Card shell

```json
{
  "name": "Card",
  "type": "frame",
  "layout": "vertical",
  "layoutSizingHorizontal": "fixed",
  "layoutSizingVertical": "hug",
  "width": 320,
  "paddingTop": 24,
  "paddingBottom": 24,
  "paddingLeft": 24,
  "paddingRight": 24,
  "itemSpacing": 16,
  "cornerRadius": 12,
  "fill": "#ffffff",
  "stroke": "#e2e8f0",
  "strokeWidth": 1,
  "children": []
}
```

Always prefer binding to existing variables/styles when reference exports are present in the conversation. Fall back to the raw values shown above only when no matching paths exist.
