# Clockwork Picnic — Project Bootstrap

**Project:** Clockwork Picnic  
**Status:** Bootstrap complete; ready for pattern construction  
**Tracker:** MilkyTracker  
**Testing platform:** Linux / PikaOS  
**Target format:** 4-channel ProTracker MOD  
**Compatibility target:** ProTracker 2  
**Pattern length:** 64 rows  
**Baseline speed:** `06`  
**Baseline BPM:** `84` hex (132 decimal)

---

## 1. Current Goal & Next 3 Steps

### Current Goal

Compose an original, highly polished early-1990s Amiga-game-style `.mod` titled **Clockwork Picnic**, using authentic ProTracker 2 constraints, ST-01 samples, four channels, compact pattern reuse, and a definite non-fade coda.

The intended character is:

- jaunty, cheerful, engaging game-title / attract-mode music;
- piano-led;
- unmistakably tracker-built in rhythm, voicing, pattern reuse, and channel economy;
- contrasted by a haunting two-pattern PanFlute solo;
- informed by the spirit of Tim Wright and David Whittaker without imitating a specific piece;
- approximately 85–105 seconds, although musical flow and authenticity take priority over exact duration.

### Next 3 Steps

1. **Design the first pattern set and reusable pattern roles.**  
   Translate the structural arc and motif map into a compact initial pattern inventory. Establish which patterns are foundational, which are variants, and which are reserved for the PanFlute feature and coda.

2. **Compose and test the opening/main-theme patterns.**  
   Begin with the “Winding the Clock” material and establish the main RingPiano theme, SoftBass pulse, and core drum vocabulary in compiler-ready 64-row patterns.

3. **Develop the contrasting and terminal material.**  
   Write the two-pattern PanFlute section, then build the reprise and deliberate coda using pattern reuse plus a small number of purpose-built variants.

Do **not** finalize the complete order list before enough musical material exists to judge which patterns genuinely deserve reuse.

---

## 2. State of Play

### Source-of-Truth Hierarchy

Use this hierarchy whenever records disagree:

1. **Auditioned project files/settings are authoritative** for:
   - exact sample loop points;
   - exact sample volumes;
   - exact per-row volume edits;
   - exact finetune values;
   - any final by-ear edits.

2. **This bootstrap file is authoritative** for:
   - project architecture;
   - pattern roles;
   - order-list intent;
   - note/rhythm/effect structure;
   - final sample identities;
   - tested status.

3. **The ST-01/ST-02 archives are sample-file sources only.**

### Core Composition Rules

- 4 channels only.
- 64 rows per pattern.
- ProTracker-compatible effects only.
- No XM-only composition features.
- Global note range: `C-3` through `B-5`.
- Low-pitched samples should be restricted to octaves 4–5.
- High-pitched samples should be restricted to octaves 3–4.
- Forward sample loops only.
- No ping-pong loops.
- Pattern reuse is preferred.
- The composition must not loop indefinitely.
- The ending must be a deliberate coda, not a fade-out.
- Exact final runtime is secondary to musical flow, authenticity, and PT2 compatibility.
- Bonus objective: final `.mod` under 40 KB, but not at the expense of the music.
- Unless otherwise required, lone numbers should be written in hex.
- Explain effects the first time they are used.

### Locked Title & Tempo

- **Title:** Clockwork Picnic
- **Speed:** `06`
- **BPM:** `84` hex / 132 decimal

The title is the thematic seed: **clockwork** suggests interlocking, precise, reusable mechanical figures; **picnic** supplies warmth, cheerfulness, melody, and playfulness.

### Approved Instrument Set

All eight samples have been auditioned in a test pattern and passed.

| ID | Sample | Role | Volume | Finetune | Loop |
|---:|---|---|---:|---:|---|
| `01` | `ST-01/RingPiano` | Main piano / principal melody | `10` | `0` | No |
| `02` | `ST-01/PanFlute` | Haunting woodwind solo | `10` | `e` | No, provisionally |
| `03` | `ST-01/SoftBass` | Main bass | `40` | `f` | No |
| `04` | `ST-01/BassDrum3` | Kick | `28` | — | No |
| `05` | `ST-01/Snare1` | Snare | `2c` | — | No |
| `06` | `ST-01/CloseHiHat` | Closed hi-hat | `40` | — | No |
| `07` | `ST-01/Strings7` | Sustained harmonic bed | `20` | `2` | Yes |
| `08` | `ST-01/PingBells` | Mechanical sparkle / accents | `38` | — | No |

