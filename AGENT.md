# Project Rules & Hard Constraints

## Core Technical Rules

- **Product**: "Lazy Girl Clicker: Lo-Fi Edition" — a single-screen tap-to-earn clicker game with a Spotify-inspired music disc feature.
- **Single File Architecture**: Everything MUST be in a single `index.html` file (all inline CSS in `<style>` tags and all Vanilla JavaScript in `<script>` tags).
- **No Frameworks / Dependencies**: Strictly no external frameworks, libraries, npm packages, or build tools. System font stacks only.
- **Data Source**: Unlockable data (snacks, music1, music2, music3, music4, music5) based on `UNLOCKS.md`. Track data based on `TRACKS.md` with integrated YouTube streaming.
- **State Management**: Application state (energy, owned unlockables, current track index) and persistence handled via `localStorage`.
- **Character**: A single custom-drawn character (inline SVG with full hair, bangs, twin buns, and star hairclip) represents the "lazy girl." No external image assets.
