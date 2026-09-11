# Inked Colibri Skills

![Inked Colibri — Accelerate your workflow](./assets/banner.png)

**Generate production-ready JSON for the Inked Colibri Figma plugin**
Manager mode → Variables + Text Styles with binding
Builder mode → Complete component structures as `cmp.json`

This skill teaches an AI assistant how to output correct, plugin-ready JSON for the Inked Colibri design system (Token Commander + Component Builder). It's written as plain Markdown with a small YAML header, so it isn't locked to one AI product — see below.

**Links**
- 🔌 Figma Plugin: https://www.figma.com/community/plugin/1460728764618520613/inked-colibri-rtc-converter-and-more
- 📚 Documentation: https://inked-colibri.narek.ch/
- ▶️ YouTube: https://www.youtube.com/@inkedcolibri
- 💼 LinkedIn: https://www.linkedin.com/company/inked-colibri

---

## Is this AI-agnostic?

**Yes.** The skill itself (`SKILL.md` + `references/*.md`) is just Markdown instructions with a YAML frontmatter block (`name` + `description`). There is nothing Grok-specific, Claude-specific, or ChatGPT-specific inside those files — no proprietary syntax, no platform API calls. Any assistant that can read a block of text as instructions can follow it.

What *does* differ between platforms is the **install mechanism** — i.e., how you get the file's content in front of the model:

| Platform | Native "skill/file upload" support | Notes |
|---|---|---|
| **Grok** | Yes — Skills feature (upload zip/folder) | Original packaging target; see below |
| **Claude** (claude.ai / API) | Yes — Skills (Settings → Capabilities → Skills, or Projects) | Upload the `inked-colibri-skills` folder as-is |
| **ChatGPT** | Partial — via Custom GPT "Knowledge" files or Projects | Upload `SKILL.md` + `references/` as knowledge files |
| **Any other chatbot / local LLM** | Manual | Paste `SKILL.md` (and relevant reference file) into the system prompt or first message |

In short: the *content* is portable everywhere; only the *upload step* changes.

---

## What this skill does

| Mode     | Trigger words                                      | Output                                      |
|----------|----------------------------------------------------|---------------------------------------------|
| **Manager** | variables, styles, size scheme, typography, layout, binding | Flat JSON with `"variables"` and/or `"textStyles"` |
| **Builder** | component, header, button, card, nav, cmp.json, "build me a …" | Valid `cmp.json` ready for the Component Builder |

The assistant automatically detects which mode you need and applies the correct rules and reference schemes.

---

## How to install

### Claude (claude.ai, Claude Desktop, or API/Projects)

1. Download this repository (or just the `inked-colibri-skills/` folder) as a zip.
2. In claude.ai: go to **Settings → Capabilities → Skills** (naming may vary by plan) and upload the `inked-colibri-skills` folder/zip. In a **Project**, you can instead drop the folder into the Project's knowledge files.
3. Once added, reference it naturally in chat — Claude will pull in the relevant reference file automatically based on your request.

### Grok

**Option A – Upload zip (easiest)**
1. Download the latest release zip from this repository (or download the `inked-colibri-skills` folder as zip).
2. Go to [grok.com](https://grok.com) → **Skills**.
3. Click **New Skill** → **Upload** / **Import**.
4. Select the zip (or the `inked-colibri-skills` folder).
5. The skill appears under **Personal** as `inked-colibri-skills`.

**Option B – Manual copy**
1. Clone or download this repository.
2. Copy the entire `inked-colibri-skills/` folder into your Grok skills directory:
   - User skills: `~/.grok/skills/` (or `/home/workdir/.grok/skills/` in the Grok sandbox)
3. Restart the conversation or type `/` and look for the skill.

If you have a paid Grok account you can also publish the skill and get a direct link:

```
https://grok.com/skill-link/0c002c50ee8d91873c2b9720cb1fd93f
```

(Requires SuperGrok / paid access to install from skill-link — the zip/GitHub method above works for free accounts too.)

### ChatGPT

ChatGPT doesn't have a "Skills" system identical to Claude/Grok, but you can get equivalent behavior:

1. Create a **Custom GPT** (or use a **Project**).
2. Under **Knowledge**, upload `SKILL.md` and the files inside `references/`.
3. In the Custom GPT's **Instructions** field, add a short pointer such as: *"When asked for Inked Colibri variables, styles, or components, follow the rules in the uploaded SKILL.md and the matching file in references/."*
4. Save, then prompt it the same way described below.

### Any other AI (Gemini, local LLMs, etc.) — manual method

This always works, regardless of platform:

1. Open `inked-colibri-skills/SKILL.md`.
2. Paste its full contents at the start of your conversation (or into a system prompt, if the tool supports one).
3. When you need a specific reference file (e.g. `rtc-color-system.md` for colors), paste that file's contents into the same conversation before asking your question.
4. Ask your request normally — see examples below.

---

## How to use

Once installed (on any platform), invoke it naturally:

```
Use the inked-colibri-skills skill and generate a size scheme based on Tesla scale
```

or just describe what you need directly:

```
Generate variables for a primary color system with shades and alpha
Create a card component set with header, body and actions
```

### Manager mode examples

```
Generate a complete size scheme (base + alias) using the official Tesla scale
Create typography variables + text styles for a design system
Build layout spacing tokens + extended breakpoints
Generate RTC color variables for brand/primary with shades, dark shades and alpha
```

### Builder mode examples

```
Build a header component with logo, nav and CTA button
Create a card component set (default, hover, selected)
Generate cmp.json for a primary button with icon and loading state
```

The assistant will output clean, valid JSON that you can paste directly into the Inked Colibri Manager or Component Builder.

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

## Banner text suggestions (for docs / website)

You can replace the current banner text with any of these:

**Short**
```
Skip the boring setup.
Generate design-system JSON with AI.
```

**Medium**
```
Accelerate your design system.
Variable & Styles Management • APCA Color Pairs per Scheme • Component Builder
```

**Focused on the skill**
```
Inked Colibri
One skill. Two modes.
Manager → Variables & Styles
Builder → Complete Components
```

**Call-to-action**
```
Install the free skill
and generate production-ready tokens & components in seconds.
```

---

## License

MIT – free to use, modify and share.

---

## Credits

- Design system & plugin: **Inked Colibri**
- Skill packaging: community contribution

## Links

- Figma Plugin: https://www.figma.com/community/plugin/1460728764618520613/inked-colibri-rtc-converter-and-more
- Documentation: https://inked-colibri.narek.ch/
- YouTube: https://www.youtube.com/@inkedcolibri
- LinkedIn: https://www.linkedin.com/company/inked-colibri
