# Sequation default samples

Files in this folder are loaded automatically into bank slots on app startup.

## How it works

The HTML file looks for sample files at the URLs listed in
`window._defaultSamples` near the top of the JavaScript section.

Each entry in `_defaultSamples` looks like:

```js
{ slot: 0, url: 'samples/kick.wav', label: 'Kick' }
```

- `slot` — the bank tile index (0–69) the sample loads into
- `url`  — relative URL to the audio file
- `label` — display label (currently used internally; can be wired into UI later)

If a file is missing or fails to load, the slot keeps its synthesized sound —
no errors, no broken behavior. Safe to add or remove files without touching
the HTML.

## Default mapping (current)

| Slot | File         | Sound  |
|------|--------------|--------|
| 0    | `kick.wav`   | Kick   |
| 1    | `snare.wav`  | Snare  |

## Adding more samples

1. Drop the audio file into this folder (`.wav`, `.mp3`, or `.ogg`)
2. Open the HTML file
3. Find `window._defaultSamples` near the top of the `<script>`
4. Add an entry pointing at your new file

Example: to add a closed hi-hat at slot 2:

```js
window._defaultSamples=[
  { slot:0, url:'samples/kick.wav',         label:'Kick' },
  { slot:1, url:'samples/snare.wav',        label:'Snare' },
  { slot:2, url:'samples/hihat-closed.wav', label:'HH'   }
];
```

## About the included samples

The bundled `kick.wav` and `snare.wav` are **synthesized starters** — basic
sine-sweep kick and tonal-body + filtered-noise snare. They sound okay but
aren't audiophile material. Replace them with anything you like.

## Recommended sources for high-quality CC0 / royalty-free samples

- **freesound.org** — search for `cc0` tag. `deadrobotmusic` has whole CC0
  packs of kicks/snares.
- **99sounds.org** — free production-quality drum kits
- **pixabay.com/sound-effects** — royalty-free, no attribution needed
- **bedroomproducersblog.com** — curates legit free drum kits

## Format notes

- Mono or stereo, any sample rate (browser will resample)
- Keep them short (< 2s) for a snappy response
- Trim silence from the start so they trigger right on tap
