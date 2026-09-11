# Size Variables Scheme

Official boilerplate. Two layers: base Schema values, then human-readable Sizes aliases that reference them.

## 1) Base schema values

```json
{
  "variables": {
    "Schema/1": {
      "type": "number",
      "value": 3,
      "description": "Numeric variable for Schema/1"
    },
    "Schema/2": {
      "type": "number",
      "value": 6,
      "description": "Numeric variable for Schema/2"
    },
    "Schema/3": {
      "type": "number",
      "value": 9,
      "description": "Numeric variable for Schema/3"
    },
    "Schema/4": {
      "type": "number",
      "value": 15,
      "description": "Numeric variable for Schema/4"
    },
    "Schema/Spaces/Tesla/2x/2": {
      "type": "number",
      "value": 12,
      "description": "Numeric variable for Schema/Spaces/Tesla/2x/2"
    },
    "Schema/Spaces/Tesla/3x/2": {
      "type": "number",
      "value": 18,
      "description": "Numeric variable for Schema/Spaces/Tesla/3x/2"
    },
    "Schema/5": {
      "type": "number",
      "value": 18,
      "description": "Numeric variable for Schema/5"
    },
    "Schema/Spaces/Tesla/3x/3": {
      "type": "number",
      "value": 27,
      "description": "Numeric variable for Schema/Spaces/Tesla/3x/3"
    },
    "Schema/6": {
      "type": "number",
      "value": 27,
      "description": "Numeric variable for Schema/6"
    },
    "Schema/Spaces/Tesla/2x/4": {
      "type": "number",
      "value": 30,
      "description": "Numeric variable for Schema/Spaces/Tesla/2x/4"
    },
    "Schema/Spaces/Tesla/3x/4": {
      "type": "number",
      "value": 45,
      "description": "Numeric variable for Schema/Spaces/Tesla/3x/4"
    },
    "Schema/7": {
      "type": "number",
      "value": 36,
      "description": "Numeric variable for Schema/7"
    },
    "Schema/Spaces/Tesla/3x/5": {
      "type": "number",
      "value": 54,
      "description": "Numeric variable for Schema/Spaces/Tesla/3x/5"
    },
    "Schema/8": {
      "type": "number",
      "value": 54,
      "description": "Numeric variable for Schema/8"
    },
    "Schema/Spaces/Tesla/3x/6": {
      "type": "number",
      "value": 81,
      "description": "Numeric variable for Schema/Spaces/Tesla/3x/6"
    },
    "Schema/9": {
      "type": "number",
      "value": 72,
      "description": "Numeric variable for Schema/9"
    },
    "Schema/Spaces/Tesla/2x/7": {
      "type": "number",
      "value": 72,
      "description": "Numeric variable for Schema/Spaces/Tesla/2x/7"
    },
    "Schema/Spaces/Tesla/3x/7": {
      "type": "number",
      "value": 108,
      "description": "Numeric variable for Schema/Spaces/Tesla/3x/7"
    },
    "Schema/10": {
      "type": "number",
      "value": 81,
      "description": "Numeric variable for Schema/10"
    },
    "Schema/Spaces/Tesla/2x/8": {
      "type": "number",
      "value": 108,
      "description": "Numeric variable for Schema/Spaces/Tesla/2x/8"
    },
    "Schema/Spaces/Tesla/3x/8": {
      "type": "number",
      "value": 162,
      "description": "Numeric variable for Schema/Spaces/Tesla/3x/8"
    },
    "Schema/11": {
      "type": "number",
      "value": 108,
      "description": "Numeric variable for Schema/11"
    },
    "Schema/Spaces/Tesla/2x/9": {
      "type": "number",
      "value": 144,
      "description": "Numeric variable for Schema/Spaces/Tesla/2x/9"
    },
    "Schema/Spaces/Tesla/3x/9": {
      "type": "number",
      "value": 216,
      "description": "Numeric variable for Schema/Spaces/Tesla/3x/9"
    },
    "Schema/12": {
      "type": "number",
      "value": 216,
      "description": "Numeric variable for Schema/12"
    },
    "Schema/Spaces/Tesla/2x/10": {
      "type": "number",
      "value": 162,
      "description": "Numeric variable for Schema/Spaces/Tesla/2x/10"
    },
    "Schema/Spaces/Tesla/3x/10": {
      "type": "number",
      "value": 243,
      "description": "Numeric variable for Schema/Spaces/Tesla/3x/10"
    },
    "Schema/13": {
      "type": "number",
      "value": 324,
      "description": "Numeric variable for Schema/13"
    },
    "Schema/Spaces/Tesla/2x/12": {
      "type": "number",
      "value": 432,
      "description": "Numeric variable for Schema/Spaces/Tesla/2x/12"
    },
    "Schema/Spaces/Tesla/3x/12": {
      "type": "number",
      "value": 648,
      "description": "Numeric variable for Schema/Spaces/Tesla/3x/12"
    },
    "Schema/Spaces/Tesla/2x/13": {
      "type": "number",
      "value": 648,
      "description": "Numeric variable for Schema/Spaces/Tesla/2x/13"
    },
    "Schema/Spaces/Tesla/3x/13": {
      "type": "number",
      "value": 972,
      "description": "Numeric variable for Schema/Spaces/Tesla/3x/13"
    }
  }
}
```

