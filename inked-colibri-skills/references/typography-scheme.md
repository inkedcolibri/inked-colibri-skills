# Typography Variables + Text Styles Scheme

Official boilerplate. First create the Type variables (many of which reference Sizes), then create the textStyles that bind to those Type variables.

## 1) Base type variables

```json
{
  "variables": {
    "Type/Font Family/Primary": {
      "type": "string",
      "value": "Arial",
      "description": "String variable for Type/Font Family/Primary"
    },
    "Type/Font Family/Secondary": {
      "type": "string",
      "value": "Georgia",
      "description": "String variable for Type/Font Family/Secondary"
    },
    "Type/Font Weight/Regular": {
      "type": "number",
      "value": 400,
      "description": "Numeric variable for Type/Font Weight/Regular"
    },
    "Type/Font Weight/Bold": {
      "type": "number",
      "value": 700,
      "description": "Numeric variable for Type/Font Weight/Bold"
    },
    "Type/Font Weight/Black": {
      "type": "number",
      "value": 900,
      "description": "Numeric variable for Type/Font Weight/Black"
    },
    "Type/Font Size/Caption": {
      "type": "number",
      "value": "Sizes/2x/2",
      "description": "Variable reference for Type/Font Size/Caption"
    },
    "Type/Font Size/Body": {
      "type": "number",
      "value": "Sizes/5",
      "description": "Variable reference for Type/Font Size/Body"
    },
    "Type/Font Size/Subtitle": {
      "type": "number",
      "value": "Sizes/6",
      "description": "Variable reference for Type/Font Size/Subtitle"
    },
    "Type/Font Size/Title": {
      "type": "number",
      "value": "Sizes/7",
      "description": "Variable reference for Type/Font Size/Title"
    },
    "Type/Font Size/Medium Title": {
      "type": "number",
      "value": "Sizes/8",
      "description": "Variable reference for Type/Font Size/Medium Title"
    },
    "Type/Font Size/Big Title": {
      "type": "number",
      "value": "Sizes/9",
      "description": "Variable reference for Type/Font Size/Big Title"
    },
    "Type/Font Size/Huge Title": {
      "type": "number",
      "value": "Sizes/11",
      "description": "Variable reference for Type/Font Size/Huge Title"
    },
    "Type/Line Height/Caption": {
      "type": "number",
      "value": "Sizes/4",
      "description": "Variable reference for Type/Line Height/Caption"
    },
    "Type/Line Height/Body": {
      "type": "number",
      "value": 27,
      "description": "Numeric variable for Type/Line Height/Body"
    },
    "Type/Line Height/Subtitle": {
      "type": "number",
      "value": 36,
      "description": "Numeric variable for Type/Line Height/Subtitle"
    },
    "Type/Line Height/Title": {
      "type": "number",
      "value": 50,
      "description": "Numeric variable for Type/Line Height/Title"
    },
    "Type/Line Height/Medium Title": {
      "type": "number",
      "value": 67,
      "description": "Numeric variable for Type/Line Height/Medium Title"
    },
    "Type/Line Height/Big Title": {
      "type": "number",
      "value": 81,
      "description": "Numeric variable for Type/Line Height/Big Title"
    },
    "Type/Line Height/Huge Title": {
      "type": "number",
      "value": 120,
      "description": "Numeric variable for Type/Line Height/Huge Title"
    },
    "Type/Letter Spacing/Tight": {
      "type": "number",
      "value": -0.5,
      "description": "Numeric variable for Type/Letter Spacing/Tight"
    },
    "Type/Letter Spacing/Wide": {
      "type": "number",
      "value": 0.5,
      "description": "Numeric variable for Type/Letter Spacing/Wide"
    },
    "Type/Letter Spacing/Default": {
      "type": "number",
      "value": 0.29,
      "description": "Numeric variable for Type/Letter Spacing/Default"
    }
  }
}
```

## 2) Text style boilerplate

