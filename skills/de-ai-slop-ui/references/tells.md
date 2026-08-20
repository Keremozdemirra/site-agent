# The 30 tells

Grouped by what fixing them requires, not by the original list order — palette
and type changes cascade into everything else, so they come first. Original
numbering is noted so nothing gets lost.

Every entry is: **the tell → why it reads as machine-made → what to do instead.**
The replacement is the important half. Deleting a gradient and leaving a void is
not a fix.

---

## Color (tells 1, 3, 4, 20, 29, 30)

### 1. Harsh gradients

Multi-stop gradients across a hero or a button, usually at a diagonal, usually
between two saturated hues with nothing in common. The eye catches the hard
transition band where the stops meet.

**Instead:** default to a flat surface. If you want depth, use a gradient with a
tiny hue range — a single color moving through lightness (`#1d4ed8` →
`#1e40af`), which reads as light falling on a surface rather than as decoration.
Keep it to one place on the page. If two gradients survive the pass, one of them
is decoration.

### 20. Purple-on-black palette

`#0a0a0a` background, `#8b5cf6` accent, white text. This is the single fastest
tell — it's the default "looks like AI/dev-tool/SaaS" palette, and it's on
thousands of sites.

**Instead:** pull the accent from something real — the logo, the product, the
industry. If there's genuinely nothing, pick a hue that isn't in the 250–280°
violet band and isn't the safe SaaS blue either: a deep green, a rust, an ochre,
an ink navy. One accent, used sparingly, beats a palette.

### 3. Pure white background

`#ffffff` next to `#000000` text is maximum contrast and slightly harsh on a
bright screen; more importantly it's what you get when nobody picked a
background.

**Instead:** move a couple of degrees off white — `#fafaf9`, `#f8f7f4`, a warm
paper tone. Text at `#18181b` rather than pure black. The page immediately looks
considered, at the cost of two hex values. Same logic in dark mode: `#0f1115`
over `#000000`.

### 4. Rainbow gradient text

`bg-gradient-to-r from-purple-500 via-pink-500 to-orange-500 bg-clip-text
text-transparent` on the headline. It also hurts legibility and often fails
contrast checks partway through the gradient.

**Instead:** solid color for the headline. If a word needs emphasis, give that
word the accent color, or set it in the display face at a heavier weight. The
headline should be readable at a glance, which a gradient works against.

### 29. Neon colors

Electric cyan, hot magenta, `#39ff14` green — especially glowing on dark. Reads
as "cyberpunk template" and nearly always fails contrast.

**Instead:** if the brand really is loud, keep one saturated accent and mute
everything around it so it can be loud. Neon works as a single note, never as a
palette.

### 30. Cliché pastel tones

The soft lavender / mint / peach / baby-blue set, usually four pastels at equal
weight so nothing leads. Common on "friendly" and wellness-adjacent pages.

**Instead:** pastels are fine if they're *yours* and unequal — one dominant
tint carrying the page, the rest as small accents, with a genuinely dark text
color so there's structure. Equal-weight pastels are what a model outputs when
asked for "soft and friendly".

---

## Typography (tells 10, 9)

### 10. Inter / Geist / Space Grotesk

Not bad fonts — Inter especially is excellent. But this trio is the default in
every starter template, so the page inherits the same voice as everything else
shipped from the same tools.

**Instead:** keep a workhorse for body text (Inter is genuinely fine here) and
give the display face real character. Free options with actual personality:
Instrument Serif, Fraunces, Bricolage Grotesque, Newsreader, Gambetta, Redaction,
General Sans, Söhne alternatives like Switzer. A serif headline over a sans body
alone moves a page out of template territory. Two families is the budget; three
is usually a mistake.

### 9. Em dashes

The `—` is a fine mark, and Claude reaches for it constantly. In marketing copy,
several per paragraph is a strong tell — the rhythm is unmistakable.