## 2) Alias layer for human-readable names

```json
{
  "variables": {
    "Sizes/1": {
      "type": "number",
      "value": "Schema/1",
      "description": "Variable reference for Sizes/1"
    },
    "Sizes/2": {
      "type": "number",
      "value": "Schema/2",
      "description": "Variable reference for Sizes/2"
    },
    "Sizes/3": {
      "type": "number",
      "value": "Schema/3",
      "description": "Variable reference for Sizes/3"
    },
    "Sizes/4": {
      "type": "number",
      "value": "Schema/4",
      "description": "Variable reference for Sizes/4"
    },
    "Sizes/5": {
      "type": "number",
      "value": "Schema/5",
      "description": "Variable reference for Sizes/5"
    },
    "Sizes/6": {
      "type": "number",
      "value": "Schema/6",
      "description": "Variable reference for Sizes/6"
    },
    "Sizes/7": {
      "type": "number",
      "value": "Schema/7",
      "description": "Variable reference for Sizes/7"
    },
    "Sizes/8": {
      "type": "number",
      "value": "Schema/8",
      "description": "Variable reference for Sizes/8"
    },
    "Sizes/9": {
      "type": "number",
      "value": "Schema/9",
      "description": "Variable reference for Sizes/9"
    },
    "Sizes/10": {
      "type": "number",
      "value": "Schema/10",
      "description": "Variable reference for Sizes/10"
    },
    "Sizes/11": {
      "type": "number",
      "value": "Schema/11",
      "description": "Variable reference for Sizes/11"
    },
    "Sizes/12": {
      "type": "number",
      "value": "Schema/12",
      "description": "Variable reference for Sizes/12"
    },
    "Sizes/13": {
      "type": "number",
      "value": "Schema/13",
      "description": "Variable reference for Sizes/13"
    },
    "Sizes/2x/2": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/2x/2",
      "description": "Variable reference for Sizes/2x/2"
    },
    "Sizes/3x/2": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/3x/2",
      "description": "Variable reference for Sizes/3x/2"
    },
    "Sizes/3x/3": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/3x/3",
      "description": "Variable reference for Sizes/3x/3"
    },
    "Sizes/2x/4": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/2x/4",
      "description": "Variable reference for Sizes/2x/4"
    },
    "Sizes/3x/4": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/3x/4",
      "description": "Variable reference for Sizes/3x/4"
    },
    "Sizes/3x/5": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/3x/5",
      "description": "Variable reference for Sizes/3x/5"
    },
    "Sizes/3x/6": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/3x/6",
      "description": "Variable reference for Sizes/3x/6"
    },
    "Sizes/2x/7": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/2x/7",
      "description": "Variable reference for Sizes/2x/7"
    },
    "Sizes/3x/7": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/3x/7",
      "description": "Variable reference for Sizes/3x/7"
    },
    "Sizes/2x/8": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/2x/8",
      "description": "Variable reference for Sizes/2x/8"
    },
    "Sizes/3x/8": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/3x/8",
      "description": "Variable reference for Sizes/3x/8"
    },
    "Sizes/2x/9": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/2x/9",
      "description": "Variable reference for Sizes/2x/9"
    },
    "Sizes/3x/9": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/3x/9",
      "description": "Variable reference for Sizes/3x/9"
    },
    "Sizes/2x/10": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/2x/10",
      "description": "Variable reference for Sizes/2x/10"
    },
    "Sizes/3x/10": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/3x/10",
      "description": "Variable reference for Sizes/3x/10"
    },
    "Sizes/2x/12": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/2x/12",
      "description": "Variable reference for Sizes/2x/12"
    },
    "Sizes/3x/12": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/3x/12",
      "description": "Variable reference for Sizes/3x/12"
    },
    "Sizes/2x/13": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/2x/13",
      "description": "Variable reference for Sizes/2x/13"
    },
    "Sizes/3x/13": {
      "type": "number",
      "value": "Schema/Spaces/Tesla/3x/13",
      "description": "Variable reference for Sizes/3x/13"
    }
  }
}
```

## How to use

1. Paste / execute the base Schema first.
2. Paste / execute the Sizes alias layer second.
3. All later typography and layout tokens should reference `Sizes/...` paths.
