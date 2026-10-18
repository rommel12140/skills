# Spatial scenes, shaders and delivery

Read this when the signature depends on depth, material, a camera, image deformation or a WebGL transition.
Choose the scene from the subject first, then choose Three.js, React Three Fiber or plain WebGL to fit the existing stack.
Plain WebGL suits a small image-plane effect with an established renderer; Three.js supplies scene, material and loader infrastructure; R3F fits a React application that already owns component lifecycles.
Do not add a second renderer merely to animate a heading.
The techniques below are recommendations, informed by the [studio research](motion-research.md).

## Scene types with a job

| Scene | What to build | Choreography and alternate version |
| --- | --- | --- |
| Product assembly | A correctly proportioned GLB with named parts, pivots, an environment and baked AO | Scroll separates parts as DOM labels explain construction; reduced motion shows an assembled view and a labeled exploded still |
| Material study | A close surface with designed roughness, directional light, normal detail and a constrained inspection area | Pointer or scroll reveals how the actual surface catches light; touch has an explicit inspect action and a high-quality still |
| Spatial editorial sequence | One camera rail and target rail through a few composed views | Stage context before camera travel; preserve direct section links and a vertical still sequence |
| Work index into case study | One persistent image plane or mesh, with DOM-aligned initial and final bounds | Selected image expands while its title remains identifiable; ordinary navigation retains the same image without the transition |
| Subject-derived simulation | A bounded field that expresses the real material, such as cloth, fluid or type particles | Bake repeatable animation or run the simulation at reduced resolution; preserve a composed poster and the meaningful final state |

Draw three camera states and the composition at the two handoffs before detailing a model.
Prototype grey geometry and real HTML together.
Match perspective, crop, light direction, object scale and reading space before adding surface effects.
A rotating stock torus with no relationship to the brand is a failed concept even at 60fps.

## Build a 3D object to a finished standard

Use this process whenever the signature is a modelled object: a product, a plant, a tool or a mark given depth.
A scene can be smooth, well lit and cheap and still fail because the object reads as a flat illustration.
The bar is what a reviewer sees at the object's real size in the page, not the toolchain or the polygon count.
A deliberately stylized object, such as a flat-shaded or low-poly mark, keeps the same bar for silhouette, proportion, junctions, pose, composition and cost, and records its stylization as the decision.

### The quality bar

- The silhouette comes from the real subject or the approved source art, and stays recognizable at small and full display size.
- Every structural part has volume.
  Supports have a shaped cross-section that tapers along a traced axis, thin parts are closed shapes with edge thickness, and no part relies on colour alone to look solid.
- Repeated parts vary one by one, in cup, curl, twist or fold, so each catches the light differently.
- Parts grow out of their supports: junction proportions match the subject, and material blends along the real form rather than along a painted mask.
- Each face and material has its own pigment and roughness, fine detail comes from a normal map, contact shading is baked, and highlights stay restrained.
  Plastic gloss, noisy weathering and lighting painted into the pigment fail.