**Instead:** vary the punctuation. Most em dashes become a period (two short
sentences read stronger anyway), a colon when introducing something, or a comma.
Keep one if it's doing real parenthetical work. Related tell: sentences built as
"It's not just X — it's Y" (see tell 15) usually contain one, so fixing that copy
pattern removes many of these for free.

---

## Layout & structure (tells 6, 13, 19, 17, 16)

### 6. Three cards side by side

`grid-cols-3` with three equal cards, each an icon, a three-word heading, and two
lines of body copy. It's the shape a model produces for "features section", and
the visual rhythm is instantly recognizable.

**Instead:** let content decide the shape. Real products don't have three equally
important features — lead with the one that matters, at larger scale, with a
screenshot, and let the rest be a compact list or a two-up row. Asymmetry reads
as editing; symmetry reads as a template. If you must keep a grid, vary card
sizes or use two, four, or five items so the "3" rhythm breaks.

### 13. Bento box layout

The rounded-rectangle mosaic of mixed-size tiles. Apple made it good; then it
became the default answer to "make the features section interesting", and now
each tile usually holds a fake chart or an icon rather than anything real.

**Instead:** a bento only works when the tiles hold genuinely different *kinds*
of content — a screenshot, a metric, a quote, a short demo video. If your tiles
all hold an icon and a sentence, it's a card grid wearing a costume; use plain
stacked sections instead.

### 19. Excessive border radius

`rounded-3xl` (24px+) on cards, `rounded-full` on everything, radii that don't
relate to each other — a 24px card containing an 8px button containing a fully
round badge.

**Instead:** pick one radius scale and apply it consistently, sized to the
element: something like 6px for inputs and buttons, 12px for cards, and keep
`rounded-full` for avatars and pills only. Nested elements should have a *smaller*
radius than their container, not larger. Sharp corners are also a legitimate,
underused choice — they read as deliberate.

### 17. Three-tier pricing table

Starter / Pro / Enterprise, the middle one scaled up with a "Most popular"
badge, checkmark lists down each column, "Contact us" on the right. Correct
pattern, executed identically everywhere, and often shipped by products with one
price or no price at all.

**Instead:** show your actual pricing. One plan? Show one, large, with what it
includes. Usage-based? Show the calculator. If you do have three tiers, drop the
badge or make the recommendation honest and specific ("most teams under 20
people pick this"). Never ship a three-tier table you invented to fill the
section.

### 16. Checkmark bullet lists

Green ✓ or `<Check>` in front of every line, everywhere — features, benefits,
pricing rows, the footer.

**Instead:** plain text or a modest bullet for a neutral list. Reserve the
checkmark for where it actually signals inclusion versus exclusion — a
comparison table where some rows are ✓ and some are ✗. A checkmark next to every
line carries no information; it's decoration pretending to be structure.

---

## Content honesty (tells 12, 18, 14, 26, 27)

These four matter more than anything visual. A polished page making claims it
can't back is worse than an ugly honest one, and a visitor who catches one
invented detail stops believing the rest.

### 12. Invented testimonials

"Sarah Chen, CTO at TechFlow" with a generated avatar, praising a product that
launched yesterday. Recognizable by suspiciously on-message quotes, generic
company names, and stock or AI-generated faces. Depending on jurisdiction this is
also a straightforward consumer-protection problem, not just a taste one.

**Instead:** cut the section until you have a real quote. An empty space is
honest; a fabricated endorsement is a lie the visitor can often smell. In the
meantime the slot can hold something true: a "built by" note, a changelog, a
GitHub star count, a screenshot of real usage, or nothing.

### 18. No real product screenshot

The page describes software but never shows it. Instead: illustrations, floating
UI fragments, a browser frame with a placeholder inside. Visitors read this
correctly — as "there may be nothing here".

**Instead:** one real screenshot, above the fold, even if the product is rough.
It outperforms every abstract visual because it's the only element that proves
the thing exists. If it genuinely doesn't exist yet, say so — a waitlist page
that admits it's pre-launch is credible; one that fakes a UI isn't.

### 14. Fake terminal window

A dark rounded box with three traffic-light dots, a `$ npm install your-product`
line, and a typing animation. Ubiquitous in dev-tool templates and usually
showing a command that doesn't work.

**Instead:** if the product genuinely is a CLI, show a real session with real
output — the actual value is in what it prints, not in the chrome. If it isn't a
CLI, delete the terminal; it's costume.

### 26. No terms of service

A page selling something, collecting accounts, or taking payment, with no terms
anywhere. The footer link goes to `#` or doesn't exist.

**Instead:** write real terms covering what the service does, acceptable use,
liability limits, and termination. Generators are acceptable as a starting point
if the result is actually read and edited to match the product. If money or
accounts are involved, this is a real legal requirement, not a checklist item.

### 27. No privacy policy

Same, and stricter: if the site touches EU/UK/California visitors — which it
does — collecting an email without a privacy policy is a compliance problem.
Analytics alone triggers it.

**Instead:** state what's collected, why, who else sees it (every third party by
name: analytics, payments, email, hosting), how long it's kept, and how to
request deletion. Then make sure the deletion path actually works — see the
`pre-launch-security-audit` skill, item 21, because a policy promising deletion
that doesn't happen is worse than no policy.

