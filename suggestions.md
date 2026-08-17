# Personal Academic Website Suggestions

Case study: **Alexander Panfilov's site**, https://kotekjedi.github.io/ (research
section: `#research`). Analyzed from the live HTML/CSS on 2026-08-17.

Important context up front: despite looking like it could be al-folio, this site is
**not** al-folio or even Jekyll — it's a single hand-built `index.html` (footer literally
says *"Vibe-coded with CodeX. Last updated Apr 08, 2026."*), one long page with anchors
`#news` and `#research`, custom CSS (`assets/styles.css`), Google Fonts (Space Grotesk),
Font Awesome via CDN, a JSON-LD `Person`/`ScholarlyArticle` schema block, Google Analytics
(gtag) and GoatCounter. That framing matters: several things it does well are "what a
minimal single-page site can do that al-folio's multi-page structure doesn't force you to
think about," and a few things it's missing are exactly what al-folio gives you for free.

---

## 1. Overall structure / navigation / information architecture

**What it does:**
- Everything lives on one page (`/`) with two nav links, `News` and `Research`, that
  scroll-jump via `#news` / `#research` anchors (`html { scroll-behavior: smooth; }`).
  No CV page, no separate publications page, no teaching/projects/blog.
- Order top to bottom: hero (name, affiliation, tagline, socials, bio, CTA buttons) →
  "My current..." panel (3 short cards: Research Interests / Whereabouts / Plans) →
  News timeline → Research/publications → Acknowledgements → footer.

**Assessment:**
- For a single researcher with 5 papers and no separate teaching/project material, a
  single scrolling page removes friction — there's no click-through to a sparse CV page
  or an empty "Portfolio" page (a common al-folio failure mode when someone leaves default
  nav items live). Every nav item on this site has real content behind it.
- The "My current..." panel (Research Interests / Whereabouts / Plans) is a good, distinctive
  pattern — it's essentially a lightweight, always-fresh "now page" that a static CV/bio
  can't offer. It signals openness to collaboration and current location without
  requiring a reader to dig through prose. **Worth borrowing** for an al-folio `about.md`:
  al-folio supports a similar "news"-style include; a compact 3-card "current status" block
  above or beside the bio would translate directly.
- The weak spot: there's no dedicated **CV page** — "Download CV" only opens a PDF
  (`assets/pdf/cv.pdf`) in a new tab. There's no HTML-rendered CV, so it's not searchable,
  not indexable by Google, and not skimmable on mobile without a PDF viewer. Al-folio's
  built-in `cv.md` (rendered from `_data/cv.yml`) is a genuine advantage here — a
  Weckbecker-style site that already has an HTML CV page is strictly better on this axis
  and should keep it rather than regress to a PDF-only link.
- No "Projects" or "Teaching" section at all — fine for this specific researcher's stage
  (3rd-year PhD, no teaching yet), but a caution for anyone adapting this pattern: don't
  keep nav items (Projects, Teaching, Blog) that lead to skeletal or default-demo pages.
  Trim nav to only sections with real content, exactly as this site does.

---

## 2. How research/publications are presented

**What it does (concretely, from the HTML):**
Each of the 5 publications is a `.publication-card` with:
- a **thumbnail image** specific to the paper (e.g. `assets/img/publications/monitor.png`,
  `assets/img/publications/scaling.png`) rather than a generic placeholder,
- a venue/year line (`ICLR 2026`, `ICML 2025`, `Preprint`),
- the paper title linking straight to arXiv/proceedings,
- an author list with the site owner's own name wrapped in
  `<span class="author-self">` and bold/highlighted (a nice touch — makes scanning
  multi-author lists easy) and shared-first-authorship marked with `*`,
