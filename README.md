# LeadEight

Eight-bar live lead melody desk for bedroom producers and AI-music finishers stuck in loops.

Enter your BPM (60–180), key, and 4-chord progression (example: Am F C G). LeadEight lays a real-sample lead line (and optional bass) over it so the section has a melodic voice and the track can finish. Live mutes take effect within one bar. Export WAV (48 kHz / 24-bit, exact bar length, first downbeat at sample 0, seamless loop by folding the tail) + MIDI (one track per chair) that drops into any DAW on the grid.

## Samples
Place honest CC0 instrument samples in `public/samples/`:
- lead.wav (flute, violin, or piano – named after the real instrument)
- bass.wav (electric or upright bass)

Never pitch more than ±4 semitones. Preload shows progress; missing samples are named in the UI.

Free to use. Pricing recommendation: one-time $29 on Gumroad (full sample pack + future updates). Best place to sell: Gumroad or Lemon Squeezy for music producers.

## Audio Engine
Follows WorkinWithAI rules:
- Lookahead scheduler on AudioContext clock (LOOKAHEAD_MS=25, SCHEDULE_AHEAD=0.12)
- Live state object for BPM, key, chords, mutes
- Stop silences active sources immediately
- Exports: OfflineAudioContext, exact sample count, no random jitter, 48k/24bit, MIDI alongside
- Samples pinned/bundled, honest voices
- Visibility change stops cleanly

## Acceptance checks
(1) Export at 92 BPM, 8 bars, 48 kHz: exactly 1,001,739 samples, first transient within 1 ms of sample 0.
(2) Import WAV at bar 1 of 92 BPM DAW, loop 4×: no clicks, no grid drift.
(3) Play, switch tab 30s, return: stopped cleanly, no stacked notes.
(4) Change recipe/mutes/BPM while playing: heard within one bar, no restart.
(5) Block sample host: UI names missing instruments.
(6) Longest pad/note sustains to end.
(7) No @main/@gh-pages, no Math.random in export path, voice names match samples.

Distinct from yesterday’s AnchorGroove (rhythm section focus). This is melodic lead finish.
