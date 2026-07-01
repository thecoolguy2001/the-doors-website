# DOORS

An infinite dream you wander forever — open, surreal low-poly **worlds** drowned
in colored fog. **LSD: Dream Emulator**, reborn in the browser.

Roam a world. Touch a glowing gate — or just wander to the edge — and the dream
fades, re-seeds, and drops you into a completely different one. There is no end.

## Run it

ES modules need to be served over HTTP (not `file://`). From this folder:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

Click to enter, then:

- **W A S D** / **arrow keys** — wander
- **mouse** — look around
- **shift** — run
- **touch a glowing gate** (or reach a world's edge) — slip into the next dream
- **esc** — wake (release the mouse)

## How it works

- Every world is **randomly assembled** from a clashing neon palette + a
  rarity-weighted bag of features, so no two are ever the same. Common things
  (flower **decals**, **floaters**, **monoliths**, **buildings**, **pillars**)
  show up often; rare things seldom — giant floating **face-orbs**, **eyeballs**,
  wandering rainbow **creatures**, **crystals**, **pools**, torii **arches**,
  face **totems**, enterable **houses**, **orbits**, **floating islands**,
  eye **watchers** that track you, a huge breathing **giant sleeper**, and a
  slow **chaser** you do not want to be caught by.
- Worlds also vary at the top level: **enclosed** indoor rooms vs open sky,
  different ground patterns (checker, stripes, rings, noise, katakana text,
  grid, spiral), different skies, and a per-world **scale** so some dreams are
  tiny and some colossal. Solid structures have **collision** so you navigate
  around them.
- Floors and structures wear busy procedural textures, all nearest-filtered for
  crunchy pixels.
- Walking through a **door** (they emit a light beam so you can find them)
  derives the next seed — deterministic but effectively endless.
- The **PS1 look** is deliberate: low internal resolution scaled up (chunky
  pixels), a vertex-jitter shader that snaps geometry to a coarse grid (the
  classic PS1 wobble), and flat **unlit** bold colors.
- Runs fully **offline**, zero build step (Three.js loads from a CDN).

## Notes

- Renderer is Three.js **WebGL** (rock-solid everywhere) rather than raw WebGPU.

---

<details>
<summary>⚠️ spoiler — how to escape the dream</summary>

There is a hidden win condition, with no in-game instructions by design.

Rarely, a world contains a **circle of robed figures holding hands**. Step into
the **centre** of that circle to complete it (once per world). Each completion
warps reality a little more — geometry wobbles, colours start to cycle, and the
world snaps coarser. That escalating distortion is the *only* feedback.

Complete the circle in **10 different worlds** and the dream releases you.
Because the circle worlds are rare and there is no counter shown, this is meant
to take a very long time and to be discovered, not told.

</details>

— Part of a 30-for-30: one project every day in June.