- action buttons: **Paper**, **Code**, and toggle buttons for **Abstract** and **BibTeX**
  that expand inline (`data-toggle-target`, JS toggles a `.toggle-panel`, and opening one
  auto-closes the other so Abstract/BibTeX don't stack),
- full abstract text and a ready-to-copy BibTeX block, generated to match the paper's
  actual bibkey (`panfilov2026claudini`, etc.).

**Assessment — strong points worth copying into an al-folio site:**
- **Toggleable abstract + BibTeX right on the listing** is exactly what al-folio's
  `_layouts/bib.html` / jekyll-scholar already supports (`enable_bib_dashboard` /
  `toggle_abstract`, etc.) — if not already turned on, this is direct evidence it's worth
  enabling: a reader doesn't have to leave the page or open a separate `.bib` file to get
  the citation.
- **Self-authorship highlighting in multi-author bylines** — jekyll-scholar can bold the
  configured author name via `_config.yml`'s `scholar.details_dir` / name-matching, but
  it's easy to leave off. Explicitly confirm the maintained site does this; it materially
  helps a reader scanning a 9-author paper find which name is the page owner.
- **Per-paper cover image** instead of a generic journal/conference icon makes the
  research section feel far less like a bare list and more like a portfolio. Each image
  is a genuinely distinct figure (a Pareto front, a scaling curve, etc.) pulled from the
  paper, not stock art.
- Every publication has an outbound **Code** or **Website** link in addition to Paper —
  worth checking that all `_bibliography/papers.bib` entries have `code`/`website` fields
  populated where repos exist, since incomplete link coverage is a common gap.

**Assessment — weaknesses:**
- Reverse-chronological order is implicit from file order, same constraint noted in this
  repo's own CLAUDE.md notes about `papers.bib` ordering — nothing new, but confirms that
  convention (newest first) is the norm worth following.
- No filtering/tagging by topic (e.g. "red-teaming" vs "interpretability" vs
  "alignment") even though the papers span distinct sub-areas — at 5 papers this doesn't
  matter yet, but al-folio's publications page supports `related_publications` and
  category grouping; worth having that switched on before the list grows past ~10 entries
  so it doesn't get flattened.
- No citation counts / Google Scholar badge inline (only a top-level Scholar link) — minor,
  but al-folio's scholar integration can surface citation counts per entry, which this
  site doesn't use.
- One publication (`Claudini...`) cites `datePublished: 2026` for a *preprint* dated
  ahead of the analysis date context — a reminder to double check that preprint/venue
  years are correct at publish time, since these dates get baked into BibTeX others will
  copy-paste.

---

## 3. Visual design, typography, whitespace, color

- Single font family throughout: Google Fonts "Space Grotesk" (400/500/600 weights) with
  system-font fallback, no serif/mono mixing — clean and consistent, but a bit flat for a
  research site since there's no visual distinction between prose (bio) and structured
  data (BibTeX). BibTeX blocks are just `<pre><code>` with no monospace font declared
  beyond the browser default — a monospace font stack for `.pub-bibtex` would read better.
- Color palette is a tight, restrained set of CSS custom properties: `--accent: #2f4bff`,
  `--bg: #f7f8fc`, `--text: #191b2c`, `--muted: #5a607d`, applied consistently to links,
  highlighted conference/event names (`.highlight`), and buttons (`.pill-button`). This
  restraint is good practice — most al-folio customizations that go wrong do so by adding
  too many one-off colors instead of theming through variables like this.
- **No dark mode.** `:root { color-scheme: light; }` is hardcoded and there's no
  `prefers-color-scheme` media query or toggle anywhere in `styles.css`. This is a real
  regression compared to al-folio, which ships dark mode by default — worth explicitly
  calling out as something *not* to imitate. Keep al-folio's dark-mode toggle rather than
  stripping it for a "cleaner" custom build.
- Layout uses generous whitespace via a `.page-shell` max-width (1770px, quite wide for a
  personal site — on an ultra-wide monitor lines of prose in the hero section run very
  long, which hurts readability; al-folio's narrower content column is actually better
  for line length even though it looks "smaller").
- Sticky nav with `backdrop-filter: blur(18px)` — nice modern touch, cheap to add to any
  theme's nav bar CSS.
- Pill-shaped buttons (`.pill-button`) used consistently for CTAs, paper/code links, and
  abstract/bibtex toggles — visually unifies very different actions (external link vs.
  in-page toggle) under one button style, which is good but can also mildly mislead users
  about which buttons navigate away vs. expand in place; consider a subtle icon
  differentiation (e.g. an external-link icon) if adopting this pattern.

---

## 4. Content clarity — bio, research statement, CV

- The bio is four short, punchy paragraphs, informal register ("Yo! My name is Sasha...",
  "Roughly four days a week I am an AI doomer.") — distinctive voice, but a risk: informal
  humor like "AI doomer" dates quickly and may read oddly to a hiring committee or
  collaborator unfamiliar with the register. A middle ground — one informal line, rest
  professional — is safer for a site meant to last years.
- Research interests are stated **twice** in slightly different words: once in the hero
  bio paragraph ("red-teaming LLMs and stuff around them... red-teaming for AI Control and
  Automated RnD") and again in the "Research Interests" card ("introspection and its
  implications for AI Control, automated R&D, and white-box alignment methods"). Minor
  redundancy — a single canonical research-interests sentence, referenced once, would be
  tighter.
- "Whereabouts" and "Plans" cards are a nice, concrete touch (names actual cities/events:
  Tübingen, London, Bay Area, ICLR 2026 in Brazil) — far more useful to a reader deciding
  whether to reach out than a generic "open to collaboration" line.
- CV is PDF-only (`assets/pdf/cv.pdf`) with no HTML equivalent — flagged already in
  §1; repeating here because it's the single biggest content-clarity gap. A PDF CV can't
  be quoted, isn't findable by on-page search, and doesn't render on very narrow phone
  screens without pinch-zooming.
- Acknowledgements section is a genuinely nice, humane touch — naming mentors/collaborators
  by name with links to their Scholar profiles. Uncommon on personal sites, costs little,
  and reads well. Worth considering for an al-folio `about.md` if there are mentors worth
  crediting.

---

## 5. SEO / meta basics

- `<title>Alexander Panfilov</title>` — short and correct, but generic; doesn't include
  the field (e.g. "Alexander Panfilov — AI Safety Research") which would help in search
  result snippets and browser tab disambiguation when many tabs are open.
- `<meta name="description" content="AI safety, Adversarial ML, & LLM Red-Teaming">` is
  present and reasonably specific — good baseline, better than leaving it blank as many
  personal sites do.
- No Open Graph (`og:title`, `og:image`, `og:description`) or Twitter Card meta tags at
  all — sharing the URL on Slack/Twitter/LinkedIn will produce a bare link with no
  preview image or summary. This is a concrete, easy win to flag: al-folio's default
  `_includes/head.html` / `_includes/metadata.html` already emits OG tags if
  `og_image`/`social_preview` fields are filled in — make sure they actually are, since
  it's a common thing left blank after cloning the theme.
- Good: a full `application/ld+json` **schema.org `Person`** block with `sameAs` links
  (Scholar, X, LinkedIn, GitHub), `jobTitle`, `affiliation`, and even a nested
  `publication` array of `ScholarlyArticle` entries with authors, venue, and URL. This is
  a substantive SEO/structured-data feature most personal academic sites skip entirely,
  and it's more complete than what al-folio ships out of the box (al-folio's default
  structured data, if enabled via `_config.yml`'s `serve_static_files`/schema settings,
  typically only covers the `Person`, not a full publication array). **Concretely worth
  copying**: adding a JSON-LD block listing publications with `headline`, `author`,
  `datePublished`, `url` for each paper, hand-authored or generated from `papers.bib` at
  build time.
- `<link rel="icon" ... href="assets/favicon_mine.ico">` is set (good — no default-theme
  favicon left in place, a mistake worth checking for on any al-folio fork).
- Both Google Analytics (`gtag.js`) and GoatCounter are loaded simultaneously — redundant
  tracking, no real downside but unnecessary page weight; one analytics tool is enough for
  a personal site with this level of traffic.

---

## 6. Accessibility / technical details

- Images have descriptive `alt` text throughout, e.g.
  `alt="Adaptive Attacks on Trusted Monitors Subvert AI Control Protocols cover"` for
  each publication thumbnail, and `alt="Alexander Panfilov"` for the profile photo — this
  is done correctly and consistently; worth auditing an al-folio site's `_bibliography`
  entries and profile image for the same (al-folio's `bib.html` include does support an
  `alt` attribute on preview images, but it must be set per-entry or falls back to
  something generic).
- `loading="lazy"` is applied to every image, including the hero profile photo and all
  publication thumbnails — a small performance win worth mirroring; check whether an
  al-folio fork's `_includes/figure.html`/image includes set this by default (recent
  al-folio versions do, but only if not overridden).