---

## Effects & motion (tells 5, 8, 22, 23, 24, 25, 28, 2, 7, 21)

Individually harmless, collectively the strongest signal on the page — because
the model added every effect it knew rather than choosing between them.

### 5. Shadow on everything

`shadow-lg` on cards, buttons, inputs, navbar, images, modals. Shadow means
elevation; when everything is elevated, nothing is.

**Instead:** one or two levels total. Cards usually need no shadow at all — a
1px border in a slightly darker tone does the separation more cleanly. Save real
shadow for things that genuinely float above the page: dropdowns, popovers,
modals. Prefer tight, low-opacity shadows (`0 1px 2px rgb(0 0 0 / 0.06)`) over
the big soft blurs.

### 8. Glassmorphism

`backdrop-blur-lg bg-white/10 border border-white/20`, on cards, the navbar,
and modals. It reads as 2021 template, hurts text contrast, and is a real
performance cost on mobile because it forces expensive repaints.

**Instead:** solid surfaces. A translucent blurred header over scrolling content
is the one place it still earns its keep — keep it there, at a subtle blur, with
enough background opacity that text stays legible, and drop it everywhere else.

### 22. Blurred glow blob

One or more large blurred colored circles behind the hero
(`blur-3xl opacity-30 rounded-full`), often two in complementary colors.
Meaningless decoration whose only job is to keep the background from being empty.

**Instead:** if the background feels empty, that's usually a spacing or
hierarchy problem, and a blob is covering for it — fix the real problem. If you
want atmosphere, a very subtle noise texture or a faint single-hue wash reads far
less generic. Absolutely never two blobs in different hues.

### 23. Dot grid background

The faint dotted or graph-paper pattern across the hero. Direct descendant of
the same template lineage as the blob, and it fights with text.

**Instead:** leave the background alone. Whitespace is not a bug. If texture is
wanted, keep it to one section rather than the page, at low enough contrast that
you have to look for it.

### 24. Sparkle icon

The ✨ / `<Sparkles>` icon on anything AI-related — buttons, badges, headings.
It's the universal "this is the AI feature" marker, which now signals "generated
by AI" as much as "powered by AI".

**Instead:** name the thing the feature does. "Summarize", "Draft reply",
"Find similar" beats "✨ AI Magic" — it's clearer *and* it doesn't carry the
tell. If an icon is needed, pick one that depicts the actual action.

### 25. Animated bouncing arrows

