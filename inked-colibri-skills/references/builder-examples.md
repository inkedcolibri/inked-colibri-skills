# Builder — Working Examples

## 1. Simple primary button (bound to paint styles + padding variables)

Prefer `layoutSizing*` over the older `primaryAxisSizingMode: "auto"` form.

```json
{
  "name": "Primary Button",
  "type": "frame",
  "layout": "horizontal",
  "layoutSizingHorizontal": "hug",
  "layoutSizingVertical": "hug",
  "paintStyleVar": "Button-2/primary/states/rest/plate",
  "paddingTop": "Layout Control/Desktop/Button/V_Padding",
  "paddingBottom": "Layout Control/Desktop/Button/V_Padding",
  "paddingLeft": "Layout Control/Desktop/Button/H_Padding",
  "paddingRight": "Layout Control/Desktop/Button/H_Padding",
  "itemSpacing": "Layout Control/Desktop/Button/Gap",
  "cornerRadius": 8,
  "primaryAxisAlignItems": "center",
  "counterAxisAlignItems": "center",
  "children": [
    {
      "name": "Icon",
      "type": "frame",
      "width": 16,
      "height": 16,
      "paintStyleVar": "Button-2/primary/states/rest/leadingIcon"
    },
    {
      "name": "Label",
      "type": "text",
      "content": "Submit",
      "paintStyleVar": "Button-2/primary/states/rest/text"
    }
  ]
}
```

If no variable/style references are available, replace paths with raw values:

```json
{
  "name": "Primary Button",
  "type": "frame",
  "layout": "horizontal",
  "layoutSizingHorizontal": "hug",
  "layoutSizingVertical": "hug",
  "fill": "#3b82f6",
  "paddingTop": 8,
  "paddingBottom": 8,
  "paddingLeft": 16,
  "paddingRight": 16,
  "itemSpacing": 8,
  "cornerRadius": 8,
  "primaryAxisAlignItems": "center",
  "counterAxisAlignItems": "center",
  "children": [
    {
      "name": "Label",
      "type": "text",
      "content": "Submit",
      "fontSize": 14,
      "fontFamily": "Inter",
      "fontWeight": 500,
      "fill": "#ffffff"
    }
  ]
}
```

## 2. Component set (Rest + Hover, Primary)

```json
{
  "setName": "Button / Primary",
  "setLayout": "horizontal",
  "setSpacing": 24,
  "components": [
    {
      "name": "State=Rest, Type=Primary",
      "type": "component",
      "layout": "horizontal",
      "layoutSizingHorizontal": "hug",
      "layoutSizingVertical": "hug",
      "paintStyleVar": "Button-2/primary/states/rest/plate",
      "paddingTop": "Layout Control/Desktop/Button/V_Padding",
      "paddingBottom": "Layout Control/Desktop/Button/V_Padding",
      "paddingLeft": "Layout Control/Desktop/Button/H_Padding",
      "paddingRight": "Layout Control/Desktop/Button/H_Padding",
      "itemSpacing": "Layout Control/Desktop/Button/Gap",
      "cornerRadius": 8,
      "primaryAxisAlignItems": "center",
      "counterAxisAlignItems": "center",
      "children": [
        {
          "name": "Icon",
          "type": "frame",
          "width": 16,
          "height": 16,
          "paintStyleVar": "Button-2/primary/states/rest/leadingIcon"
        },
        {
          "name": "Label",
          "type": "text",
          "content": "Click Me",
          "paintStyleVar": "Button-2/primary/states/rest/text"
        }
      ]
    },
    {
      "name": "State=Hover, Type=Primary",
      "type": "component",
      "layout": "horizontal",
      "layoutSizingHorizontal": "hug",
      "layoutSizingVertical": "hug",
      "paintStyleVar": "Button-2/primary/states/hover/plate",
      "paddingTop": "Layout Control/Desktop/Button/V_Padding",
      "paddingBottom": "Layout Control/Desktop/Button/V_Padding",
      "paddingLeft": "Layout Control/Desktop/Button/H_Padding",
      "paddingRight": "Layout Control/Desktop/Button/H_Padding",
      "itemSpacing": "Layout Control/Desktop/Button/Gap",
      "cornerRadius": 8,
      "primaryAxisAlignItems": "center",
      "counterAxisAlignItems": "center",
      "children": [
        {
          "name": "Icon",
          "type": "frame",
          "width": 16,
          "height": 16,
          "paintStyleVar": "Button-2/primary/states/hover/leadingIcon"
        },
        {
          "name": "Label",
          "type": "text",
          "content": "Click Me",
          "paintStyleVar": "Button-2/primary/states/hover/text"
        }
      ]
    }
  ]
}
```

## 3. Marketing header (raw-value fallback — safe when no references given)

```json
{
  "name": "Marketing Header",
  "type": "frame",
  "layout": "horizontal",
  "layoutSizingHorizontal": "fill",
  "layoutSizingVertical": "hug",
  "height": 80,
  "paddingLeft": 32,
  "paddingRight": 32,
  "primaryAxisAlignItems": "center",
  "counterAxisAlignItems": "center",
  "itemSpacing": 24,
  "fill": "#ffffff",
  "children": [
    {
      "name": "Logo",
      "type": "frame",
      "layout": "horizontal",
      "layoutSizingHorizontal": "hug",
      "layoutSizingVertical": "hug",
      "itemSpacing": 8,
      "primaryAxisAlignItems": "center",
      "children": [
        {
          "name": "Logo Mark",
          "type": "rectangle",
          "width": 32,
          "height": 32,
          "cornerRadius": 8,
          "fill": "#3b82f6"
        },
        {
          "name": "Logo Text",
          "type": "text",
          "content": "Brand",
          "fontSize": 18,
          "fontFamily": "Inter",
          "fontWeight": 700
        }
      ]
    },
    {
      "name": "Nav",
      "type": "frame",
      "layout": "horizontal",
      "layoutSizingHorizontal": "fill",
      "layoutSizingVertical": "hug",
      "itemSpacing": 24,
      "primaryAxisAlignItems": "center",
      "counterAxisAlignItems": "center",
      "children": [
        { "name": "Link", "type": "text", "content": "Product", "fontSize": 14, "fontFamily": "Inter" },
        { "name": "Link", "type": "text", "content": "Pricing", "fontSize": 14, "fontFamily": "Inter" },
        { "name": "Link", "type": "text", "content": "Docs", "fontSize": 14, "fontFamily": "Inter" },
        { "name": "Link", "type": "text", "content": "About", "fontSize": 14, "fontFamily": "Inter" }
      ]
    },
    {
      "name": "CTA",
      "type": "frame",
      "layout": "horizontal",
      "layoutSizingHorizontal": "hug",
      "layoutSizingVertical": "hug",
      "paddingTop": 10,
      "paddingBottom": 10,
      "paddingLeft": 20,
      "paddingRight": 20,
      "cornerRadius": 8,
      "fill": "#3b82f6",
      "primaryAxisAlignItems": "center",
      "counterAxisAlignItems": "center",
      "children": [
        {
          "name": "CTA Label",
          "type": "text",
          "content": "Get started",
          "fontSize": 14,
          "fontFamily": "Inter",
          "fontWeight": 600,
          "fill": "#ffffff"
        }
      ]
    }
  ]
}
```

When Desktop / Layout Control variables exist, replace the numeric padding and spacing with the corresponding path strings.