- The object holds up through its whole motion, front, back, three-quarter, edge-on and the frames between, and it rests only in poses that read as the subject.
- It keeps a stated relation to the type at every width, as [layout and surfaces](layout-and-surfaces.md#establish-a-composition) requires.
- It draws nothing at rest, meets the [budget](#performance-and-accessibility-budget), and has an equally composed still for reduced motion, missing WebGL and software rendering.
- The report names what the object is: an authored interpretation is never presented as a scan or a photograph.

### Steps

1. Study references before modelling.
   Collect close photographs of the real subject from a reliable source, and note what each one informs, such as vein contrast, sheen or fibre direction.
   Use references to judge the model, not as embedded assets, unless their rights are clear.
2. Block the form in grey at its real display size, with the real type and the page's light.
   Settle silhouette, proportion, pose and the relation to the type at 1280, 1440 and 390 before any surface work.
3. Build the structure.
   Trace the outline and main axis from the source, give each support a shaped cross-section, and build each repeated part as its own closed piece with a root that meets its support.
   Add per-part variation and edge thickness.
   Generate the geometry with a deterministic script so it can be rebuilt and regression-tested.
4. Author the materials.
   Remove painted light from the pigment maps so the scene's light does the shading, keep fine detail in a normal map, and give each face its own pigment and roughness.
   Bake contact occlusion, pigment variation and fibres into the maps.
   An offline tool such as Blender run headless is a fine authoring step, but never a runtime or build dependency.
   Add specular response and light transmission only as far as the subject shows them.
5. Fit the budget.
   Sample geometry by visible size: dense along long parts, sparse on tiny ones.
   Pack and compress the model, ship smaller maps to phones, keep one draw call where the subject allows, and regenerate delivery files in the production build so stale assets cannot ship.
6. Wire the delivery.
   Render on demand with [the starter below](#threejs-starter-render-only-when-the-scene-changes), and lower render resolution only under measured GPU pressure.
   Treat a software renderer as missing WebGL: request `failIfMajorPerformanceCaveat` and check the reported renderer name, such as SwiftShader or llvmpipe, then show the still.
   Capture posters and stills from the renderer itself at the poses the page uses, and recapture them after any change to geometry, materials or light.
   Fade a moving object as one layer, drawn opaque and faded as a whole, so its folded parts never show through each other.
   Draw the loading indicator from the same silhouette, as [the loader gate](../SKILL.md#no-generic-loaders-progress-bars-or-decorative-slop) requires.
7. Review against matched captures.
   Compare candidate and accepted version at the same viewport, pose, light and progress: front, back, three-quarter and edge-on, plus a turning sequence forward and back.
   Inspect close-ups at the base, middle and tip, then the object at its real size in the page, in both themes and on a phone.
   Compare pixels with and without the object inside each line of nearby text, and measure the contrast of any text it passes behind.
   Record idle draws, a throttled-phone trace, transfer bytes, GPU memory, and the software and no-WebGL paths; extra offscreen draws can stand in for a weaker GPU.
   Present one result for visual acceptance, because passing tests do not establish it.

When a round is rejected, reproduce the reviewer's pose and size first, then name the layer that failed: silhouette, structure, junction, surface, pose, composition or cost.
Fix that layer.
A shading change the reviewer cannot see is a failed round, and when the form is wrong, rebuild the geometry rather than adjusting the light.

### Worked example: a botanical hero object

A fern frond with a green upper face and a pale underside, turned by scroll in a portfolio hero, went through these rounds between 22 September and 10 October 2026.

| Version | What was wrong | What fixed it |
| --- | --- | --- |
| Tinted stalk on a flat leaf sheet | The stalk had no depth, and its colour mask missed the real curve, so it looked coloured in | A closed, tapered support following the traced ridge |
| Leaf bases | The mask left the stalk's shoulders green, so the blades read as joined to each other | Shoulders measured from the gaps between blades, with material blended into each insertion |
| Thicker stalk | Its diameter came from the broad shoulders, so it looked bulky and the joins flared | A slender profile resampled locally around the axis |
| Subtle shading pass | The front view looked unchanged | 36 closed blades with their own cup, curl, twist, edge thickness and raised midribs, a 16-sided stalk, separate front and back materials, and baked contact occlusion |
| First full rebuild | 61,518 vertices, a 1.8 MB model and 1.3 MB of maps | A packed model and lossy maps, then sampling by visible size: 28,808 vertices and about 0.6 MB with maps, with veins, fibres and a grooved stalk moved into the baked maps |
| Hero placement | It overlapped the name's letters, then slid off the centre | One stated relation, slanting through the centre between the name and the introduction, with a pixel check of each text line |
| Idle page | 300 draws in five idle seconds | Render on demand: zero draws at rest |
| Loader | A separate progress line, then a clipping version that cost more main-thread time | The same silhouette filling from base to tip by moving gradient stops only |
| Edge-on rest pose | It did not read as a leaf | A three-quarter pose |
| Software graphics | Stutter doubled on a simulated slow laptop without GPU acceleration | A still render when a software renderer is detected |

## Asset pipeline and scene ownership

Use GLB/glTF for interchange, with meaningful node names, applied transforms, correct pivots and documented units.
Export only the meshes, cameras, textures and animation clips the scene needs.
Bake AO and repeatable motion; use a matcap or environment map when it preserves the intended material without live reflections.
Use Meshopt or Draco for geometry where decode cost is justified, and KTX2/Basis textures where supported by the asset pipeline.
Configure the matching loader/decoder paths explicitly and handle failure.
Transfer compression is not GPU-memory compression: a small JPEG can still occupy a large RGBA texture after upload.

Keep the product, captions, navigation, primary action and alternative explanation in semantic HTML.
Treat decorative canvas content as `aria-hidden`; interactive 3D needs equivalent named DOM controls and a visible selected state.
Use one renderer across related sections when continuity matters, and one owner for scroll progress, camera and object transforms.
A model-loading callback must not add an object after the route has unmounted.
Dispose geometries, materials, owned textures, render targets, observers and listeners; cached resources need a shared ownership policy.
Sources: [GLTFLoader](https://threejs.org/docs/#GLTFLoader), [KTX2Loader](https://threejs.org/docs/#KTX2Loader), [cleanup](https://threejs.org/manual/en/cleanup.html).

## Three.js starter: render only when the scene changes

This pattern takes a scene builder so an actual product model or original geometry can supply the subject.
`buildSubject` returns an owned `object`, a deterministic `pose(progress)` function, and `dispose()` for its resources.
It can use `GLTFLoader.loadAsync`; a late result is disposed if the route has already gone away.
Keep a poster in the same aspect-ratio slot underneath the canvas.
Mount only for normal motion; on reduced motion, dispose the scene and show the authored still explanation.

```js
import * as THREE from "three";

export function mountSpatialScene(slot, buildSubject) {
  const canvas = slot.querySelector("canvas");
  canvas.hidden = true;
  slot.classList.remove("is-spatial-ready");
  let renderer;
  try {
    renderer = new THREE.WebGLRenderer({ canvas, alpha: true, antialias: true });
  } catch {
    return { setProgress() {}, dispose() {} };
  }
  renderer.setPixelRatio(Math.min(devicePixelRatio, 1.5));
  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(35, 1, 0.1, 100);
  camera.position.set(0, 0.4, 5);
  camera.lookAt(0, 0, 0);
  scene.add(new THREE.HemisphereLight(0xffffff, 0x555555, 2));
  const key = new THREE.DirectionalLight(0xffffff, 3);
  key.position.set(3, 4, 2);
  scene.add(key);
  let subject, frame = 0, visible = false, dead = false, lost = false, ready = false, progress = 0;
  function invalidate() {
    if (frame || dead || lost || !ready || !visible || document.hidden) return;
    frame = requestAnimationFrame(() => {
      frame = 0;
      if (dead || lost || !visible || document.hidden) return;
      subject.pose(progress);
      renderer.render(scene, camera);
      canvas.hidden = false;
      slot.classList.add("is-spatial-ready");
    });
  }
  const resize = new ResizeObserver(([entry]) => {
    const { width, height } = entry.contentRect;
    if (width <= 0 || height <= 0) return;
    renderer.setSize(width, height, false);
    camera.aspect = width / height;
    camera.updateProjectionMatrix();
    invalidate();
  });
  resize.observe(slot);
  const visibility = new IntersectionObserver(([entry]) => {
    visible = entry.isIntersecting;
    invalidate();
  });
  visibility.observe(slot);
  const onVisibility = () => invalidate();
  const onLost = (event) => {
    event.preventDefault();
    lost = true;
    canvas.hidden = true;
    slot.classList.remove("is-spatial-ready");
  };
  const onRestored = () => { lost = false; invalidate(); };
  canvas.addEventListener("webglcontextlost", onLost);
  canvas.addEventListener("webglcontextrestored", onRestored);
  document.addEventListener("visibilitychange", onVisibility);
  const deadline = setTimeout(() => api.dispose(), 8000);
  const api = {
    setProgress(value) {
      progress = THREE.MathUtils.clamp(value, 0, 1);
      invalidate();
    },
    dispose() {
      if (dead) return;
      dead = true;
      clearTimeout(deadline);
      cancelAnimationFrame(frame);
      resize.disconnect();
      visibility.disconnect();
      document.removeEventListener("visibilitychange", onVisibility);
      canvas.removeEventListener("webglcontextlost", onLost);
      canvas.removeEventListener("webglcontextrestored", onRestored);
      subject?.dispose();
      renderer.dispose();
      canvas.hidden = true;
      slot.classList.remove("is-spatial-ready");
    },
  };
  Promise.resolve().then(buildSubject).then(async (loaded) => {
    if (dead) { loaded.dispose(); return; }
    subject = loaded;
    scene.add(subject.object);
    await renderer.compileAsync(scene, camera);
    if (dead) return;
    clearTimeout(deadline);
    ready = true;
    invalidate();
  }).catch(() => api.dispose());
  return api;
}
```

The eight-second enhancement deadline and DPR cap are starting choices, not library defaults or award requirements.
Set the slot's dimensions in CSS before mount and make the canvas fill it without changing layout.
Hide only the poster's visual layer with `.is-spatial-ready [data-poster] { visibility: hidden; }` after a successful frame, and restore it on failure or disposal.
Keep the equivalent semantic description outside that hidden layer so the alternative meaning remains available to assistive technology.
Drive `setProgress` from the same ScrollTrigger timeline as the DOM explanation.
For baked clips, use `AnimationMixer.setTime(progress * clip.duration)` with a non-looping clip, and test the exact endpoint so the final frame does not wrap to the beginning.
For a camera rail, sample a `CatmullRomCurve3` for position and another for the look target; reuse vectors instead of allocating them each frame.
Keep labels on a separate readable plane or in HTML.
Continuous simulation needs a controlled frame loop with offscreen/tab pause and a visible pause control when required; do not convert every scene to perpetual rendering.
Sources: [WebGLRenderer](https://threejs.org/docs/#WebGLRenderer), [AnimationMixer](https://threejs.org/docs/#AnimationMixer).

## React Three Fiber adaptation

Use `frameloop="demand"` for a scene whose appearance changes only when scroll or input changes.
Mutation in `useFrame` avoids React state updates on every frame.
The caller's stable progress store must expose `get()` and `subscribe(listener)`, returning an unsubscribe function.

```jsx
import { useEffect, useRef } from "react";
import { Canvas, useFrame, useThree } from "@react-three/fiber";

function Assembly({ progress, object }) {
  const part = useRef();
  const invalidate = useThree((state) => state.invalidate);
  useEffect(() => progress.subscribe(invalidate), [progress, invalidate]);
  useFrame(() => {
    const p = progress.get();
    part.current.rotation.y = p * Math.PI * 0.35;
    part.current.position.y = p * 0.2;
  });
  return <group ref={part}><primitive object={object} /></group>;
}

export function ProductCanvas({ progress, object }) {
  return <Canvas frameloop="demand" dpr={[1, 1.5]} camera={{ position: [0, 0, 5], fov: 35 }}>
    <hemisphereLight args={[0xffffff, 0x555555, 2]} />
    <directionalLight position={[3, 4, 2]} intensity={3} />
    <Assembly progress={progress} object={object} />
  </Canvas>;
}
```

The actual subject should articulate named parts rather than merely rotate the entire product.
This excerpt demonstrates frame ownership; the parent must mount it only while visible and normal motion is allowed, retain a poster, handle context loss, and place an error boundary around the canvas.
Provide an HTML loading state outside the canvas, not an unlabelled spinner in 3D space.
R3F does not automatically dispose the external object used by `<primitive>`; the asset owner must dispose it or release its cache reference on teardown.
For instanced parts, share geometry/materials and vary instance transforms; for repeated scenes, avoid allocating a new canvas per card.
Source: [R3F performance and invalidation](https://r3f.docs.pmnd.rs/advanced/scaling-performance), [R3F objects and disposal](https://r3f.docs.pmnd.rs/api/objects).

## Image distortion and displacement

Use a shader when the image's material or the change of context calls for deformation.
Keep captions, evidence and UI sharp in HTML.
The following fragments use Three.js `ShaderMaterial` with a plane whose vertex shader passes UVs.

```glsl
varying vec2 vUv;
void main() {
  vUv = uv;
  gl_Position = projectionMatrix * modelViewMatrix * vec4(position, 1.0);
}
```

A bounded inspection ripple samples a real displacement texture rather than generating unrelated full-screen liquid.
`uPointer` is normalized within the image, `uAspect` is the displayed image ratio, and `uStrength` is clamped in JavaScript to at most `0.025` as a starting bound.
Ramp it to zero on pointer leave and set it to zero for reduced motion.
Use a displacement asset whose directional structure belongs to the subject, such as paper grain or water recorded for a marine subject.

```glsl
uniform sampler2D uImage;
uniform sampler2D uDisplacement;
uniform vec2 uPointer;
uniform float uAspect;
uniform float uStrength;
varying vec2 vUv;
void main() {
  vec2 delta = (vUv - uPointer) * vec2(uAspect, 1.0);
  float lens = 1.0 - smoothstep(0.05, 0.35, length(delta));
  vec2 warp = texture2D(uDisplacement, vUv).rg * 2.0 - 1.0;
  vec2 uv = clamp(vUv + warp * lens * uStrength, 0.001, 0.999);
  gl_FragColor = texture2D(uImage, uv);
  #include <tonemapping_fragment>
  #include <colorspace_fragment>
}
```

Set the color image's texture color space correctly; keep the displacement texture as non-color data.
Account for `object-fit: cover` in the UV mapping when the image and plane have different aspect ratios.
Overscan or mirror the source at boundaries if clamping smears visible edges.
For a scene transition, use two image textures and a progress-controlled displacement envelope `sin(progress * PI)`, so distortion is zero at both endpoints.
Blend with a directional mask whose shape comes from the brand's aperture, cut, fold or manufacturing process.
Keep the incoming title and destination ready even if the shader fails.

## Noise and gradients with material direction

A gradient can model directional illumination, pigment or atmosphere within an actual scene.
Choose two or three sampled material colors, a light direction, a focal region and a small grain amplitude.
Keep it attached to the object or photographic treatment; a drifting mesh blob behind unrelated copy remains banned.
This static grain field avoids a perpetual time uniform and visible noise flicker.

```glsl
uniform vec3 uShadow;
uniform vec3 uLight;
uniform vec2 uDirection;
varying vec2 vUv;
float grain(vec2 p) {
  return fract(sin(dot(p, vec2(127.1, 311.7))) * 43758.5453);
}
void main() {
  vec2 direction = uDirection / max(length(uDirection), 0.0001);
  float light = smoothstep(-0.5, 0.5, dot(vUv - 0.5, direction));
  vec3 color = mix(uShadow, uLight, light);
  color += (grain(floor(vUv * 900.0)) - 0.5) / 255.0;
  gl_FragColor = vec4(color, 1.0);
  #include <tonemapping_fragment>
  #include <colorspace_fragment>
}
```

Use actual lights and surface normals for a volumetric object; this plane shader is an illustrative light field, not physically based shading.
Keep alpha and contrast under control when text overlaps it.
For vertex displacement, move along the surface normal with a bounded amplitude and sufficient subdivisions, then account for changed normals in lighting.
Do not use a high-frequency displacement on a low-poly plane and call the resulting facets a material choice unless that faceting is intentional.
Source: [ShaderMaterial](https://threejs.org/docs/#ShaderMaterial), [color management](https://threejs.org/manual/en/color-management.html).

## Performance and accessibility budget

The values below are prototype budgets for a typical brand homepage, not Awwwards rules or measured winner values.
Tune them against the audience's devices before enlarging the scene.

| Area | Starting budget or contract | Verify |
| --- | --- | --- |
| Frame delivery | Target 60fps on the agreed representative device; 16.7ms total frame time at 60Hz | Record a trace through the busiest scroll and transition, frame misses and long tasks; desktop emulation is not physical-phone evidence |
| Animation work | Aim below 8ms of app work per 60Hz frame to leave rendering headroom | Profile JS, layout, paint and GPU separately; inspect shader compile spikes |
| First useful render | HTML, CSS, fonts and poster within roughly 1MB transferred; critical JS within 200KB compressed where the stack permits | Cold cache with recorded network/CPU conditions; separate scene chunks from critical route code |
| First 3D scene | Begin around 2MB compressed models/textures plus the separately measured renderer chunk | Record both transfer and decoded/GPU allocation; defer later scenes |
| Render cost | Start at DPR 1 to 1.5, fewer than 100 draw calls, fewer than 200k visible triangles and at most one full-resolution post pass | Use `renderer.info`, a trace, and a physical phone where available; numbers are diagnosis aids, not quality scores |
| Textures | Prefer 1K/2K maps when their screen footprint permits; target about 64MB resident textures for the initial mobile scene | Include mipmaps, environments and render targets; a 2048-square RGBA8 texture is about 16MiB before mipmaps |
| Load behavior | Immediate poster and real controls; no artificial minimum loader duration | Slow, cached, failed decode, blocked GPU and enhancement deadline |
| Reduced motion | No camera travel, parallax, continuous simulation, lagging cursor or long empty pin distance | Initial preference and live change; preserve all meaning and actions in authored compositions |
| Semantics and input | Semantic HTML, visible focus, native touch scroll, named alternatives for 3D actions | Keyboard journey, screen-reader check, coarse pointer and no hover |
| Failure and lifetime | Poster on context loss; dispose on route exit; no background/offscreen work without a reason | Context loss/restore, repeated visits, hidden tab and asset failure |

Optimize in this order: find the dominant cost, remove invisible work, batch or instance, compress and defer, reduce offscreen buffer resolution, bake expensive lighting/simulation, lower DPR, then recompose the same signature for constrained devices.
If real-time 3D still misses the budget, retain its composition and narrative in a rendered sequence or crafted still version.
Do not erase the central art direction and describe the resulting flat page as performance polish.
Keep the normal-motion version ambitious and the reduced-motion version equally composed.
Automatically moving content lasting more than five seconds alongside other content needs pause/stop/hide when WCAG's conditions apply, and audio begins only after user intent.
Sources: [rendering performance](https://web.dev/articles/rendering-performance), [Pause, Stop, Hide](https://www.w3.org/WAI/WCAG22/Understanding/pause-stop-hide.html), [Animation from Interactions](https://www.w3.org/WAI/WCAG22/Understanding/animation-from-interactions.html).
