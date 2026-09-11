# Inked Colibri Skills

![Inked Colibri — Accelerate your workflow](./assets/banner.png)

**Generate production-ready JSON for the Inked Colibri Figma plugin, using any AI chat.**

- **Variable & Styles Management** — flat JSON for variables and text styles, with binding
- **APCA Color Pairs Generator** — accessible color pairs per color scheme
- **Component Builder** — full component structures as `cmp.json`

This is a plain-Markdown skill (a `SKILL.md` file + reference docs) that teaches an AI assistant the exact rules and JSON schema the Inked Colibri plugin expects. It's not tied to any single AI product — it works anywhere you can give the model text to read.

**Links**
- Figma Plugin: https://www.figma.com/community/plugin/1460728764618520613/inked-colibri-rtc-converter-and-more
- Documentation: https://inked-colibri.narek.ch/
- YouTube: https://www.youtube.com/@inkedcolibri
- LinkedIn: https://www.linkedin.com/company/inked-colibri

---

## How to use in regular AI chats

This skill is plain Markdown — there's no package manager, no install script. "Using" it means giving the files to an AI chat so it can follow the rules.

### Step by step (works everywhere — ChatGPT, DeepSeek, Claude, Gemini, Mistral, etc.)

Some chats (DeepSeek, plain ChatGPT, most others) can't open a GitHub link or read a repo on their own — you have to paste the actual text in. This method works on every chat that accepts a long message:

1. Open `inked-colibri-skills/SKILL.md` in this repo and copy its full contents.
2. Paste it as your **first message** in a new chat (or into the system prompt / custom instructions field, if the tool has one).
3. Depending on what you're asking for, also copy-paste the matching reference file into the same chat, right after `SKILL.md`:
   - **Variables, text styles, size/type/layout schemes** → paste `references/core-rules.md` plus the relevant scheme file (`size-scheme.md`, `typography-scheme.md`, `layout-scheme.md`, or `layout-extended.md`)
   - **Colors / APCA pairs** → paste `references/rtc-color-system.md`
   - **Components (`cmp.json`)** → paste `references/builder-critical-rules.md`, `references/builder-schema.md`, `references/builder-supported.md`, and `references/builder-examples.md`
   - **Components using RTC colors** → add `references/rtc-color-system.md` on top of the Builder files above
4. Now type your actual request — see **Commands** below.

**If the chat starts ignoring the rules** (long conversations drift), start a fresh chat and re-paste `SKILL.md` + the relevant reference file at the top — don't just scroll up and remind it.

### Tools that support file/folder upload

If your tool has a "Skills", "Knowledge", or "Project files" feature (Claude Skills or Projects, Custom GPTs, Gemini Gems, Cursor/Windsurf-style `@file` references), you can upload or attach the `inked-colibri-skills/` folder directly instead of copy-pasting. It works the same way — the AI just reads the files from there instead of from your message.

### RTC path quick rule

When colors are involved, one rule trips people up more than any other:

| Mode | Path form | Example |
|------|-----------|---------|
| **Manager** (variables/styles) | bare — **no** `RTC/` | `primary-shades-dark/primary-85` |
| **Builder** (`fillVar`, `strokeVar`, etc.) | prefixed — **must** include `RTC/` | `RTC/primary-shades-dark/primary-85` |

Manager is *defining* the variable inside the `RTC` collection, so it doesn't repeat the collection name. Builder is *pointing to* that variable from a component, so it needs the collection name to resolve it — a bare path here fails silently (the color just doesn't apply, no error). See `references/rtc-color-system.md` §1a and §14 for the full explanation.

---

## Commands

```
Generate variables for a primary color system with shades and alpha
Generate APCA color pairs for a brand color scheme
Create a complete size scheme (base + alias) using the Tesla scale
Create typography variables + text styles for a design system
Build a header component with logo, nav and CTA button
Create a card component set (default, hover, selected)
Generate cmp.json for a primary button with icon and loading state
```

The assistant detects whether you need **Manager** output (variables/styles JSON) or **Builder** output (`cmp.json`) and applies the matching rules automatically. Output is clean, valid JSON ready to paste into the Inked Colibri plugin.

---

## Package contents

```
inked-colibri-skills/
├── SKILL.md                          # Main skill instructions
└── references/
    ├── core-rules.md                 # Variable generation rules
    ├── size-scheme.md                # Size base + alias layers
    ├── typography-scheme.md          # Type variables + textStyles
    ├── layout-scheme.md              # Spacing & dimensions
    ├── layout-extended.md            # Breakpoints, containers, grid
    ├── rtc-color-system.md           # Reactive Color Variable structure
    ├── builder-schema.md             # cmp.json structure
    ├── builder-primitives.md         # Supported primitives
    ├── builder-supported.md          # Supported properties
    ├── builder-critical-rules.md     # Hard rules for Builder
    └── builder-examples.md           # Ready-to-adapt examples
assets/
└── banner.png                        # Repo banner
```

---

## License

MIT – free to use, modify and share.

---

## Credits

Design system & plugin: **Inked Colibri**
