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
- [ ] Add profile photo (`assets/img/prof_pic.jpg`) — to be uploaded by user
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

- [ ] Replace all Albert Einstein placeholder data with your own:
  - [ ] Name, label, email, location
  - [ ] Education entries
  - [ ] Experience/work entries
  - [ ] Awards (if any)
  - [ ] Skills
  - [ ] Languages
  - [ ] Remove or update Volunteer, Certificates, References sections as needed
- [ ] Upload CV PDF to `assets/pdf/` and update path in `_data/socials.yml`

## 6. Publications (`_bibliography/papers.bib`)

- [ ] Replace Einstein placeholder entries with your own BibTeX publications
- [ ] Mark selected/featured papers with `selected={true}`
- [ ] Add thumbnails/previews for papers (optional, `assets/img/publication_preview/`)
- [ ] Update `scholar` config in `_config.yml` with your name (see Section 1)

## 7. Repositories Page (`_data/repositories.yml`)

- [ ] Add your GitHub repositories to display
- [ ] Add your GitHub username to the config

## 8. News / Announcements (`_news/`)

- [ ] Remove placeholder news entries
- [ ] Add your own announcements (paper acceptances, talks, etc.)

## 9. Miscellaneous Page (Optional — Add Later)

- [ ] Decide on content for a miscellaneous page
- [ ] Create `_pages/misc.md` and add to navigation
