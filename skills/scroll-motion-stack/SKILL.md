---
name: scroll-motion-stack
description: Builds scroll-driven sites on the Lenis + GSAP ScrollTrigger + Three.js stack: pinned sections, scrubbed timelines, a scroll-linked 3D hero, and the performance pass that keeps it at 60fps on a laptop. Use for a scroll-driven, cinematic or 3D-feeling website — "scroll animasyonu", "sayfa kaydirinca degissin", "Apple gibi zoom", "sinematik giris", "site premium dursun", "Awwwards tarzi", "scroll storytelling", "make the hero feel expensive" — and before shipping any scroll-heavy page. Not for UI micro-motion (use animate) or the AI-slop visual tells (use de-ai-slop-ui).
---

# Scroll-driven site stack

Award sites are not one secret tool. They are a small set of libraries combined
the same way every time, plus a discipline about which effects earn their cost.
This skill covers the scroll layer. Component-level motion belongs to `animate`.

## Pick the stack before writing anything

| Layer | Library | Use it when |
| --- | --- | --- |
| Motion engine | GSAP + ScrollTrigger | Always, for any scroll-tied animation |
| Smooth scroll | Lenis | Always, alongside GSAP - it gives ScrollTrigger a clean scroll value |
| Real-time 3D | Three.js | The scene reacts to input or data: particles, shaders, generative geometry |
| Designed 3D | Spline | The scene is static or lightly interactive and you want to light it by eye |
| 3D keyframing | Theatre.js | You need a GUI to direct a Three.js scene instead of hardcoding values |

Default to GSAP + Lenis only. Add a 3D layer **only when the brief requires it**,
and say so in one line before you add it. Most "3D" scroll effects on award sites
are not 3D at all - see the image-sequence section below.

Rule of thumb: "rotating object in the hero" → Spline. "particles that follow the
cursor" → Three.js. "product that rotates as I scroll" → image sequence, not 3D.

## The three scroll patterns

- **Pinning** - element stays fixed while the page scrolls past it, so its internal
  animation plays out fully before releasing.
- **Scrubbing** - animation progress is tied to scroll position, not to a duration.
  Scroll up and it reverses.
- **Staggered reveal** - groups of elements animate in with a delay between each.

```js
import Lenis from 'lenis';
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
gsap.registerPlugin(ScrollTrigger);

const lenis = new Lenis();
lenis.on('scroll', ScrollTrigger.update);
gsap.ticker.add((time) => lenis.raf(time * 1000));

gsap.timeline({
  scrollTrigger: {
    trigger: '.pin-section',
    start: 'top top',
    end: '+=2000',
    pin: true,
    scrub: 1,
  },
})
  .to('.title', { scale: 0.6, y: -200 })
  .from('.cards', { opacity: 0, stagger: 0.15 });
```

## The image-sequence trick

The Apple-style scroll-zoom is **not** live 3D rendering. It is a pre-rendered
frame sequence scrubbed on a canvas, which is why it holds 60fps on a phone that
would choke on WebGL.

1. Render the 3D model (Blender, Spline, or an AI video tool) as 60-150 frames.
2. Export each frame as WebP, numbered sequentially.
3. Map scroll position to a frame index with ScrollTrigger.
4. Draw that frame to a `<canvas>`.

```js
const canvas = document.querySelector('canvas');
const ctx = canvas.getContext('2d');
const frameCount = 120;
const images = [];

for (let i = 0; i < frameCount; i++) {
  const img = new Image();
  img.src = `/frames/frame_${String(i).padStart(4, '0')}.webp`;
  images.push(img);
}

function render(index) {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ctx.drawImage(images[index], 0, 0, canvas.width, canvas.height);
}

gsap.to({ frame: 0 }, {
  frame: frameCount - 1,
  snap: 'frame',
  ease: 'none',
  scrollTrigger: {
    trigger: '.scroll-zoom-section',
    start: 'top top',
    end: 'bottom bottom',
    scrub: true,
  },
  onUpdate: function () { render(Math.round(this.targets()[0].frame)); },
});
```

Preload the frames before the section enters, or the first scrub will stutter.

## Cinematic intro loaders

The first 2-3 seconds set the tone. A preloader is a first-impression device, not
a loading indicator. Four that work: a 0→100 progress counter, an SVG logo that
draws itself, a color panel that wipes away, a text-scramble headline.

Hold the loader for a **minimum** ~2s even when assets are already there - a
loader that flashes past reads as broken - but never past 2.5s.

```js
const counter = document.querySelector('.loader-count');
const overlay = document.querySelector('.loader-overlay');
let progress = 0;

const interval = setInterval(() => {
  progress += Math.random() * 12;
  if (progress >= 100) {
    progress = 100;
    clearInterval(interval);
    gsap.to(overlay, { yPercent: -100, duration: 1, ease: 'power4.inOut', delay: 0.3 });
  }
  counter.textContent = Math.floor(progress) + '%';
}, 120);
```

## Direction, not decoration

What separates an award site from a 3D demo is that every decision points the same
way. Enforce these four:

- **One accent color** for every interactive element - cursor, links, highlights.
  Never introduce a second.
- **One easing curve** across the whole site. Export it as a constant and import it
  everywhere; do not mix ease types per section.
- **Speed scales with size** - small UI moves in 200-300ms, full-page transitions in
  800ms-1.2s.
- **Background video and 3D scenes stay in 2-3 brand colors.** Recolor or desaturate
  anything that looks like stock.

```js
// motion.config.js - import this everywhere
export const EASE = 'power3.inOut';
export const DURATION = { fast: 0.3, base: 0.6, slow: 1.1 };
```

## Performance pass - run before calling it done

This is where clones die, and it is not optional.

**Mobile**
- Detect device and lower pixel ratio and particle count for real-time 3D.
- Compress GLTF/GLB with Draco or gltf-pipeline. Full-size models load on phones too.
- Background video needs `muted` and `playsinline` or mobile browsers block playback.

**Jank**
- Animate `transform` and `opacity`. Animating `top`/`left`/`width` forces layout
  every frame.
- Batch related animations into one timeline instead of many ScrollTrigger instances.
- `will-change: transform` on heavily animated elements, so they get a GPU layer.

**Verify**
- Lighthouse on **mobile**, not desktop.
- LCP under 2.5s, CLS near 0.
- Test on a real mid-range phone, not the dev machine.
- Drive the built page with the Playwright MCP: screenshot it, click every control,
  scroll the full page, and fix what breaks.

## Ship checklist

Small additions that separate a finished site from a demo. Add what the site needs,
not all of them.

Navigation: sticky header, scroll progress bar, back-to-top button, mobile menu,
skip-to-content link, site search.
State: loading animations, hover states, form success state, form error state,
confirmation modals for destructive actions.
Content: expandable FAQ, last-updated date, copy button on code and addresses,
print stylesheet.
Practical: dark mode toggle, cookie banner (essential-only by default), floating
contact, password visibility toggle, UTM tracking on campaign links.

## Prompting an AI for each piece

Name the exact libraries. "Add cool animation" produces generic output; "set up
Lenis smooth scroll and a GSAP ScrollTrigger timeline that pins `.hero` for 2000px
and staggers `.feature-cards` as it unpins" produces the thing you asked for.
