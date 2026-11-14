# Site cleanup and upstream beautiful-jekyll sync (combined plan)

**Status:** ACTIVE (approved 2026-11-14)
**Date:** 2026-11-14

---

## 1. Objective

Clean up the fork of `daattali/beautiful-jekyll`, fix the broken links, and merge the 109 upstream commits. All work happens on a branch. `main` and the live site do not change until you approve the final merge.

**Your decisions, all applied here**
- Upstream: full `git merge upstream/master` on branch `sync-upstream`.
- Broken PDF links: move the two PDFs to a published `files/` folder.
- Verification: push only the branch and let `ci.yml` build it.
- Deletions: **only the 8 files ChatGPT's plan listed.** Everything else stays.

**Kept (no deletion):** `docs/ml-slides.pdf`, `img/profile-19Dec01-cropped.jpg`, `img/Kim_2023_의정연구.pdf`, `.github/FUNDING.yml`, both `.github` templates, all Staticman files, `sysilviakim.github.io.Rproj`, the `prose:` block's neighbours (comment and analytics includes), `.github/maintenance-plan.md` (left untracked and uncommitted).

**Checked today**
- GitHub `main` is 2 commits ahead of local (`0e5ae51`, `f18fdae`, both `student.md`).
- `/blog/page2/` is live and `/blog/` is a 404, so `index.html` is the blog pagination template.
- The latest CI log shows the duplicate-homepage warning (`index.html` and `index.md`).
- `external-events/`, `staticman.yml` and the `.Rproj` file are public on the live site.
- `/cv/` works, so the `research.md` link needs no fix.

---

## 2. Files affected

**Deleted (8)**
- `docs/index.html`
- `img/404-southpark.jpg` (duplicate of the `assets/img` copy)
- `assets/img/`: `avatar-icon.png`, `bgimage.png`, `hello_world.jpeg`, `install-steps.gif`, `path.jpg`, `thumb.png`

**Deleted because the merge adds them (upstream demo files):** `_posts/2020-02-28-sample-markdown.md`, `assets/img/crepe.jpg`, `Appraisals`, and any other demo file the merge brings in (`aboutme.md`, `screenshot.png`, `CHANGELOG.md`, the flake-it post stay deleted or get removed).

**Moved**
- `index.html` → `blog/index.html` (title `Blog`, stock subtitle removed, `layout: home` kept)
- `docs/ps-jobmarket-tex.pdf` → `files/ps-jobmarket-tex.pdf`
- `docs/rladies_dallas_reproducibility_20210125.pdf` → `files/rladies_dallas_reproducibility_20210125.pdf`

**Edited**
- `_config.yml`
  - `google-scholar:` → `lbvTrNIAAAAJ` (upstream now adds the URL prefix itself)
  - remove the `prose:` block, the old `## google_analytics` comment, `edit_page_button: true`, and the three commented `bgimage.png` example lines
  - add to `exclude:`: `reports/`, `external-events/`, `sysilviakim.github.io.Rproj`, `beautiful-jekyll-theme.gemspec`, `staticman.yml`
- `index.md`: remove `use-site-title: true`; CV link → the same Dropbox URL as `cv.md`
- the two 2021 posts: `/figs/` → `/files/`
- `student.md`: `blob/master` → `blob/main` (2 links)
- `README.md`: site URL → `sysilviakim.com`
- `.github/workflows/ci.yml`: add an `upload-artifact` step for `_site`
- `beautiful-jekyll-theme.gemspec`: keep your dependency versions; bump the version string to `6.0.1`

**Merge conflicts to hand-resolve (2 real ones)**
- `assets/css/beautifuljekyll.css`: take upstream, re-apply your font sizes, the `.img` class and the 95% root size.
- `_includes/social-networks-links.html`: take upstream's loop version, re-add `buymeacoffee`.
- The other 6 are "keep yours" or "keep deleted".

**New:** `files/`, `blog/index.html`, `reports/plans/2026-11-14_site-cleanup-and-upstream-sync.md`.

---

## 3. Ordered steps

About 45 minutes of work, plus about 2 minutes per CI run.

