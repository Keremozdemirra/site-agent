---
name: de-ai-slop-ui
description: Finds and removes the 30 visual and copy tells that make a site instantly recognizable as AI-generated - purple-on-black palettes, harsh gradients, glassmorphism, blurred glow blobs, dot-grid backgrounds, sparkle and default Lucide icons, Inter/Geist/Grotesk, pure-white backgrounds, shadows and hovers on everything, huge border radius, three-card feature grids, bento layouts, three-tier pricing tables, checkmark bullets, "not just X, it's Y" copy, em dashes, emoji as icons, invented testimonials, fake terminal mockups, no real product screenshot, neon and cliche pastels, layout shift, bouncing arrows, missing terms and privacy pages. Replaces each with a deliberate alternative rather than just deleting it. Use whenever the user says their site looks AI-made, generic, templated or soulless; wants a design to look human, custom, original or less like v0/Lovable built it; pastes this kind of tell-list; and proactively before shipping any AI-generated landing page or app UI.
---

# De-slop a UI

Every one of the 30 tells below is a *default* — what a model reaches for when
no one specified anything. None is ugly in isolation. What marks a site as
machine-made is that all thirty arrived together, unchosen, and the result looks
like a hundred other sites shipped that week. Visitors read that as "nobody was
home", and it costs trust exactly where trust is being asked for.

So the goal is not a purge. Removing every gradient and every rounded corner
produces a different kind of generic. The goal is that **every remaining choice
was made on purpose, for this product**. A purple gradient a designer chose
because the brand is purple is fine. A purple gradient nobody chose is the tell.
Keep that distinction in front of you the whole way through — it's the
difference between de-slopping and vandalizing.

## Workflow

### 1. Learn what this product actually is

You can't replace generic choices with specific ones without knowing the
specifics. Before changing any code, establish:

- **What it does, in the user's words.** Not "streamline your workflow" — the
  literal thing. This drives nearly all the copy fixes.
- **Who visits.** A tool for radiologists and a tool for skaters cannot look the
  same. Audience determines palette, typography, and density more than taste does.
- **Whether any brand exists.** A logo, a color, an existing app, a competitor
  they like or hate. Anything real beats anything invented.
- **Whether there's a real product to show.** This decides items 18 and 14. If a
  screenshot exists, it replaces the fake mockups. If nothing is built yet, the
  page has to be honest about that instead of faking a UI.

If the user is present, ask. Two questions here save an entire wrong redesign.
If they're away, infer from the repo — README, existing copy, actual features —
and state what you assumed at the top of your report.

### 2. Audit against the 30 tells

Read `references/tells.md` — it has all thirty with what to grep for, why each
reads as machine-made, and a concrete replacement. Then look at the actual code:
the global CSS / Tailwind config, the page components, the copy, and whether
`/terms` and `/privacy` exist at all.

Report as a table, worst offenders first, where "worst" means most immediately
recognizable rather than most numerous:

```markdown
## AI-tells found — <page/site>

| # | Tell | Where | Replace with |
|---|------|-------|-------------|
| 1 | Purple→black gradient hero + glow blob | `app/page.tsx:20-38` | Flat warm off-white, one accent from the logo |
| 2 | Three feature cards, identical, Lucide icons | `components/Features.tsx` | Two asymmetric rows, product screenshots |

**Fine as-is:** rounded-lg on buttons (consistent, restrained), Inter for body
(legible, and the headline font now carries the character).
```

The "fine as-is" line matters. It shows you're making judgments rather than
running a find-and-replace, and it stops the user from thinking they have to
tear up everything.

### 3. Fix in this order

Order matters, because the early moves change how the later ones look:

1. **Palette** — one background, one text color, one accent, chosen for this
   product. Almost everything else keys off this.
2. **Typography** — one distinctive display face, one workhorse body face.
3. **Structure** — break the symmetric card-grid rhythm.
4. **Content** — real screenshots, real copy, real or absent testimonials.
5. **Effects** — remove shadows, blurs, glows, and hovers that aren't earning
   their place. This goes last because after 1–4, most of them are already gone.
6. **The missing pages** — terms, privacy, and anything else a real site has.

Get the user's sign-off before a large rewrite. On a design change, showing is
better than describing: build the revised page, screenshot it, and let them look.
If Playwright is available (Chromium is already installed here), render before
and after at 1280×800 and at 390×844 so mobile is checked too — most of these
sites break at mobile widths, which is its own tell.

### 4. Verify

Look at the result and ask the honest question: *could this be any other
product's site?* If swapping the logo and name would work seamlessly, it's still
generic and the palette/type/content work isn't done.

Then check the mechanics, since these regress easily: does it still build, does
it hold up at 390px wide, does text still pass contrast (4.5:1 for body), does
it work with dark mode if the site has one, and did removing a hover state
remove the only affordance on something clickable — including for keyboard users,
who need a visible `:focus-visible` ring regardless.

## Reference

`references/tells.md` — all 30 tells: detection, why it reads as AI, and the
replacement. Read it in step 2.

If the project has a broader design skill available (`frontend-design`,
`canvas-design`, `dataviz` for charts), use it alongside this one: this skill is
subtractive — it removes what marks the page as machine-made — while those are
generative. Both directions are usually needed.