#### Finetune Notes

- `RingPiano`: base `0`; `+1` remains an acceptable by-ear alternative.
- `PanFlute`: base `e` (`-2`); `d` (`-3`) remains an acceptable by-ear alternative.
- `SoftBass`: `f` (`-1`).
- `Strings7`: base `2`; values `3`–`4` remain acceptable by-ear alternatives.

#### Strings7 Loop

- Start: `00f0`
- Length: `25bc`
- Loop type: forward only

### Practical Pitched Ranges

These are composition ranges, not merely the full playback range supported by the format.

- `01 RingPiano`: `C-3`–`C-5`; main melodic centre around octave 4 into octave 5.
- `02 PanFlute`: `G-3`–`B-4`; favour the middle of the range for the solo.
- `03 SoftBass`: `C-4`–`B-5`.
- `07 Strings7`: `C-3`–`B-4`.
- `08 PingBells`: `C-3`–`B-4`, usually favouring octave 4 upward.

Percussion should use consistent fixed playback notes once the preferred timbral pitch has been established during pattern writing.

---

## Structural Arc

### I. Winding the Clock

A compact opening that assembles the tune piece by piece.

- Begin with a small RingPiano figure and light mechanical percussion.
- Introduce bass after the initial idea is established.
- Let the full groove “snap” into place rather than starting with all channels saturated.
- Establish the clockwork identity before presenting the complete main tune.

### II. The Picnic Sets Off

The full main RingPiano theme.

- Bright, memorable, rhythmically nimble.
- SoftBass and percussion provide a characteristic bounce.
- PingBells appear as punctuation, not continuous decoration.
- This section should contain the material most worth reusing later.

### III. Clockwork Games

Recombine established material.

- Fragment or revoice the RingPiano theme.
- Reuse bass/drum logic from earlier patterns.
- Increase the role of PingBells and/or Strings7 selectively.
- Pattern reuse should become musically audible here rather than merely economical.

### IV. The Strange Little Wood

The required two-pattern PanFlute feature.

- PanFlute becomes the principal melodic voice.
- Strings7 provides sustained harmonic support.
- SoftBass supplies restrained movement.
- Percussion thins out.
- Pattern 1 of the solo should pose an idea; pattern 2 should develop and resolve it.
- The harmony may become wistful or ambiguous, but the section must remain recognizably part of Clockwork Picnic.

### V. Back to the Picnic

Return to the established RingPiano material.

- Prefer reuse of earlier patterns over rewriting the whole reprise.
- Use one or two strategically altered patterns if extra lift is needed.
- The familiar theme should feel refreshed by the preceding PanFlute contrast.

### VI. The Clock Springs Loose

Purpose-built coda.

- No fade-out.
- Break the established motifs into shorter fragments.
- Use piano fragments, bell answers, bass punctuation, and a coordinated final flourish.
- The ending should sound composed as an ending, not merely stopped.

---

## Motif Map

### Motif A — The Picnic Tune

**Voice:** RingPiano

A jaunty, syncopated melodic cell with a clear upward gesture followed by a playful downward answer.

Functions:

- main thematic identity;
- transposition;
- fragmentation;
- rhythmic displacement;
- reprise material;
- coda fragments.

### Motif B — The Clockwork Step

**Voices:** SoftBass + BassDrum3

A short alternating bass figure tightly coupled to the kick.

Functions:

- rhythmic engine;
- creates the “ticking” impression through deliberate gaps;
- survives beneath multiple melodic patterns;
- one of the main mechanisms for pattern reuse.

### Motif C — The Cutlery Rattle

**Voices:** CloseHiHat + Snare1

A light, slightly asymmetric percussion figure.

Functions:

- mechanical subdivision;
- rhythmic bounce;
- easy variation by omitting hats or shifting occasional snare accents;
- supports both main-theme and transition material.

### Motif D — The Glint

**Voice:** PingBells

Sparse two- or three-note answering figures.

Functions:

- metallic clockwork punctuation;
- transition accents;
- call-and-response with RingPiano;
- possible coda ingredient.

Use sparingly. It is an accent voice, not a permanent arpeggio layer.

### Motif E — The Long Grass

**Voice:** Strings7

Sustained harmonic support.

Functions:

- bridges between sections;
- provides continuity while other channels change roles;
- supports the PanFlute feature;
- may provide restrained counterlines or held chord tones.