- Abstract/BibTeX toggle buttons correctly manage `aria-expanded` state via JS
  (`button.setAttribute('aria-expanded', expanded)`), which is good practice for screen
  readers, though the toggle *targets* (`<div class="toggle-panel">`) aren't wrapped in
  `role="region"` or given `aria-live` — a minor gap but not a major accessibility issue.
- All external links use `target="_blank" rel="noopener"` consistently — correct and
  worth confirming as a lint check on any theme (`rel="noopener"` without `noreferrer` is
  fine; `noopener` alone covers the tab-nabbing security concern).
- The page has only one `<h1>` (the name in the hero) and uses `<h2>`/`<h3>`/`<h4>`
  correctly for section and card headings — clean heading hierarchy, easy to audit and
  worth spot-checking on any custom-themed al-folio page since it's easy to drift
  (e.g. an `about.md` accidentally emitting two `<h1>`s if front matter and body both
  declare a title).

---

## 7. Concrete punch list — what to check on an al-folio site because of this comparison

1. **Enable/verify Open Graph + Twitter Card meta tags** (`og:image`, `og:description`) —
   this site has none; don't repeat that gap on a theme that supports it.
2. **Keep dark mode** — this site dropped it entirely by hardcoding `color-scheme: light`;
   al-folio's toggle is a genuine advantage, don't remove it in a redesign.
