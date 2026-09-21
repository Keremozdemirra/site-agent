# Component, motion and design sources

Read this before writing a component, a background, a loader or a scroll effect
by hand. Kerem forwarded these on 2026-09-21 so they stop arriving one link at
a time; this file is where a chat looks first. Two rules: check the licence on
the library's own page before shipping anything from it, and pass the result
through de-ai-slop-ui, since most of these ship the defaults that read as
AI-made (glow, glass, gradients, three-card grids).

## Stack for a page that should feel expensive

React Bits builds the UI, GSAP animates it, Lenis smooths the scroll. The
scroll-motion-stack skill carries the implementation and the 60 fps pass.

| Library | For | Where |
|---|---|---|
| Lenis | smooth scrolling, scroll effects, parallax | https://lenis.dev/ and https://github.com/darkroomengineering/lenis |
| GSAP | timelines, scroll animations, text animation, complex interaction | https://gsap.com/docs/ and https://gsap.com/docs/v3/Installation/ |
| React Bits | animated React components, backgrounds, text effects, buttons, cards | https://reactbits.dev/ and https://reactbits.dev/get-started/index |

## Four component libraries to open first

1. Unlumen UI, https://ui.unlumen.com/
2. Magic UI, https://magicui.design/
3. SmoothUI, https://smoothui.dev/
4. RetroUI, https://retroui.dev/

## Featured component libraries

Magic UI, React Bits, Kibo UI, daisyUI, HeroUI, Motion Primitives, Animate UI,
Cult UI, Preline UI, Headless UI.

## More component libraries

8bitcn UI, Base UI (BaseCN), Fancy Components, 21st.dev, Spectrum UI, ReUI,
Jolly UI, FlyonUI, TailArk, TailGrids, Flowbite, HyperUI, Float UI, Meraki UI,
Tremor, Origin UI, Kokonut UI, SmoothUI, Skiper UI, MVP Blocks, Reverse UI,
Easy UI, Eldora UI, Eternity UI, Amicro UI, Beautiful UI, Extra UI, Lightswind
UI, UI Layouts, Ninna UI, Aceternity UI, HextaUI, AlignUI, shadcn/ui, Radix
UI, Mantine, Chakra UI, MUI, Ant Design, Park UI, Ripple UI, Franken UI,
Animata, Hese UI, RetroUI.

Names only, as forwarded; resolve each to its own site before use and record
the licence next to the component you take.

## Design resource sites

From the shared document "Amazing sites for ux/ui designers" (Google Docs,
owner ironcoding.net, shared 2026-09-14, read 2026-09-21):

1. https://shaders.com/ (shader backgrounds)
2. https://www.ls.graphics/ (mockups and design assets)
3. https://pikaicons.com/ (icon set)

## Two portfolio code archives on Drive, read 2026-09-21

Both shared by chiragdeepsingh88@gmail.com on 2026-09-14, downloaded to
`~/agents/vendor/portfolio-zips/` and unpacked there. Neither carries a licence,
so both are reference only: patterns may be studied, code is never copied into
the site or any public repository.

1. `portfolio-2-website-code.zip` (3.2 MB): "Unifex", a digital agency and
   creative portfolio HTML template (static HTML, CSS, GSAP bundle, Bootstrap).
   A commercial theme by its title; treat it as someone else's licensed product.
   Static scan: seven pattern hits, all on minified libraries, a base64 image in
   the CSS and HTML comments; nothing hostile.
2. `portofolio-main.zip` (5.2 MB): a Vite, React, react-three-fiber, rapier,
   GSAP, motion, Tailwind and Firebase portfolio. Worth reading for how the 3D
   hero and GSAP timelines are wired, the same stack as keremozdemir.de/world.
   Static scan: 36 known-vulnerable pinned packages in its lockfile (OSV), so
   do not run `npm install` on it as it stands; a Firebase web config is present in the source, so the author's project id is in there as well.