### Motif F — The Woodwind Question

**Voice:** PanFlute

A longer-breathed, more legato melodic idea contrasting with Motif A.

Functions:

- two-pattern haunting solo;
- should reference the main theme subtly through interval, contour, or transformed rhythm;
- creates emotional contrast without becoming stylistically detached from the rest of the tune.

---

## Channel Architecture

Motifs are **roles**, not simultaneous layers.

Typical main-theme allocation:

- Channel 1: RingPiano
- Channel 2: RingPiano answering figure or PingBells
- Channel 3: SoftBass
- Channel 4: drums

Typical PanFlute-section allocation:

- Channel 1: PanFlute
- Channel 2: Strings7
- Channel 3: SoftBass
- Channel 4: sparse drums

Channel duties may migrate between patterns as required. Arrangement decisions must remain genuinely four-channel rather than being designed as a larger arrangement and stripped down afterward.

---

## 3. Dependency Map & Version Log

### Dependency Map

```text
Clockwork Picnic
|
+-- Format / Compatibility
|   +-- ProTracker 2
|   +-- 4 channels
|   +-- 64-row patterns
|   +-- C-3..B-5 global note range
|   +-- PT-compatible effects only
|   +-- forward loops only
|
+-- Source Samples
|   +-- ST-01 archive
|   |   +-- RingPiano
|   |   +-- PanFlute
|   |   +-- SoftBass
|   |   +-- BassDrum3
|   |   +-- Snare1
|   |   +-- CloseHiHat
|   |   +-- Strings7
|   |   +-- PingBells
|   |
|   +-- ST-02 archive
|       +-- available as source material
|       +-- no currently selected instruments
|
+-- Auditioned Instrument State
|   +-- volumes
|   +-- finetunes
|   +-- Strings7 loop
|   +-- all 8 samples passed
|
+-- Musical Architecture
|   +-- title / thematic seed
|   +-- structural arc
|   +-- motifs A-F
|   +-- channel-role model
|   +-- pattern-reuse requirement
|
+-- Pattern Construction
|   +-- compiler row format
|   +-- first pattern inventory   [NEXT]
|   +-- opening/main-theme rows   [NEXT]
|   +-- PanFlute feature          [NEXT]
|   +-- reprise/coda
|   +-- final order list
|
+-- Testing
    +-- MilkyTracker
    +-- PikaOS
    +-- compiled .mod
    +-- by-ear verification
    +-- PT2 compatibility checks
```

### Version Log

#### Current Consolidated Bootstrap

- Project title locked as **Clockwork Picnic**.
- Baseline tempo locked at speed `06`, BPM `84`.
- Eight-sample instrument set selected and auditioned.
- Auditioned volumes accepted as authoritative.
- Pitched-sample finetunes established.
- `Strings7` forward-loop data established.
- Structural arc completed.
- Six-motif system completed.
- Four-channel role architecture established.
- Complete order list intentionally deferred until enough patterns exist for musically justified reuse.
- Project is ready to begin pattern construction.

This entry represents the current baseline only. Superseded sample choices, rejected settings, and earlier analytical guesses are intentionally omitted.

---

## 4. 'Golden' Code Blocks

### Project Metadata

```yaml
project:
  title: Clockwork Picnic
  status: bootstrap-complete
  tracker: MilkyTracker
  platform: Linux / PikaOS
  format: ProTracker MOD
  compatibility: ProTracker 2
  channels: 4
  rows_per_pattern: 64
  speed: 0x06
  bpm: 0x84
  target_runtime_seconds:
    min: 85
    max: 105
    strict: false
  looping_composition: false
  ending: deliberate-coda
```

### Approved Instruments

```yaml
instruments:
  - id: 1
    source: st01
    name: ST-01/RingPiano
    volume: 0x10
    finetune: 0x0  # 0 or +1

  - id: 2
    source: st01
    name: ST-01/PanFlute
    volume: 0x10
    finetune: 0xe  # -2 or -3
    # provisionally unlooped

  - id: 3
    source: st01
    name: ST-01/SoftBass
    volume: 0x40
    finetune: 0xf

  - id: 4
    source: st01
    name: ST-01/BassDrum3
    volume: 0x28

  - id: 5
    source: st01
    name: ST-01/Snare1
    volume: 0x2c

  - id: 6
    source: st01
    name: ST-01/CloseHiHat
    volume: 0x40

  - id: 7
    source: st01
    name: ST-01/Strings7
    volume: 0x20
    finetune: 0x2  # +2 to +4
    start: 0x00f0
    length: 0x25bc

  - id: 8
    source: st01
    name: ST-01/PingBells
    volume: 0x38
```