`animate-bounce` chevron at the bottom of the hero, plus arrows sliding on hover
across every link. Constant motion in the periphery is distracting and hurts
users with vestibular sensitivity.

**Instead:** trust visitors to scroll — they will. If you need to signal more
content, let a section peek above the fold instead of animating an arrow. Keep
motion for transitions that communicate state (a menu opening, an item added),
and honor `prefers-reduced-motion`.

### 28. Hover effect on everything

Every card lifts, scales, glows, and changes border on hover — including cards
that aren't clickable. Hover states are affordances; applying them to static
content teaches visitors the wrong thing.

**Instead:** hover feedback only on interactive elements, and one property, not
four. A background-tone shift or a border-color change is plenty; `scale-105`
plus `-translate-y-2` plus shadow plus border is a slot machine. Whatever you
keep, ensure `:focus-visible` gets a clear ring too — keyboard users get no hover
at all, and removing hover styling without adding focus styling makes the page
less accessible, not more.

### 2. Default Lucide icons

Not Lucide's fault — it's the default in every AI-built UI, so the same rocket,
zap, shield, and sparkle appear at the same 24px stroke weight on every one of
these sites.

**Instead:** ask whether the icon adds information. Most feature-card icons
don't and can be deleted, which improves the layout. Where you need icons, use a
set with a distinct voice (Phosphor's duotone, Iconoir, Remix, Untitled, Nucleo)
or commission/draw the five that matter. And never use rocket 🚀 for "launch",
zap ⚡ for "fast", or shield 🛡 for "secure" — those three mappings are the tell
inside the tell.

### 7. Emoji as icons

🚀 ⚡ 🎯 ✨ 🔥 as bullet markers and section icons. Renders differently on every
platform, is meaningless to screen readers, and reads as a chat message pasted
into a webpage — which is often literally what happened.

**Instead:** a real icon set, or no icon. Emoji can work in body copy where the
voice is genuinely casual, but not as UI furniture.

### 21. Layout shift / empty loading state

Content jumps as it loads: images without dimensions, fonts swapping and
reflowing, a blank white flash before a client-side render, skeleton loaders that
don't match the shape of what arrives.

**Instead:** set explicit `width`/`height` (or `aspect-ratio`) on every image so
space is reserved. Use `font-display: swap` with a metric-compatible fallback so
the swap doesn't reflow. Render something real on the server rather than a spinner
where possible. If you use skeletons, match the real content's dimensions — a
skeleton of the wrong size is a shift with extra steps. Check Cumulative Layout
Shift and aim under 0.1; see the `vibecode-tech-audit` skill for measuring it.

---

## Copy (tell 15)

### 15. "Not X, but Y"

"It's not just a task manager — it's a second brain." "Not another dashboard.
A command center." The construction shows up once per section, and it's one of
the most recognizable LLM copy rhythms there is. Its cousins: "Imagine a world
where…", "In today's fast-paced landscape…", triads of three-word phrases
("Fast. Simple. Powerful."), and "seamlessly" / "effortlessly" / "unlock" /
"supercharge" / "revolutionize".

**Instead:** say the specific true thing. "Not just a task manager — a second
brain" carries no information; "Keeps every task you've ever written, searchable
in 20ms" does. Concrete nouns, real numbers, actual verbs. A good test: could a
competitor put this exact sentence on their site? If yes, it says nothing.

---

## After the pass

Two checks worth doing, because they catch what item-by-item fixing misses:

**The swap test.** Replace the logo and product name with a competitor's. Does
the page still work perfectly? Then it's still generic — the specificity work
isn't done, regardless of how many tells you removed.

**The regression check.** De-slopping breaks things in predictable ways: removed
hover states leave no affordance (add `:focus-visible`), new palettes fail
contrast (4.5:1 body, 3:1 large text), a new display font may not have the
weights or the character set the copy needs, and desktop-first fixes often break
at 390px. Look at the result on a phone width before calling it done.
