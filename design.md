# Design

## File structure (single `index.html`)

- `<style>` — CSS custom properties for the color/type tokens, layout (centered
  "cozy nook" card), character + disc animations, responsive breakpoints.
- `<body>`
  - `.scene` (outer wrapper)
    - `.sound-toggle-bar` — sound on/off toggle button + eyebrow
    - `.energy-bar` — counter + label
    - `.character` (inline SVG "lazy girl", tappable)
    - `.dialogue-bubble` — hidden by default, shown via JS
    - `.unlocks` — six `.unlock-card` elements (snacks / music1 / music2 / music3 / music4 / music5)
    - `.disc-widget` — hidden until a music track is owned; spinning disc + current
      track title/artist, play/pause and next controls
- `<script>` — CONFIG constants, state load/save, Web Audio FX, YouTube IFrame audio streaming, render, event handlers.

## Data shapes

```js
const UNLOCKS = [
  { id: 'snacks', label: 'Snacks', emoji: '🍫', cost: 15, dialogues: [ /* 3 lines */ ] },
  { id: 'music1', label: 'Music 1', emoji: '🎵', cost: 40, dialogues: [ /* 3 lines */ ] },
  { id: 'music2', label: 'Music 2', emoji: '🎶', cost: 90, dialogues: [ /* 3 lines */ ] },
  { id: 'music3', label: 'Music 3', emoji: '🎧', cost: 130, dialogues: [ /* 3 lines */ ] },
  { id: 'music4', label: 'Music 4', emoji: '🎸', cost: 160, dialogues: [ /* 3 lines */ ] },
  { id: 'music5', label: 'Music 5', emoji: '🦇', cost: 210, dialogues: [ /* 3 lines */ ] },
];

const TRACKS = [
  { id: 'music1', videoId: 'l5sgIqzlPXc', title: 'Maula Mere Maula', artist: 'Mithoon and roopkumar Rathod' },
  { id: 'music2', videoId: 'j18MRhEfmPk', title: 'Ishqa Ve', artist: 'Zeeshan Ali' },
  { id: 'music3', videoId: 'RHcnVLbl2Z4', title: 'Khairiyat', artist: 'Arijit Singh' },
  { id: 'music4', videoId: 'NAkQVL61BRI', title: 'Raga of Revenge', artist: 'anirudh Ravichandran' },
  { id: 'music5', videoId: 'xnP7qKxwzjg', title: 'Dracula', artist: 'Tame Impala' },
];
```

## State & persistence

```js
{
  energy: number,
  owned: { snacks: boolean, music1: boolean, music2: boolean, music3: boolean, music4: boolean, music5: boolean },
  trackIndex: number
}
```

Stored under `localStorage` key `lazyGirlClicker.v2`. Read once on init, written after every mutation.

## Interaction flow

- **Tap character** → energy += 1 → bounce animation + sound effect → re-render energy + card affordability → save.
- **Unlock click** (only reachable if enabled) → spend energy → mark owned → play unlock chime + show dialogue → reveal disc widget & start YouTube audio → save.
- **Disc click / Play/Pause** (only if music owned) → toggle play/pause on active YouTube audio stream → toggle spin animation → save.
- **Next track click** → advance to next unlocked track → load and play video → show dialogue → save.
- **Dialogue bubble** → any dialogue call sets text + visible class, clears any prior hide-timer, sets a new one (~2.8s) to remove visible class.
