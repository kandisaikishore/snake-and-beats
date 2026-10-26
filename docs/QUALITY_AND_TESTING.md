# Gameplay QA and Development Guide

Snake and Beats is a Snake-inspired game with a music-themed presentation. Use the current source to confirm the actual runtime, controls, audio behavior, and available scripts.

## Setup

```bash
git clone https://github.com/kandisaikishore/snake-and-beats.git
cd snake-and-beats
```

For a static web version, open its main HTML file in a modern browser. If the repository has a package manifest, use the declared install, test, and build scripts.

## Gameplay test matrix

- Start, pause, resume, restart, and game-over transitions
- Wall and self-collision boundaries
- Food/target placement and score updates
- Keyboard input and any supported touch controls
- Repeated pause/resume and restart actions
- Missing or failed audio/assets where applicable
- Resize behavior and responsive layout

## Deterministic timing

If the game loop uses timers or animation frames, ensure only one active loop runs at a time. Clear timers/listeners on pause, restart, and unmount. Game state must stop changing while paused or after game over. Prefer fake timers or controlled frame advancement in tests rather than waiting in real time.

## Accessibility and performance

Provide visible instructions and meaningful control feedback. Check keyboard operation and avoid relying on sound alone to communicate critical game state. Test at supported viewport sizes and watch for duplicate loops or excessive updates.

## Pull-request checklist

- [ ] Add regression tests for the changed game behavior.
- [ ] Verify collision, scoring, pause/resume, and restart paths.
- [ ] Run the declared test/build scripts.
- [ ] Check browser console and asset loading.
- [ ] State which checks could not be run.