```json
{
  "textStyles": {
    "Primary/Regular/Caption": {
      "fontFamily": "Type/Font Family/Primary",
      "fontWeight": "Type/Font Weight/Regular",
      "fontSize": "Type/Font Size/Caption",
      "letterSpacing": "Type/Letter Spacing/Default",
      "lineHeight": "Type/Line Height/Caption"
    },
    "Primary/Regular/Body": {
      "fontFamily": "Type/Font Family/Primary",
      "fontWeight": "Type/Font Weight/Regular",
      "fontSize": "Type/Font Size/Body",
      "letterSpacing": "Type/Letter Spacing/Wide",
      "lineHeight": "Type/Line Height/Body"
    },
    "Primary/Regular/Subtitle": {
      "fontFamily": "Type/Font Family/Primary",
      "fontWeight": "Type/Font Weight/Regular",
      "fontSize": "Type/Font Size/Subtitle",
      "letterSpacing": "Type/Letter Spacing/Default",
      "lineHeight": "Type/Line Height/Subtitle"
    },
    "Primary/Regular/Title": {
      "fontFamily": "Type/Font Family/Primary",
      "fontWeight": "Type/Font Weight/Regular",
      "fontSize": "Type/Font Size/Title",
      "letterSpacing": "Type/Letter Spacing/Default",
      "lineHeight": "Type/Line Height/Title"
    },
    "Primary/Regular/Medium Title": {
      "fontFamily": "Type/Font Family/Primary",
      "fontWeight": "Type/Font Weight/Regular",
      "fontSize": "Type/Font Size/Medium Title",
      "letterSpacing": "Type/Letter Spacing/Default",
      "lineHeight": "Type/Line Height/Medium Title"
    },
    "Primary/Regular/Big Title": {
      "fontFamily": "Type/Font Family/Primary",
      "fontWeight": "Type/Font Weight/Regular",
      "fontSize": "Type/Font Size/Big Title",
      "letterSpacing": "Type/Letter Spacing/Default",
      "lineHeight": "Type/Line Height/Big Title"
    },
    "Primary/Regular/Huge Title": {
      "fontFamily": "Type/Font Family/Primary",
      "fontWeight": "Type/Font Weight/Regular",
      "fontSize": "Type/Font Size/Huge Title",
      "letterSpacing": "Type/Letter Spacing/Default",
      "lineHeight": "Type/Line Height/Huge Title"
    },
    "Primary/Bold/Caption": {
      "fontFamily": "Type/Font Family/Primary",
      "fontWeight": "Type/Font Weight/Bold",
      "fontSize": "Type/Font Size/Caption",
      "letterSpacing": "Type/Letter Spacing/Default",
      "lineHeight": "Type/Line Height/Caption"
    },
    "Primary/Bold/Body": {
      "fontFamily": "Type/Font Family/Primary",
      "fontWeight": "Type/Font Weight/Bold",
      "fontSize": "Type/Font Size/Body",
      "letterSpacing": "Type/Letter Spacing/Default",
      "lineHeight": "Type/Line Height/Body"
    },
    "Primary/Bold/Subtitle": {
      "fontFamily": "Type/Font Family/Primary",
      "fontWeight": "Type/Font Weight/Bold",
      "fontSize": "Type/Font Size/Subtitle",
      "letterSpacing": "Type/Letter Spacing/Default",
      "lineHeight": "Type/Line Height/Subtitle"
    },
    "Primary/Bold/Title": {
      "fontFamily": "Type/Font Family/Primary",
      "fontWeight": "Type/Font Weight/Bold",
      "fontSize": "Type/Font Size/Title",
      "letterSpacing": "Type/Letter Spacing/Default",
      "lineHeight": "Type/Line Height/Title"
    },
    "Primary/Bold/Medium Title": {
      "fontFamily": "Type/Font Family/Primary",
      "fontWeight": "Type/Font Weight/Bold",
      "fontSize": "Type/Font Size/Medium Title",
      "letterSpacing": "Type/Letter Spacing/Default",
      "lineHeight": "Type/Line Height/Medium Title"
    },
    "Primary/Bold/Big Title": {
      "fontFamily": "Type/Font Family/Primary",
      "fontWeight": "Type/Font Weight/Bold",
      "fontSize": "Type/Font Size/Big Title",
      "letterSpacing": "Type/Letter Spacing/Default",
      "lineHeight": "Type/Line Height/Big Title"
    },
    "Primary/Bold/Huge Title": {
      "fontFamily": "Type/Font Family/Primary",
      "fontWeight": "Type/Font Weight/Bold",
      "fontSize": "Type/Font Size/Huge Title",
      "letterSpacing": "Type/Letter Spacing/Default",
      "lineHeight": "Type/Line Height/Huge Title"
    },
    "Primary/Black/Caption": {
      "fontFamily": "Type/Font Family/Primary",
      "fontWeight": "Type/Font Weight/Black",
      "fontSize": "Type/Font Size/Caption",
      "letterSpacing": "Type/Letter Spacing/Default",
      "lineHeight": "Type/Line Height/Caption"
    },
    "Primary/Black/Body": {
      "fontFamily": "Type/Font Family/Primary",
      "fontWeight": "Type/Font Weight/Black",
      "fontSize": "Type/Font Size/Body",
      "letterSpacing": "Type/Letter Spacing/Default",
      "lineHeight": "Type/Line Height/Body"
    },
    "Secondary/Regular/Body": {
      "fontFamily": "Type/Font Family/Secondary",
      "fontWeight": "Type/Font Weight/Regular",
      "fontSize": "Type/Font Size/Body",
      "letterSpacing": "Type/Letter Spacing/Wide",
      "lineHeight": "Type/Line Height/Body"
    }
  }
}
```

## How to use

1. Execute the Type variables first (they depend on the Size scheme).
2. Execute the textStyles second.
3. All fontSize / lineHeight values that can reference Sizes should do so.
