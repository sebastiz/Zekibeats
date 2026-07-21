# Dance Track Maker — Step Seq · 16

A dance track maker that runs entirely in the browser. Everything is synthesized live with the Web Audio API — no samples, no build step, no dependencies beyond React loaded from a CDN.

**Live app:** https://sebastiz.github.io/dance-track-maker/

## Features

- **10-track drum machine** — kick, snare, clap, rimshot, closed/open hats, low/high toms, cowbell, ride. All sounds generated with oscillators and filtered noise (909/808-style recipes).
- **Bass synth** — 303-style monophonic piano roll (A minor, one octave) with four voices (saw, square, sub, FM) and live cutoff/resonance for acid sweeps.
- **Lead synth** — one octave up, four voices (pluck, saw, bell, chip).
- **Chord machine** — one-tap Am/F/C/G stabs with stab, pad, and organ voices.
- **Clip matrix** — each section (drums, bass, lead, chords) has four independent patterns (A–D), Ableton Session View style.
- **Song mode** — a 16-bar × 4-section arrangement grid. Tap cells to cycle A→B→C→D→off; empty cells silence that section for the bar, which is how intros, breakdowns, and drops are built.
- **FX rack** — drive (waveshaper), bipolar DJ filter (LP/HP sweep), tempo-synced feedback delay, convolution reverb, sidechain-style pump, and a glue compressor on the master. Per-section delay/reverb sends.
- **Timing** — lookahead scheduler on the audio clock (rock-solid on mobile), tempo 90–160 BPM, adjustable swing.
- **WAV export** — renders the current pattern or the whole song arrangement offline at 44.1 kHz and downloads a 16-bit stereo WAV.

## Quick start

1. Press **PLAY** — it starts with a house groove.
2. Tap grid cells to toggle hits/notes. While stopped, tapping auditions the sound.
3. Open **SONG** mode and tap arrangement cells to build the track structure.
4. **EXPORT TRACK** to download the WAV.

## Tech notes

- Single-file, pre-compiled build (`index.html`) — the JSX is compiled ahead of time with Babel so nothing compiles in the browser.
- One `AudioContext`; per-section gain buses feed a master chain (drive → DJ filter → compressor → pump), with delay and reverb as sends.
- The offline WAV export rebuilds the identical engine in an `OfflineAudioContext`.

## License

MIT