### Compatibility Rules

```text
4 channels only
64 rows per pattern
ProTracker-compatible effects only
No XM-only composition features
No notes below C-3
No notes above B-5
Low-pitched samples: restrict to octaves 4-5
High-pitched samples: restrict to octaves 3-4
Forward sample loops only
No ping-pong loops
Pattern reuse preferred
Composition must have a definite ending
No fade-out coda
Exact final runtime is not important
```

### Compiler Pattern-Row Format

```text
| RR | NNN II EEE | NNN II EEE | NNN II EEE | NNN II EEE |
```

Where:

- `RR` = row number;
- `NNN` = note;
- `II` = instrument slot;
- `EEE` = effect;
- each pattern must include a Markdown table header;
- effects must remain ProTracker-compatible;
- effects should be explained the first time they are introduced.

### Structural Logic

```yaml
structure:
  - section: winding_the_clock
    purpose: assemble the groove and introduce the mechanical identity
    motifs: [B, C, A-fragment, D-optional]

  - section: picnic_sets_off
    purpose: establish the full main theme
    motifs: [A, B, C, D-occasional]

  - section: clockwork_games
    purpose: recombine familiar material and make reuse audible
    motifs: [A-fragments, B, C, D, E-optional]

  - section: strange_little_wood
    purpose: two-pattern haunting PanFlute contrast
    motifs: [F, E, B-restrained, C-sparse]

  - section: back_to_the_picnic
    purpose: reprise established material with minimal new patterns
    motifs: [A, B, C, D]

  - section: clock_springs_loose
    purpose: deliberate non-fade coda
    motifs: [A-fragments, B-fragments, D, final-ensemble-gesture]
```

### Motif Roles

```yaml
motifs:
  A:
    name: The Picnic Tune
    primary_voice: RingPiano
    role: main melodic DNA

  B:
    name: The Clockwork Step
    voices: [SoftBass, BassDrum3]
    role: bass-kick pulse and reuse anchor

  C:
    name: The Cutlery Rattle
    voices: [CloseHiHat, Snare1]
    role: light asymmetric mechanical percussion

  D:
    name: The Glint
    primary_voice: PingBells
    role: sparse metallic answering accents

  E:
    name: The Long Grass
    primary_voice: Strings7
    role: sustained harmonic bed and transition support

  F:
    name: The Woodwind Question
    primary_voice: PanFlute
    role: two-pattern legato contrast derived subtly from main-theme DNA
```

---

## 5. Tested & Passing Status Confirmation

### Passed

- [x] Project title selected and locked.
- [x] Baseline speed and BPM selected.
- [x] Eight final sample identities selected.
- [x] All eight samples auditioned in a test pattern.
- [x] All eight samples passed audition.
- [x] Auditioned default volumes established.
- [x] Pitched-sample finetunes established.
- [x] `Strings7` forward-loop start and length established.
- [x] Structural arc completed.
- [x] Motif map completed.
- [x] Four-channel arrangement model established.
- [x] PT2 compatibility constraints retained.
- [x] Compiler row format retained.

### Not Yet Tested

- [ ] Actual composed pattern rows.
- [ ] Pattern-to-pattern transitions.
- [ ] Main-theme melodic contour in context.
- [ ] Two-pattern PanFlute solo in context.
- [ ] Final order list.
- [ ] Coda execution.
- [ ] Full compiled `.mod`.
- [ ] Final runtime.
- [ ] Final ProTracker compatibility pass.
- [ ] Final file size.

### Current Status

**Bootstrap stage: PASSING.**

The sample set and project architecture are accepted and stable enough to begin composition. No composed pattern data has yet been declared tested or passing.

---

## Tools Used

- **Testing OS:** PikaOS
- **Testing tracker:** MilkyTracker
- **Pattern entry:** not entered directly into MilkyTracker
- **Build path:** patterns are written in the compiler's Markdown-compatible row format and compiled into the final `.mod`

The compiler requires each row in this form:

```text
| RR | NNN II EEE | NNN II EEE | NNN II EEE | NNN II EEE |
```

Each pattern should therefore be emitted as a Markdown table with an appropriate header.
