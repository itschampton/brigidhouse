# Brigid House

A hand-coded static site (HTML/CSS/JS, no build step, no framework) for the Brigid House new-construction build-diary brand — deployed via GitHub Pages at `itschampton/brigidhouse`, domain `brigidhouse.com`. Two pages: `index.html` (home) and `work-with-me.html` (media kit), sharing one `style.css` and a nav.

## Design system

Use the **Chalk & Celadon** design system for all UI work: https://claude.ai/artifact/7MriZ1ndDLrUg7pjGAWew6

Before making UI changes, read `project/README.md` and `project/tokens.json` from that artifact (via the Artifact tool's `read_file` action) for the full rationale and current token values — this file is a working summary, the artifact is the source of truth.

### Semantic tokens (light / dark)

| Token | Light | Dark | Use |
|---|---|---|---|
| `ground` | `#FBF8F2` (Chalk) | `#2F3A40` (Ink) | Page background |
| `surface` | `#F1EBE1` (Shell) | `#3A464D` | Cards, bands, stripes |
| `text` | `#2F3A40` (Ink) | `#FBF8F2` (Chalk) | Body copy |
| `text-muted` | `#6F6A61` (Stone) | `rgba(251,248,242,.72)` (off-white) | Captions, secondary text |
| `border` | `#DFD8CC` (Rule) | `#4E5A61` | Card outlines, section rules — decorative only |
| `hairline` | `rgba(47,58,64,.16)` | `rgba(251,248,242,.18)` | Dividers within a component |
| `accent` | `#3F5A6B` (Harbor) | `#C3D4DD` (Powder) | Headings, links, primary buttons |
| `on-accent` | `#FBF8F2` | `#2F3A40` | Text/icons on an `accent` fill |
| `block-deep` | `#3F5A6B` (Harbor) | `#7B9BB0` (Chambray) | Deep-blue field on inverted bands/covers |
| `off-white` | `#FBF8F2` | *(same value)* | Alias of Chalk, added for this project. Used at 72% opacity as dark-mode `text-muted` (see below) rather than a flat hex, so muted text stays visibly dimmer than full-white `text` — don't use it at full opacity for text, only for the `ring` treatment or as a literal background. |
| `ring` | `#C3D4DD` (Powder) | *(same value, not theme-swapped)* | Fixed decorative ring color around the About Me portrait — see Shape & layout. |

**Project overrides from the system default:**
- `eyebrow` is set to the same value as `accent` (`#3F5A6B` Harbor light / `#C3D4DD` Powder dark), not the system default Fern/Celadon green. The owner prefers a blue-forward palette over the system's default green-and-blue mix — labels, links and buttons all read as one blue rather than splitting across green and blue. Green tokens (`fern`, `sage`, `celadon`) are unused on this site; keep new UI blue-accented, not green, unless asked otherwise.
- Dark-mode `text-muted` was changed from Stone-analog `#B2AFA6` to a 72%-opacity off-white, at the owner's request for a lighter, airier feel in dark mode. Light mode keeps Stone (`#6F6A61`) unchanged — full off-white text on the light `ground` would be unreadable, so this swap is dark-mode only.

### Shape & layout

- **Square corners, with two deliberate exceptions**, both at the owner's explicit request — don't extend rounding beyond these without asking:
  - The About Me portrait photo is circular with a two-stroke `ring` border (`box-shadow: 0 0 0 3px ring, 0 0 0 5px ground, 0 0 0 7px ring`).
  - Buttons (`.btn`) use a 2px `border-radius`, not `radius-none`. Everything else — cards, tags, form fields — stays square.
- **Hairline borders, not shadows** — 1px `border-hairline` separates elements.
- Content column max `68rem`, fluid gutter 20–56px.
- Sections sit `space-7` (80px desktop / 52px mobile) apart; a section head sits `space-5` (28px) above its content.
- Cards: 1px `border` outline, colored chip on top, `ground` body below with its own top rule.

### Type

- **Display/headings** — **Fraunces** (variable, `opsz,wght@9..144`), weight 400 always, balanced wrapping. Swapped from Marcellus at the owner's request — she wanted more period character for the "2026 like it's 1926" branding.
- **Body and labels** — **Public Sans** (400/500/600), replacing Karla. Chosen deliberately for both roles: body copy and the small uppercase `label`/eyebrow style (e.g. "About me", "Get in touch", "Media kit") both use Public Sans — there's no separate label typeface, `label` just applies uppercase/letter-spacing/size on top of the same body font.
- **Numbers, hex, specs** — IBM Plex Mono, tabular numerals.
- All three load from Google Fonts.
- `label` style: 11px Public Sans 600, uppercase, 0.2em tracking, 8–10px above an h2.
- Line-length limits: body 62ch, ledes 56ch, hero lines ~16 characters.

### Voice

- Plain, specific, first person where it's the creator speaking as herself (the About Me heading reads "Hi, I'm Caitlyn." — a "Hi, I'm Brigid House." brand-persona version was tried and reverted, so don't reintroduce it without asking).
- Sentence case for headings/buttons; uppercase only via `label`/`tag` styles.
- No emoji, no exclamation marks, no manufactured casualness, no em dashes (use comma, colon, or period).
- Fine to state a trade-off plainly rather than smoothing it over.
- Core identity to keep surfacing: a millennial mom in Raleigh, building with her husband and toddler son after moving from DC. The build philosophy/tagline is **"Building a house in 2026 like it's 1926"** — craftsman at heart, with a touch of Cape Cod, new construction that's rooted in 1920s historical style rather than a builder-grade modern look. This tagline also runs on the owner's TikTok, so keep it verbatim when it's quoted.
- Strict first person singular (I/my) when describing her own content, work or opinions, e.g. "my floor plan choices," "my biggest video" — not "our"/"we". The one natural exception is references to her actual family unit ("our toddler son," "my husband and I"), where plural is factually correct rather than a voice slip.

