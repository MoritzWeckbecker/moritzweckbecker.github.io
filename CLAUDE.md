@AGENTS.md

## Session Continuity Notes

This is Moritz Weckbecker's personal site (al-folio fork), being migrated away from the
Einstein demo content. **`to-do.md` at the repo root is the single source of truth for
remaining work** — read it first. Sections 1–7 are done; Section 8 (news), Section 9
(optional misc page), and Section 10 (broken/old artifacts audit) are still open.

### Deployment

- Personal GitHub Pages site: pushes to `main` are built by `.github/workflows/deploy.yml`
  and pushed to the `gh-pages` branch. GitHub Pages **Source** must be set to "Deploy from
  a branch" → `gh-pages` (not the default GitHub Actions Jekyll auto-build, which fails on
  this theme's Liquid tags).
- `.nojekyll` must exist at the repo root (already added) or GitHub reprocesses the
  already-built `gh-pages` output and breaks it.
- `deploy.yml` only triggers on pushes touching certain file patterns (`assets/**`, `*.md`,
  `*.yml`, `*.html`, etc.) — a bare dotfile change like `.nojekyll` alone won't trigger it;
  use `workflow_dispatch` from the Actions tab if needed.

### Working conventions established this session

- One short-lived branch per to-do subsection (e.g. `section-N-topic`), fast-forward merge
  to `main`, push, delete the branch — no long-lived feature branches.
- After any `_config.yml`/`_data/*.yml`/front-matter edit: validate YAML with a quick
  `python3 -c "import yaml; ..."` sanity check, then `npx prettier <files> --check`
  (prettier + `@shopify/prettier-plugin-liquid` are installed as devDependencies).
- Check off completed items in `to-do.md` in the same commit as the change.
- CV content (`_data/cv.yml`, bibliography) is sourced from `assets/pdf/CV_MWeckbecker.pdf`
  — re-read it rather than re-deriving facts if more CV-based content is needed.
- Don't publish home address/phone/birthdate from the CV on public pages; use the
  Fraunhofer HHI office address (Salzufer 15/16, 10587 Berlin, Germany) instead.
- jekyll-scholar's default `sort_by` is `none`, so bibliography/selected-papers display
  order equals `_bibliography/papers.bib` file order — reorder entries in the file itself
  to control featured-publication order, no other config needed.
- The working tree has long-standing _unstaged_ deletions of unused demo images
  (`assets/img/1.jpg`–`12.jpg`, `prof_pic.jpg`, `rhino.png`, etc.) and an untracked
  `assets/img/2025-05-DidaConference-3.jpg` — intentionally left alone pending the Section
  10 cleanup decisions; don't commit or discard them without checking with the user first.
