# Tasks

## Phase 1 — Core loop (visible)
- [1.1] Build page shell, Lofi RPG color/type tokens, character SVG with full hair, energy counter.
- [1.2] Wire tap handler: +1 energy, bounce animation, tap pop sound. (Req 2)
- [1.3] Load/save state from `localStorage` on init and after every change. (Req 1, 3)

**Verify**: opening `index.html` shows the character and counter; tapping
increases energy and the value survives a page reload.

## Phase 2 — Unlockables (Snacks + Music 1-5)
- [2.1] Render 6 unlock cards from `UNLOCKS` with locked/unlocked visual states. (Req 4, 5)
- [2.2] Wire unlock click: spend energy, mark owned, persist. (Req 6)
- [2.3] Build dialogue bubble + auto-hide timer, trigger on unlock. (Req 6, 9)

**Verify**: earning enough energy enables a card; clicking it spends energy,
shows a dialogue line, and stays unlocked after reload.

## Phase 3 — YouTube Music Disc Player
- [3.1] Build disc widget (hidden by default), reveal when any music track is owned. (Req 7)
- [3.2] Wire disc click: advance track, spin/pulse animation, update label, stream real audio. (Req 8)
- [3.3] Responsive pass for mobile widths. (Req 10)

**Verify**: unlocking music reveals the disc; clicking it cycles unlocked YouTube tracks and
the current track survives reload.
