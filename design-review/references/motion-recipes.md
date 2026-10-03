# Motion implementation recipes

Use the mechanism that serves the chosen signature, not every recipe on the same page.
These are adaptable starter patterns, not a complete router or production scene.
Confirm installed versions and stack ownership first.
GSAP examples use the GSAP 3 APIs; SplitText's `mask`, `autoSplit` and `onSplit` pattern requires 3.13 or later.
Import and register plugins once in the application's animation module.
Use the framework's client mount and unmount lifecycle; do not initialize browser code during server rendering.

## GSAP and ScrollTrigger: one timeline owns the scene

Compose a material reveal around a fixed explanation: an assembled product opens into a cutaway, then its image becomes evidence in the next section.
Keep the text and link visible from first paint.
Use one normalized progress value for DOM, camera and shader state when they describe the same event.
Do not run independent scroll listeners that fight over the same transform.

Required markup: `[data-story]` contains `[data-stage]` with a decorative `[data-shell]` over `[data-cutaway]`, plus a `[data-explanation]` wrapper holding ordinary HTML.
Give images intrinsic dimensions and the stage a real aspect ratio.
The default CSS shows the resolved cutaway; only successful enhancement establishes the assembled state.

```css
[data-stage] { position: relative; aspect-ratio: 4 / 3; }
[data-shell], [data-cutaway] { position: absolute; inset: 0; width: 100%; height: 100%; object-fit: cover; }
[data-shell] { visibility: hidden; }
[data-explanation] { position: relative; }
@media (min-width: 48rem) {
  [data-story] { display: grid; grid-template-columns: minmax(0, 1.4fr) minmax(0, 1fr); gap: 2rem; align-items: start; }
  [data-story].is-moving { min-height: 180svh; }
  .is-moving [data-stage] { position: sticky; top: 12svh; }
}
@media (prefers-reduced-motion: reduce) {
  [data-story].is-moving { min-height: 0; }
  .is-moving [data-stage] { position: relative; top: auto; }
}
```

```js
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export function mountStory(root, paintScene = () => {}) {
  const mm = gsap.matchMedia();
  mm.add({
    motion: "(prefers-reduced-motion: no-preference)",
    reduced: "(prefers-reduced-motion: reduce)",
    wide: "(min-width: 48rem)",
  }, ({ conditions }) => {
    const shell = root.querySelector("[data-shell]");
    if (!conditions.motion) {
      paintScene(1);
      return;
    }
    root.classList.add("is-moving");
    const progress = { value: 0 };
    gsap.set(shell, { visibility: "visible", clipPath: "inset(0% 0% 0% 0%)" });
    const timeline = gsap.timeline({
      paused: true,
      defaults: { ease: "none" },
      onUpdate: () => paintScene(progress.value),
    });
    timeline.to(progress, { value: 1, duration: 1 }, 0)
      .to(shell, { clipPath: "inset(0% 100% 0% 0%)", duration: 0.65 }, 0.15);
    ScrollTrigger.create({
      animation: timeline,
      trigger: root,
      start: conditions.wide ? "top top" : "top 80%",
      end: conditions.wide ? "bottom bottom" : "bottom 20%",
      scrub: true,
      invalidateOnRefresh: true,
      onRefresh: (self) => paintScene(self.progress),
    });
    paintScene(timeline.progress());
    return () => root.classList.remove("is-moving");
  });
  let alive = true;
  document.fonts.ready.then(() => { if (alive) ScrollTrigger.refresh(); });
  return () => { alive = false; mm.revert(); };
}
```

