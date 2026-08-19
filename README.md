# site-agent

Agents and skills for designing and building websites that do not look generated.

Most sites built by an assistant share a tell: centred hero, three
feature cards, gradient, a font nobody chose. They are not bad so much as
anonymous, and anonymity is the one thing a personal or professional site cannot
afford.

This repository holds the agents and skills for building sites that read as
deliberate — structure decided before layout, type chosen before colour, content
written before it is arranged — and the technical checks that decide whether the
result is findable, shareable and fast.

The first thing built with it is Kerem's own site, which is also the honest test
of whether the pack works.

## What this is not

It is not a template collection and does not ship a starter. A
template is the problem it is trying to solve.

It is not a design system. It teaches the decisions; it does not make them for
you.

It does not host anything or manage a deployment.

## Layout

```
agents/
  <name>.md           one specialist, its brief and its boundaries
skills/
  <name>/
    SKILL.md          the instruction, with triggering description frontmatter
    scripts/          only where deterministic code beats instruction
examples/
  <name>/             worked example on real input, with the output committed
```

## Roadmap

See [BACKLOG.md](BACKLOG.md). The first unchecked item is the one being built.

## Planned contents

Nothing here is built yet. This table is the intended shape, and the daily loop
fills it in one item at a time.

| # | Skill | What it does |
| --- | --- | --- |
| 001 | [build-keremozdemir-site](skills/build-keremozdemir-site) | Build Kerem's own site with this repository's skills — the honest test of the pack. |
| 002 | [structure-before-style](skills/structure-before-style) | Decide what a page is for and what it must say before anything is designed. |
| 003 | [type-and-scale](skills/type-and-scale) | Choose a typeface and a modular scale on stated grounds. |
| 004 | [content-first-copy](skills/content-first-copy) | Write the words before the layout, because a hero section written to fill a shape says nothing. |
| 005 | [portfolio-section](skills/portfolio-section) | Generate a repositories or work section from a real source — the GitHub API, a data file — with a stated refresh path, so it cannot silently go stale. |
| 006 | [responsive-without-breakpoint-soup](skills/responsive-without-breakpoint-soup) | Layout that adapts on content rather than on a list of device widths. |
| 007 | [ship-checklist](skills/ship-checklist) | The technical pass before publishing: title and meta description, og:image, canonical, sitemap, robots, 404, html lang, alt text, no console errors, no leftover framework defaults. |
| 008 | [accessibility-pass](skills/accessibility-pass) | Contrast, focus order, keyboard traps, motion preferences. |
| 009 | [performance-budget](skills/performance-budget) | State a budget in kilobytes and milliseconds before building, then hold to it. |

## Licence

MIT. See [LICENSE](LICENSE).