### Accessibility

- Focus ring: 2px solid `accent`, offset 2px.
- Respect the documented contrast pairings above rather than inventing new color-on-color combinations.

### Layout pattern ("Quiet Ledger")

- No filled card backgrounds. Sections are separated by a 1px `border` top rule, not a box.
- Form fields are underline-style (bottom border only, transparent background), not boxed inputs.
- Buttons are solid `accent` fills (not outlined) — the owner specifically likes a solid blue button over an outlined one.
- Stat numbers use `mono` with `tabular-nums`; stat tiles get a hairline top rule instead of a card border.
- Percentage breakdowns (demographics) render as thin `accent`-filled bar tracks on a `border`-colored track, with the value in `mono-sm` at the end of the row — not pie charts.
- `work-with-me/index.html` section order: key stats, then "Recent performance" (post list), then "Audience" (demographics), then contact. All posts render at the same visual weight in one `.post-list`, sorted by views descending (including outsized ones like the 2.2M-view post) — no separate "featured" callout box for a standout number, that read as confusing/oversized when tried.

## Project structure

- `index.html` (home: hero image, intro, TikTok link, About Me teaser, contact) and `work-with-me/index.html` (media kit: stats, audience demographics, top posts, contact) — same `style.css` and `script.js`, no build tooling.
- `work-with-me` is a folder (not a `.html` file) specifically so it serves at the clean URL `/work-with-me/` instead of `/work-with-me.html` — GitHub Pages treats any `index.html` as a folder's default document. Follow the same pattern for any future page.
- All asset references (`style.css`, `script.js`, `images/...`) use root-absolute paths (`/style.css`, not `style.css`) on both pages. This is required, not just tidiness — `work-with-me/index.html` lives one directory deeper than `index.html`, so a relative path there would resolve to the wrong location.
- `nav` (wordmark + Home / Work with me links) is duplicated at the top of both pages, also using root-absolute hrefs (`/`, `/work-with-me/`) rather than filenames — there's no templating, so a nav change means editing both files.
- `images/hero.jpg` (banner illustration on the home page, cropped to the content column width via CSS) and `images/portrait.jpg` (About Me headshot, cropped to a circle with the `ring` border via CSS) — cropping happens in CSS, not the source files, so any source aspect ratio works.
- `.gitignore` excludes `.claude/` (local preview server config, not part of the deployed site).
- Contact form (identical on both pages) posts to Formspree (`https://formspree.io/f/xjykbnlo`), which forwards submissions to email — no backend of our own.
- Media kit stats on `work-with-me/index.html` are pulled manually from TikTok analytics screenshots the owner provides, dated in the page header (`Updated <date>`) — there's no live data feed, so refreshing the numbers means editing the HTML directly and updating that date.
- `favicon.svg` (root): a serif "B" in Chambray blue (`#7B9BB0`, fixed, not theme-swapped) on a transparent background, chosen to read on both light and dark browser chrome. Linked via `<link rel="icon" href="/favicon.svg" type="image/svg+xml">` on both pages — no PNG/ICO fallback exists, which is fine for current mainstream browsers but won't show in very old ones.
- Both pages carry Open Graph + Twitter Card meta tags (`og:title`, `og:description`, `og:image`, `twitter:card`) so link previews in texts/social apps show `images/hero.jpg` as the thumbnail. `og:image` must stay an absolute URL (`https://brigidhouse.com/...`) — relative paths don't work for social scrapers. If a page-specific preview image is ever wanted instead of reusing the hero shot everywhere, update `og:image`/`twitter:image` per page.
- Both content images have real, specific alt text (not filler) — keep it that way for any future image: describe what's actually in the photo/illustration.
