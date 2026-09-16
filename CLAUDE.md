# Brigid House

A single-page static site (hand-coded HTML/CSS/JS, no build step, no framework) for the Brigid House new-construction build-diary brand — deployed via GitHub Pages at `itschampton/brigidhouse`, domain `brigidhouse.com`.

## Design system

Use the **Chalk & Celadon** design system for all UI work: https://claude.ai/artifact/7MriZ1ndDLrUg7pjGAWew6

Before making UI changes, read `project/README.md` and `project/tokens.json` from that artifact (via the Artifact tool's `read_file` action) for the full rationale and current token values — this file is a working summary, the artifact is the source of truth.

### Semantic tokens (light / dark)

| Token | Light | Dark | Use |
|---|---|---|---|
| `ground` | `#FBF8F2` (Chalk) | `#2F3A40` (Ink) | Page background |
| `surface` | `#F1EBE1` (Shell) | `#3A464D` | Cards, bands, stripes |
| `text` | `#2F3A40` (Ink) | `#FBF8F2` (Chalk) | Body copy |
| `text-muted` | `#6F6A61` (Stone) | `#B2AFA6` | Captions, secondary text (keep 18px+ on dark `surface`) |
| `border` | `#DFD8CC` (Rule) | `#4E5A61` | Card outlines, section rules — decorative only |
| `hairline` | `rgba(47,58,64,.16)` | `rgba(251,248,242,.18)` | Dividers within a component |
| `accent` | `#3F5A6B` (Harbor) | `#C3D4DD` (Powder) | Headings, links, primary buttons |
| `on-accent` | `#FBF8F2` | `#2F3A40` | Text/icons on an `accent` fill |
| `eyebrow` | `#4D6353` (Fern) | `#C6D2C4` (Celadon) | Eyebrow / small-caps labels |
| `control-border` | `#8CA893` (Sage) | `#8CA893` | Secondary button outline (2.43:1 on Chalk — pair with a `fern` label) |
| `block-deep` | `#3F5A6B` (Harbor) | `#7B9BB0` (Chambray) | Deep-blue field on inverted bands/covers |

Only `ink`, `harbor`, and `fern` carry text on Chalk. `celadon`, `sage`, `powder`, `chambray`, `honey`, `shell` are fills only. `honey` never sits behind text and never exceeds 2% of a surface. Aim for roughly 57% ivory neutrals, 20% green, 21% blue, 2% honey across a screen.

### Shape & layout

- **Square corners everywhere** — `radius-none` (0). No rounded buttons, cards, or tags.
- **Hairline borders, not shadows** — 1px `border-hairline` separates elements.
- Content column max `68rem`, fluid gutter 20–56px.
- Sections sit `space-7` (80px desktop / 52px mobile) apart; a section head sits `space-5` (28px) above its content.
- Cards: 1px `border` outline, colored chip on top, `ground` body below with its own top rule.

### Type

- **Display/headings** — Marcellus, weight 400 always, balanced wrapping.
- **Body** — Karla (400/500/600).
- **Numbers, hex, specs** — IBM Plex Mono, tabular numerals.
- All three load from Google Fonts.
- `label` style: 11px Karla 600, uppercase, 0.2em tracking, 8–10px above an h2.
- Line-length limits: body 62ch, ledes 56ch, hero lines ~16 characters.

### Voice

- Plain, specific, first person where it's the creator speaking.
- Sentence case for headings/buttons; uppercase only via `label`/`tag` styles.
- No emoji, no exclamation marks, no manufactured casualness, no em dashes (use comma, colon, or period).
- Fine to state a trade-off plainly rather than smoothing it over.

### Accessibility

- Focus ring: 2px solid `accent`, offset 2px.
- Respect the documented contrast pairings above rather than inventing new color-on-color combinations.

## Project structure

- `index.html` / `style.css` / `script.js` — the site itself, no build tooling.
- `.gitignore` excludes `.claude/` (local preview server config, not part of the deployed site).
- Contact form posts to Formspree (`https://formspree.io/f/xjykbnlo`), which forwards submissions to email — no backend of our own.