1. Fast-forward local `main` to `origin/main` (2 commits), then create branch `sync-upstream`.
2. Save this plan to `reports/plans/` as ACTIVE and update the copy in `Documents\`.
3. Run `git merge upstream/master`. Resolve the 8 conflicts, delete the demo files, confirm no conflict markers remain, commit.
4. Edit `_config.yml` (Scholar value, dead keys, `exclude:` list). Commit.
5. Delete the 8 files. Commit.
6. Move `index.html` to `blog/index.html` and edit its front matter. Commit.
7. Move the two PDFs to `files/` and fix the links in the posts, `student.md`, `index.md` and `README.md`. Commit.
8. Add the artifact upload to `ci.yml`. Commit.
9. Push `sync-upstream` only. `pages.yml` deploys from `main` alone, so the live site is untouched.
10. Verify (section 4). Fix and re-verify, at most 3 rounds.
11. **Stop.** Report results and ask before merging into `main`. That merge deploys the site.

After your approval of step 11: merge, push `main`, confirm the Pages deploy run happened (not only a green CI check), spot-check the live site, mark the plan DONE.

---

## 4. Verification

**Before the push (local)**
- No conflict markers; `_config.yml` parses as YAML.
- No remaining references to the 8 deleted files, `/figs/`, or `blob/master`.
- `git diff --stat origin/main..sync-upstream` matches section 2, and every "kept" file is still present.
- The two `student.md` commits from GitHub are still present.

**CI build on the branch**
- `bundle exec jekyll build --future` passes.
- The log has no "Conflict: destination is shared" warning.

**Built site (downloaded `_site` artifact, served locally, checked in the browser pane)**
1. Home shows the About page; `/blog/` and `/blog/page2/` list posts with working pager links.
2. Footer icons and URLs are correct, including the Bluesky icon and the Scholar URL.
3. Search opens and finds a post; `assets/data/searchcorpus.json` is valid JSON.
4. Events page: calendar renders, footer sits below it; `events.json` is valid.
5. Mobile width (375px): the menu collapses after a tap, tables scroll, text sizes match the live site.
6. `/files/` PDFs load; `staticman.yml`, the `.Rproj` file and `reports/` are absent from `_site`.

**Limits I will report**
- `external-events/` exists only in the `pages.yml` build, so its exclusion is confirmed only after deploy.
- The branch build uses fallback event data; the full event list is checked after deploy.

---

## 5. Results so far (2026-11-14)

Steps 1 to 10 are done on branch `sync-upstream` (pushed). Step 11, the merge into `main`, is waiting for approval, so the status stays ACTIVE.

**Verification results**
- CI on `sync-upstream`: both runs passed (`be2ecdd`, then `e278c23`). The build log has no "Conflict: destination is shared" warning.
- Pre-push checks passed: no conflict markers, no stale references, every "kept" file present, both `student.md` commits from GitHub present, `_config.yml` parses.
- Built site (CI artifact, served locally): homepage, Syllabi and a post match the live site at 1280px. `/blog/` lists 5 posts and `/blog/page2/` lists 3, with working pager links. Search finds a post, and `searchcorpus.json` and `events.json` are valid JSON. Both `/files/` PDFs load. `staticman.yml`, the `.Rproj` file, the gemspec and `reports/` are absent from the build.
- Footer: X, Bluesky and Buy Me a Coffee icons render; the Scholar URL is `citations?user=lbvTrNIAAAAJ`.
- Mobile (375px): the menu opens, the Teaching dropdown stays open when tapped, and the menu collapses after tapping a destination. No sideways page overflow.

**Fix round 1 of 3**
- The merged theme CSS sets `table { display: block }`, which collapsed the events calendar grid to 4px high. Fixed in `events.md` with a page-local rule for `#events-calendar table`. Confirmed in the second build at desktop and mobile widths.

**Deviations from the plan**
- `events.md` was edited (not in the original file list), for the fix above.
- Three of the 8 deletions (`docs/index.html`, `hello_world.jpeg`, `install-steps.gif`) came from the merge itself, since upstream had removed them.
- The machine's deletion guard blocked a forced `git rm`, so the five upstream demo files were unstaged and sent to the Recycle Bin instead.
- Upstream's `appraisal` development dependency was dropped from the gemspec along with `Appraisals`.

**Not verified**
- Wide-table scrolling: no page on the site has an HTML table other than the calendar.
- `external-events/` exclusion and the full event list: both exist only in the `pages.yml` deploy build.
- Links built with `absolute_url` point at sysilviakim.com in the preview.
- The live site: nothing is deployed until `main` is updated.
