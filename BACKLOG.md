# Backlog

Working queue. The next unchecked item is the one being built. An item stays
unchecked and picks up a `status:` note if it spans more than one working
session — finishing something half-built takes priority over starting the next
one.

Rules of thumb applied to every item:

- one job per skill, done properly, rather than a bundle of half-features
- a skill earns its place only if it beats writing the instruction out by hand;
  if a good prompt does the same job, the skill is overhead
- the `description` frontmatter is the whole trigger mechanism — write it so the
  skill fires on how the work is actually asked for, including in Turkish
- every skill carries a worked example on real input, not a toy
- no claim about a framework, standard, regulation or method without a citation
  and a vintage
- an agent gets its own file only when it needs a different judgement, not a
  different topic

---

## Done

- [x] **de-ai-slop-ui** · shipped 2026-08-20. Written before this repository existed and published here as-is; no queue item.

## Queue

- [ ] **001 — build-keremozdemir-site** · Build Kerem's own site with this repository's skills — the honest test of the pack. Single page, no framework unless one earns its place: who he is, what he works on, and a repositories section generated from the GitHub API rather than hand-maintained, since a hand-maintained list is a list that goes stale. Ships as its own repository; this one holds the method.
- [ ] **002 — structure-before-style** · Decide what a page is for and what it must say before anything is designed. The section that most often gets skipped and the one that decides whether the rest is worth doing.
- [ ] **003 — type-and-scale** · Choose a typeface and a modular scale on stated grounds. Includes the reasons the defaults look generated and what to do instead.
- [ ] **004 — content-first-copy** · Write the words before the layout, because a hero section written to fill a shape says nothing.
- [ ] **005 — portfolio-section** · Generate a repositories or work section from a real source — the GitHub API, a data file — with a stated refresh path, so it cannot silently go stale.
- [ ] **006 — responsive-without-breakpoint-soup** · Layout that adapts on content rather than on a list of device widths.
- [ ] **007 — ship-checklist** · The technical pass before publishing: title and meta description, og:image, canonical, sitemap, robots, 404, html lang, alt text, no console errors, no leftover framework defaults. What separates a site that gets found from one that does not.
- [ ] **008 — accessibility-pass** · Contrast, focus order, keyboard traps, motion preferences. Checked against the live page rather than asserted.
- [ ] **009 — performance-budget** · State a budget in kilobytes and milliseconds before building, then hold to it.
