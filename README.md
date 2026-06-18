# DOORS

An infinite, self-generating dream-house you walk through forever — every room
unique. **LSD: Dream Emulator**, reborn in the browser.

Walk through any doorway and the world fades, re-seeds, and rebuilds itself.
There is no end.

## Run it

ES modules need to be served over HTTP (not `file://`). From this folder:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

Click to enter, then:

- **W A S D** / **arrow keys** — move
- **mouse** — look around
- **walk into any glowing doorway** — fall into the next room
- **esc** — wake (release the mouse)

## How it works

- Each room is built from a numeric **seed**. Crossing a door derives a new seed
  from the old one + which door you took, so the dream is deterministic but
  effectively endless.
- Everything is **procedural**: palette, dimensions, fog, lighting, floating
  objects, and the framed wall "paintings" (generated on a `<canvas>`).
- Runs fully **offline** with zero build step (Three.js loads from a CDN).

## AI dream-images (optional hybrid mode)

The framed paintings can stream in real generated imagery and fall back to the
procedural art if anything fails. Before the page loads, set:

```html
<script>
  window.DOORS_CONFIG = {
    // {prompt} and {seed} are substituted in; must return an image.
    // Point this at YOUR proxy — never put an API key in client code.
    imageEndpoint: "https://your-proxy.example/dream?p={prompt}&s={seed}"
  };
</script>
```

The endpoint just needs to respond with an image (CORS-enabled). Without it,
the rooms stay 100% procedural.

## Notes

- Renderer is Three.js **WebGL** (rock-solid everywhere) rather than raw WebGPU.
  Same visuals, no flaky model/feature-detection on a one-day build.

— Part of a 30-for-30: one project every day in June.
