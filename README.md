# site-agent

Agents and skills for designing and building websites that do not look generated.

Most sites built by an assistant share a tell: centred hero, three
feature cards, gradient, a font nobody chose. They are not bad so much as
anonymous, and anonymity is the one thing a personal or professional site cannot
afford.

This repository holds the agents and skills for building sites that read as
deliberate. What is built today is the pass that finds the tells and replaces
each one with a choice somebody actually made. The order the rest of it rests on
— structure decided before layout, type chosen before colour, content written
before it is arranged — and the technical checks that decide whether the result
is findable, shareable and fast are queued in [BACKLOG.md](BACKLOG.md) and do not
exist yet.

The first thing to be built with it will be Kerem's own site, which is also the
honest test of whether the pack works. It is the first item in the queue.

## What this is not

It is not a template collection and does not ship a starter. A
template is the problem it is trying to solve.

It is not a design system. It teaches the decisions; it does not make them for
you.

It does not host anything or manage a deployment.

## How to use this

These are skills for Claude, not a command-line tool. There is nothing to
install and nothing to import — you describe the work and the matching skill
fires on its own.

**In Claude Code or Cowork**, once the skills are on your machine:

```bash
bash ~/Desktop/agent/_setup/sync-skills.sh
```

That clones every agent repository and links its `skills/` into `~/.claude/skills`,
so they are available in every session and every folder. Re-run it whenever one of
these repositories ships something new — it pulls rather than re-clones.

Then simply ask. Each skill's `description` frontmatter is written to match how
the request actually gets phrased, in English or Turkish, so you do not name the
skill and generally should not have to think about which one applies.

**If nothing fires**, that is a defect in the skill rather than in how you
asked. The description was written for the wrong phrasing. Say what you asked
and what you expected, and it gets fixed — that feedback is more valuable than
working around it.

**What is actually built** is listed under Contents below and in the Done
section of [BACKLOG.md](BACKLOG.md). Everything under Queue is planned and does
not exist yet.

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

`agents/` and `examples/` are empty so far.

## Roadmap

See [BACKLOG.md](BACKLOG.md). The first unchecked item is the one being built.

## Contents

| Skill | What it does |
| --- | --- |
| [de-ai-slop-ui](skills/de-ai-slop-ui) | Find and remove the thirty visual and copy tells that mark a page as machine-made. |
| [scroll-motion-stack](skills/scroll-motion-stack) | The stack behind scroll-driven sites: GSAP ScrollTrigger with Lenis, the pre-rendered image sequence that fakes an Apple-style scroll-zoom, preloaders, and the mobile performance failures that make clones feel cheap. |

These arrived already written and in daily use, rather than being built against the queue below — which is why most carry no item number. Some have Turkish bodies: they were written in the language they are used in, and translating them is a queue item rather than a blocker.

Everything still under Queue in [BACKLOG.md](BACKLOG.md) does not exist
yet.
## Licence

MIT. See [LICENSE](LICENSE).
