# Website To-Do List

## 1. Site Configuration (`_config.yml`)

- [x] Update `scholar` last/first name from `Einstein`/`Albert` to `Weckbecker`/`Moritz`
- [x] Set light mode as default (dark mode toggle remains enabled)
- [x] Disable comments (remove Giscus/Disqus config)
- [x] Disable analytics (already off — verify no keys are set)
- [x] Remove external blog sources (Medium, Google Blog entries under `external_sources`)
- [x] Update `blog_name` and `blog_description` or remove blog-related config
- [x] Update `display_tags` and `display_categories` to remove blog-specific tags

## 2. Navigation — Remove Unused Pages

- [x] Remove or hide the **Blog** page (`_pages/blog.md`)
- [x] Remove or hide the **Teaching** page (`_pages/teaching.md`)
- [x] Remove or hide the **Books** page (`_pages/books.md`)
- [x] Remove or hide the **Projects** page (`_pages/projects.md`)
- [x] Remove or hide the **Dropdown** page (`_pages/dropdown.md`)
- [x] Remove or hide the **Profiles** page (`_pages/profiles.md`)
- [x] Keep: About, Publications, CV, Repositories
- [ ] (Optional) Add a **Miscellaneous** page later

## 3. About Page (`_pages/about.md`)

- [x] Update subtitle to: `PhD Student in AI Interpretability, focusing on Data Attribution and AI Safety @ Fraunhofer HHI`
- [x] Add link to Fraunhofer HHI in the subtitle
- [x] Update office/address info below profile picture
- [x] Write biography text
- [x] Add profile photo (`assets/img/profile.jpeg`)
- [x] Disable `latest_posts` section (no blog)
- [x] Keep `announcements` (news) section enabled
- [x] Keep `selected_papers` section enabled

## 4. Social Links (`_data/socials.yml`)

- [x] Set email to `moritz.weckbecker@hhi.fraunhofer.de`
- [x] Set Google Scholar ID to `BNo6RuwAAAAJ`
- [x] Add GitHub username (`MoritzWeckbecker`)
- [x] Add LinkedIn username (`moritz-weckbecker-b5359a193`)
- [x] Add Twitter/X username (`MWeckbecker`)
- [x] Remove `inspirehep_id` (not needed)
- [x] Remove `custom_social` placeholder
- [x] Remove RSS icon (no blog)

## 5. CV (`_data/cv.yml`)

- [x] Replace all Albert Einstein placeholder data with your own:
  - [x] Name, label, email, location
  - [x] Education entries
  - [x] Experience/work entries
  - [x] Awards (if any)
  - [x] Skills
  - [x] Languages
  - [x] Remove or update Volunteer, Certificates, References sections as needed
- [x] Upload CV PDF to `assets/pdf/` and update path in `_data/socials.yml`

## 6. Publications (`_bibliography/papers.bib`)

- [x] Replace Einstein placeholder entries with your own BibTeX publications
- [x] Mark selected/featured papers with `selected={true}`
- [ ] Add thumbnails/previews for papers (optional, `assets/img/publication_preview/`)
- [x] Update `scholar` config in `_config.yml` with your name (see Section 1)

## 7. Repositories Page (`_data/repositories.yml`)

- [ ] Add your GitHub repositories to display
- [ ] Add your GitHub username to the config

## 8. News / Announcements (`_news/`)

- [ ] Remove placeholder news entries
- [ ] Add your own announcements (paper acceptances, talks, etc.)

## 9. Miscellaneous Page (Optional — Add Later)

- [ ] Decide on content for a miscellaneous page
- [ ] Create `_pages/misc.md` and add to navigation

## 10. Cleanup — Broken / Old Artifacts (found during site audit)

Site-wide placeholder text (visible on live pages right now):

- [ ] `_config.yml` `description:` is still the theme default ("A simple, whitespace theme for academics. Based on [\*folio]...") — used in SEO meta tags and RSS
- [ ] `_config.yml` `footer_text:` is still the literal placeholder `A footer.`, shown in the site footer on every page
- [ ] `_config.yml` `icon: ⚛️` — physics-atom emoji favicon left over from the Einstein template; replace with something fitting or a custom image

Broken image references (files were removed from `assets/img/` locally but are still referenced — pages currently 404 their images):

- [ ] `_pages/profiles.md` + `_pages/about_einstein.md` — fully placeholder Einstein content referencing deleted `prof_pic.jpg`; page is hidden from nav but still publicly reachable at `/people/`. Recommend deleting both files since the page isn't used.
- [ ] `_books/the_godfather.md` — demo book review referencing deleted `the_godfather.jpg`; Books page is hidden. Recommend deleting since not used.
- [ ] `_projects/1_project.md`–`9_project.md` — demo projects referencing deleted `1.jpg`–`12.jpg`; Projects page is hidden. Recommend deleting since not used.
- [ ] `_posts/` (31 theme demo/feature-showcase posts) — reference deleted demo images (`prof_pic.jpg`, `prof_pic_color.png`, `rhino.png`, etc.); Blog is hidden from nav but individual posts are still publicly reachable. Recommend deleting the whole `_posts/` directory since the blog is disabled.
- [ ] `_teachings/` (2 demo course entries: "Prof. Data", "Prof. Example") — Teaching page is hidden. Recommend deleting since not used.

Stale/auto-generated data:

- [ ] `_data/citations.yml` — still keyed to the old Einstein Google Scholar ID (`qc6CJjYAAAAJ`) instead of the real one (`BNo6RuwAAAAJ`); should self-correct on the next scheduled `update-citations.yml` run (Mon/Wed/Fri), or trigger it manually via `workflow_dispatch` sooner
- [ ] `assets/json/resume.json` — alternate JSONResume-format CV, still 100% Albert Einstein placeholder data; currently unused (`cv_format: rendercv` is active in `_pages/cv.md`) but should be updated or removed to avoid confusion
- [ ] `_pages/repositories.md` — page `description:` is still the theme's setup instructions ("Edit the `_data/repositories.yml`...") rather than real copy; do after Section 7

Uncommitted local cleanup already sitting in the working tree:

- [ ] Unstaged deletions of demo images (`assets/img/1.jpg`–`12.jpg`, `prof_pic.jpg`, `prof_pic_color.png`, `rhino.png`, `template_error.png`, `book_covers/the_godfather.jpg`, `publication_preview/*.gif`) — decide whether to commit these (recommended once the pages referencing them above are removed too, to avoid new broken links)
- [ ] `assets/img/2025-05-DidaConference-3.jpg` — uploaded but not referenced anywhere on the site yet; decide where to use it or remove it
