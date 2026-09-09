# slidev-theme-greenfield

A dark, high-tech **Slidev** theme for agentic-engineering talks — an animated grid + aurora
stage, a single signal-green accent, **Space Grotesk / Geist / Geist Mono** type, and
code-first components (terminal, SDD pipeline, agent nodes). Built for the Fwdays Academy
"Agentic Engineering — Greenfield" crash course, but usable for any AI / dev talk.

![16:9 · dark only](https://img.shields.io/badge/16%3A9-dark-25E07C)

## Use it

**Option A — local theme (recommended, no install/publish).**
Copy the `slidev-theme/` folder into your Slidev project (rename it if you like, e.g. `theme/`),
then point your `slides.md` frontmatter at it:

```yaml
---
theme: ./slidev-theme   # relative path to the folder
---
```

**Option B — preview / edit this theme directly.**
From inside this folder:

```bash
npm install     # pulls @slidev/cli
npm run dev      # opens the example.md demo deck
```

`example.md` is a full demo of every layout and component — copy slides out of it as starting
points.

> Requires `@slidev/cli >= 0.48`. The theme is **dark-only** by design.

## Layouts

| `layout:` | Use for |
|---|---|
| `cover` | Title / opener. Frontmatter: `brand:`, `tag:`. Content bottom-aligned, 92px title. |
| `default` | Standard content slide (eyebrow + heading + body/components). |
| `section` | Big statement / section break — vertically centered, balanced 72px headline. |
| `center` | Fully centered content (stat rows, single ideas). |
| `end` | Closing slide with brand footer. Frontmatter: `brand:`. |

A persistent animated **stage** (grid + aurora) sits behind every slide via `global-bottom.vue`;
a corner brand mark + page number ride on top via `global-top.vue` (hidden on cover/section/center/end).

## Components (auto-imported in any slide)

- **`<GfEyebrow>`** — mono uppercase kicker. `prefix="// "` by default.
- **`<GfBadge tone variant dot>`** — status / phase pill. tones: `green cyan violet amber rose neutral`; variants: `soft solid outline`.
- **`<GfStat value label sublabel accent gradient>`** — oversized metric.
- **`<GfTerminal title accent glow :lines>`** — shell window. `:lines="[{prompt,text,tone}]"` or default slot.
- **`<GfPipeline :steps :active-index accent>`** — SDD / flow pipeline (`steps=[{label,detail}]`).
- **`<GfAgentNode name role status accent>`** — agent chip. status: `idle running done blocked`.

## Utility classes (use in markdown)

`.grad` · `.grad-orchestra` · `.grad-ember` (gradient-clipped text) · `.glow-text` ·
`.mono` · `.muted` · `.faint`. UnoCSS utilities (`grid`, `flex`, `gap-*`, …) work too —
Slidev ships UnoCSS.

Example title:

```md
# Agentic<br><span class="grad-orchestra">Engineering</span>
```

## Theme config

Set in `package.json › slidev.defaults` (canvas 1280×720, 16:9, Geist/Geist Mono, dark).
Override per-deck in your `slides.md` headmatter, e.g. `canvasWidth`, `fonts`.

## Fonts & icons

- **Fonts** auto-import from Google Fonts (Geist, Geist Mono, Space Grotesk).
- **Icons**: components ship their own inline SVGs (no icon pack required). If you want Lucide
  glyphs in your own slides, use `<lucide-name />` — Slidev auto-installs `@iconify-json/lucide`.

## Notes / caveats

- Dark-only (`colorSchema: dark`). No light variant yet — ask if you need one.
- The brand mark is a generic "sprout" glyph; swap in the real logo by editing
  `global-top.vue` / `layouts/cover.vue` / `layouts/end.vue`.
- This theme mirrors the **Greenfield Agentic Deck System** design tokens 1:1
  (`styles/_tokens-*.css` are copies of the system's `tokens/`), so HTML mocks and Slidev
  slides stay visually identical.