`matchMedia` reverts its GSAP animations and triggers when conditions change or the owner unmounts.
Keep default CSS useful when JavaScript, images or WebGL fail.
This uses CSS sticky rather than an extra pin spacer; if the actual storyboard needs pinning, pin the stage, never a transform owned by another timeline.
On phones the stage stays in normal flow, with its reveal happening while it enters the viewport and no extra narrative scroll height.
Build the timeline before attaching the trigger and synchronize its initial progress, including direct loads partway through the scene.
Keep explanation outside the moving crop so sticky media cannot cover the text it explains.
Measure geometry after media sizing and fonts settle, and refresh after layout-changing CMS content.
Do not use `ScrollTrigger.killAll()` in a reusable component because it also destroys unrelated scenes.
Native smooth scrolling must be disabled on the scroller when another owner controls it.
Source: [ScrollTrigger](https://gsap.com/docs/v3/Plugins/ScrollTrigger/), [matchMedia](https://gsap.com/docs/v3/GSAP/gsap.matchMedia()/).

## Lenis: smooth input with one frame clock

Use Lenis when controlled scroll velocity materially improves a scene or image handoff.
It does not create choreography by itself.
Keep native touch behavior as the first mobile choice, and preserve the scrollbar, anchor destinations and keyboard navigation.
Install Lenis's stylesheet, then mount this at the application shell, not once per section.

```js
import Lenis from "lenis";
import "lenis/dist/lenis.css";

export function mountSmoothScroll(gsap, ScrollTrigger) {
  const mm = gsap.matchMedia();
  mm.add("(prefers-reduced-motion: no-preference) and (pointer: fine)", () => {
    const lenis = new Lenis({
      autoRaf: false,
      anchors: true,
      syncTouch: false,
      prevent: (node) => node.hasAttribute("data-native-scroll"),
    });
    const tick = (seconds) => lenis.raf(seconds * 1000);
    const update = () => ScrollTrigger.update();
    lenis.on("scroll", update);
    gsap.ticker.add(tick);
    return () => {
      gsap.ticker.remove(tick);
      lenis.off("scroll", update);
      lenis.destroy();
    };
  });
  return () => mm.revert();
}
```

The [official integration](https://github.com/darkroomengineering/lenis#gsap-scrolltrigger) also disables GSAP ticker lag smoothing with `gsap.ticker.lagSmoothing(0)`.
That changes a global setting: choose it once at the app shell if this is the page's frame-clock policy, never silently inside a reusable component.
Do not combine `autoRaf: true` with a second ticker or another smooth-scroll engine.
For a nested scroller, give ScrollTrigger the same `scroller` element; do not add `scrollerProxy` unless the integration actually requires it.
On route changes coordinate the single Lenis instance with the router's scroll restoration, hash handling and focus policy.
Test a focused field inside an overflowing dialog, Home/End, Page Down, direct hashes, browser Back and a live reduced-motion preference change.
Use `scroll-margin-top` for sticky headers and move focus to the destination when the navigation pattern requires it.
Locomotive Scroll v5 is itself built on Lenis, so do not stack both systems; see its [official documentation](https://scroll.locomotive.ca/docs/).

## Kinetic type: phrases, masks and readable meaning

Choose a text action from the subject: a line being typeset, a title opening like a book, a variable-width word making room for its evidence.
Animate a short display statement rather than all body text.
Use clipping or a meaningful axis change, not the banned fade-and-rise wrapper.
Keep the complete phrase readable in the accessibility tree and avoid splitting inline controls.

```js
import { SplitText } from "gsap/SplitText";
gsap.registerPlugin(SplitText);

export function mountHeadline(heading) {
  const mm = gsap.matchMedia();
  mm.add("(prefers-reduced-motion: no-preference)", () => {
    const split = SplitText.create(heading, {
      type: "lines,words",
      mask: "lines",
      autoSplit: true,
      aria: "auto",
      onSplit(self) {
        return gsap.from(self.words, {
          yPercent: 110,
          rotation: 2,
          transformOrigin: "0% 100%",
          duration: 0.7,
          ease: "power3.out",
          stagger: { amount: 0.18 },
          scrollTrigger: { trigger: heading, start: "top 88%", once: true },
        });
      },
    });
    return () => split.revert();
  });
  return () => mm.revert();
}
```

These timings are prototype values, not measurements of a winner.
Returning the tween from `onSplit` lets SplitText clean up and restore its time on reflow.
Its automatic ARIA naming does not preserve nested link semantics; use an unsplit semantic text layer and an `aria-hidden` visual duplicate when a heading contains interactive or important nested markup.
Check descenders, accents, selection, language changes, 200% text, font failure and late font loading.
For variable-font motion, verify that the supplied font actually contains the axis, bound its range, and measure the layout/paint cost; do not assume axis interpolation is compositor-only.
Source: [SplitText, responsive splitting and accessibility](https://gsap.com/docs/v3/Plugins/SplitText/).

## Hover and cursor character

Keep the native cursor unless a custom tool communicates an actual action such as inspecting material, dragging a reel or scrubbing a before/after.
A custom layer must be `aria-hidden`, `pointer-events: none`, constrained to the relevant surface, and absent for coarse pointers and reduced motion.
Keep visible instructions and native buttons for touch and keyboard users.
Do not move the click target toward or away from the pointer.

This bounded material response tilts only a decorative cover inside a stable link.
The focus-visible state uses a sharp outline and an immediately readable caption; it does not require simulated pointer coordinates.

```js
export function mountCoverHover(link, cover) {
  const mm = gsap.matchMedia();
  mm.add("(hover: hover) and (pointer: fine) and (prefers-reduced-motion: no-preference)", () => {
    const x = gsap.quickTo(cover, "rotationX", { duration: 0.25, ease: "power2.out" });
    const y = gsap.quickTo(cover, "rotationY", { duration: 0.25, ease: "power2.out" });
    let rect;
    const enter = () => { rect = link.getBoundingClientRect(); };
    const move = (event) => {
      if (!rect) enter();
      const clamp = gsap.utils.clamp(-0.5, 0.5);
      x(-clamp((event.clientY - rect.top) / rect.height - 0.5) * 8);
      y(clamp((event.clientX - rect.left) / rect.width - 0.5) * 8);
    };
    const reset = () => { rect = null; x(0); y(0); };
    link.addEventListener("pointerenter", enter);
    link.addEventListener("pointermove", move);
    link.addEventListener("pointerleave", reset);
    window.addEventListener("scroll", reset, true);
    window.addEventListener("resize", reset);
    return () => {
      link.removeEventListener("pointerenter", enter);
      link.removeEventListener("pointermove", move);
      link.removeEventListener("pointerleave", reset);
      window.removeEventListener("scroll", reset, true);
      window.removeEventListener("resize", reset);
    };
  });
  return () => mm.revert();
}
```

Apply perspective to the stable parent and leave its padding and hit area unchanged.
For a shader inspection lens, normalize pointer coordinates inside that surface and drive the bounded distortion in [WebGL craft](webgl.md#image-distortion-and-displacement).
Never attach a fluid trail to the whole site as an unrelated signature.

## Page and section transitions

Choose continuity: a selected project image becomes the incoming hero, a material mask opens the next view, or type maintains a baseline while context changes.
Keep ordinary links and one routing owner.
Do not install Barba over a framework router.

For a framework-native router, pair its route lifecycle with the View Transition API when supported.
The router supplies the actual DOM commit, document title, history, error handling and scroll restoration.
The adapter below supplies only optional animation and focus after a successful commit.
The commit callback must resolve after the incoming DOM is mounted; suppress duplicate navigation through the router's own pending state.

```js
export async function transitionRoute(commitRoute, focusDestination) {
  const reduced = matchMedia("(prefers-reduced-motion: reduce)").matches;
  if (reduced || !document.startViewTransition) {
    await commitRoute();
    focusDestination();
    return;
  }
  const transition = document.startViewTransition(commitRoute);
  // Unsupported captures can reject ready even when the route itself succeeds.
  void transition.ready.catch(() => {});
  const preference = matchMedia("(prefers-reduced-motion: reduce)");
  const skip = () => { if (preference.matches) transition.skipTransition(); };
  preference.addEventListener("change", skip);
  try {
    await transition.updateCallbackDone;
    focusDestination();
    await transition.finished;
  } finally {
    preference.removeEventListener("change", skip);
  }
}
```

Apply a unique `view-transition-name` only to the selected image in each view.
Do not give every card the same name, which invalidates the capture.
Use a short duration from [motion timing](motion.md#practical-timing-and-easing), with the visual moving toward the incoming composition.
For cross-document sites, evaluate same-origin `@view-transition { navigation: auto; }` support and keep ordinary navigation as the fallback.
Source: [View Transition API](https://developer.mozilla.org/en-US/docs/Web/API/View_Transition_API).

For an existing Barba site, use its `leave`/`enter` hooks for the transition and `afterLeave` to dispose the old page's triggers, observers and renderer.
Mount the incoming scene once in `afterEnter`, restore the expected hash or history position, and focus its heading with `tabindex="-1"` and `preventScroll` when appropriate.
Use `requestError` to release any covering layer and fall back to real navigation when fetching fails.
Test slow navigation, a failed route, double activation, modified-click/new-tab behavior, Back/Forward and a route cancelled during the effect.
Sources: [Barba hooks](https://barba.js.org/docs/advanced/hooks/), [Barba options](https://barba.js.org/docs/advanced/options/).

## Preloaders as an entrance

The loader can introduce the same object, silhouette or typography that resolves into the first scene.
Show the useful HTML and a composed poster immediately, and load only the assets that entrance actually needs.
Report real bytes only when totals are known; otherwise use one truthful status without a fake percentage.
Do not impose a minimum delay after readiness, block the primary action, or replay the full entrance on every route.
Set an enhancement deadline, then keep the poster and working page if decoding or shader compilation misses it.
Test the cached path as carefully as the cold path: a fast load should produce a coherent handoff rather than a flash of an overlay.