3. **Enable abstract/BibTeX toggles inline on the publications list** (jekyll-scholar
   `details_dir`/toggle config) if not already on — directly inspired by this site's
   expand-in-place UX, avoids sending readers off-page for a citation.
4. **Bold/highlight the site owner's name in multi-author bylines** on the publications
   page — check current `_bibliography/papers.bib` rendering does this.
5. **Add per-paper cover images** to `_bibliography/papers.bib` entries (`image` field)
   where a distinctive figure exists — increases scan-ability the way this site's
   thumbnails do.
6. **Keep the CV as an HTML page, not just a PDF download** — this site regressed to
   PDF-only; if the maintained site already has `cv.md`, treat that as a feature to
   preserve, not simplify away.
7. **Consider a compact "now" panel** (current focus / location / upcoming
   travel/conferences) near the top of `about.md`, distinct from the static bio —
   directly modeled on this site's "My current..." card row.
8. **Add a JSON-LD `Person` + `ScholarlyArticle` structured-data block** to the head if
   not already present, listing each publication's `headline`/`author`/`url`/`datePublished`
   — stronger SEO signal than this repo may currently emit.
9. **Verify favicon is customized**, not left as the theme default — this site's is,
   confirm the maintained site's is too.
10. **Check for redundant/duplicated analytics scripts** — not an al-folio-specific issue,
    but worth a one-time audit of any tracking snippets accumulated over time.
