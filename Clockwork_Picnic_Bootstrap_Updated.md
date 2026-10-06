# Clockwork Picnic — Project Bootstrap

**Project:** Clockwork Picnic  
**Status:** All patterns composed, auditioned, and passing; final order list pending  
**Tracker:** MilkyTracker  
**Testing platform:** Linux / PikaOS  
**Target format:** 4-channel ProTracker MOD  
**Compatibility target:** ProTracker 2  
**Pattern length:** 64 rows  
**Baseline speed:** `06`  
**Baseline BPM:** `84` hex (132 decimal)  
**Pattern inventory:** `00`–`0f`  
**Order list:** Pending finalization  

---

## 1. Current Goal & Next 3 Steps

### Current Goal

Assemble the audition-approved patterns into the final order list for **Clockwork Picnic**, compile the complete `.mod`, and verify that the full composition preserves the intended pacing, transitions, ProTracker 2 compatibility, and definite non-looping coda.

The composition is now musically complete at pattern level. The remaining work is arrangement and whole-track validation rather than further pattern writing.

### Next 3 Steps

1. **Finalize the order list.**  
   Reuse approved patterns deliberately, preserve the intended filter-state transitions, place the two-pattern PanFlute feature at the structural centre, and end with `0d, 0e, 0f`.

2. **Compile and audition the complete `.mod`.**  
   Check the entire track in order, with particular attention to repeated-pattern handoffs, filter state, the transition into and out of the PanFlute solo, and the final rallentando.

3. **Run final technical QA.**  
   Confirm order length, runtime, file size, sample metadata, forward-loop behavior, legal note range, supported effects, four-channel integrity, and non-looping playback.

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
   - accepted pattern rows;
   - pattern roles;
   - order-list intent;
   - note/rhythm/effect structure;
   - final sample identities;
   - tested status.

3. **The ST-01/ST-02 archives are sample-file sources only.**

### Locked Goal

Compose an original, highly polished early-1990s Amiga-game-style `.mod` titled **Clockwork Picnic**, using authentic ProTracker 2 constraints, ST-01 samples, four channels, compact pattern reuse, a human-feeling piano texture, a haunting two-pattern PanFlute feature, and a deliberate non-fade coda.

The intended character is:

- jaunty, cheerful, and suitable for a game title or attract screen;
- led by a convincingly voiced piano rather than a monophonic tracker lead;
- unmistakably early-1990s tracker music in construction and channel economy;
- contrasted by a filtered, haunting woodwind section;
- informed by the spirit of Tim Wright and David Whittaker without imitating a specific piece;
- allowed to exceed the original 85–105 second target where musical flow requires it.

### Core Compatibility Rules

```text
4 channels only
64 rows per pattern
ProTracker-compatible effects only
No XM-only composition features
No notes below C-3
No notes above B-5
Forward sample loops only
No ping-pong loops
Pattern reuse preferred
Composition must have a definite ending
No fade-out coda
Exact final runtime is secondary to musical flow
```

### Pattern Notation Rules

- Row numbers are **decimal**, from `00` through `63`.
- Entirely empty rows are omitted.
- Gaps in row numbering represent empty rows.
- No note: `---`
- No instrument: `--`
- No effect: `---`
- Actual instrument IDs and effect parameters remain hexadecimal.
- Each pattern uses this Markdown-compatible form:

```text
| RR | NNN II EEE | NNN II EEE | NNN II EEE | NNN II EEE |
```

### Locked Title & Tempo

- **Title:** Clockwork Picnic
- **Speed:** `06`
- **BPM:** `84` hex / 132 decimal
- **Final rallentando:** `F78`, `F70`, `F68`

The title remains the thematic seed:

- **clockwork** supplies interlocking figures, repeated pattern blocks, filter-state mechanics, and precise accents;
- **picnic** supplies warmth, cheerfulness, melodic openness, and a deliberately playful piano character.

### Approved Instrument Set

All eight samples have been auditioned and passed.

| ID | Sample | Role | Volume | Finetune | Loop |
|---:|---|---|---:|---:|---|
| `01` | `ST-01/RingPiano` | Principal piano voices | `10` | `0` | No |
| `02` | `ST-01/PanFlute` | Two-pattern woodwind solo | `10` | `e` | No |
| `03` | `ST-01/SoftBass` | Selective bass support | `40` | `f` | No |
| `04` | `ST-01/BassDrum3` | Kick | `28` | — | No |
| `05` | `ST-01/Snare1` | Snare | `2c` | — | No |
| `06` | `ST-01/CloseHiHat` | Closed hi-hat | `40` | — | No |
| `07` | `ST-01/Strings7` | Sustained harmonic bed | `20` | `2` | Yes |
| `08` | `ST-01/PingBells` | Beat-aligned metallic accents | `38` | — | No |

#### Finetune Notes

- `RingPiano`: base `0`; `+1` remains a by-ear alternative.
- `PanFlute`: base `e` (`-2`); `d` (`-3`) remains a by-ear alternative.
- `SoftBass`: `f` (`-1`).
- `Strings7`: base `2`; values `3`–`4` remain by-ear alternatives.

#### Strings7 Forward Loop

```yaml
start: 0x00f0
length: 0x25bc
type: forward
```

### Accepted Channel Architecture

A tracker channel represents one voice, not one entire hand.

#### Piano-led sections

| Channel | Role |
|---|---|
| CH1 | RingPiano top voice / melody |
| CH2 | RingPiano inner voice; yields occasionally to PingBells |
| CH3 | Consolidated percussion; temporarily becomes another RingPiano voice at important cadences |
| CH4 | RingPiano lowest voice / bass anchor |

This supports three- and four-note piano voicings, connected inner lines, broken-chord implications, rolled cadences, and a more plausible human performance.

#### PanFlute section

| Channel | Role |
|---|---|
| CH1 | PanFlute |
| CH2 | Strings7 |
| CH3 | SoftBass |
| CH4 | Sparse RingPiano accompaniment |

### Accepted Effect Vocabulary

| Effect | Meaning in this project |
|---|---|
| `E00` | Amiga low-pass filter on |
| `E01` | Amiga low-pass filter off |
| `ED1` | Delay note by one tick |
| `ED2` | Delay note by two ticks |
| `F78` | Set tempo to 120 BPM |
| `F70` | Set tempo to 112 BPM |
| `F68` | Set tempo to 104 BPM |

`ED1` and `ED2` are used sparingly to roll selected piano chords upward. They are not a constant humanization effect.

### Structural Arc and Accepted Pattern Roles

| Pattern | Role | Status |
|---|---|---|
| `00` | Winding the Clock | Passed |
| `01–04` | Main piano theme | Passed |
| `05–06` | Clockwork Games | Passed |
| `07` | Transition into the Strange Little Wood | Passed |
| `08–09` | PanFlute question and answer | Passed |
| `0a` | Transition back to the picnic | Passed |
| `0b–0c` | Richer piano reprise | Passed |
| `0d` | Reprise lift | Passed |
| `0e` | Coda setup / mechanism winds down | Passed |
| `0f` | Final flourish and rallentando | Passed |

### Filter-State Architecture

```text
00: filter on with E00
01–02: filter remains on
03: filter off with E01
04–06: filter remains off
07: filter on at row 32 with E00
08–09: filter remains on
0a: filter off at row 32 with E01
0b–0d: filter remains off
0e: filter on at row 32 with E00
0f: filter off at row 00 with E01
```

Any final order list must preserve sensible entry points into this state machine. Repeated `01–02` after `03` will intentionally sound brighter because the filter is already off.

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
|   +-- decimal row labels in compiler input
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
|       +-- retained as source material
|       +-- no selected instruments
|
+-- Auditioned Instrument State
|   +-- all 8 sample identities passed
|   +-- volumes locked
|   +-- finetunes locked
|   +-- Strings7 forward loop locked
|
+-- Accepted Musical Architecture
|   +-- three/four-voice piano model
|   +-- consolidated percussion
|   +-- beat-aligned bells
|   +-- filtered woodwind section
|   +-- final rallentando
|
+-- Accepted Patterns
|   +-- 00 intro
|   +-- 01-04 main theme
|   +-- 05-06 games
|   +-- 07 transition
|   +-- 08-09 solo
|   +-- 0a return transition
|   +-- 0b-0c reprise
|   +-- 0d lift
|   +-- 0e-0f coda
|
+-- Remaining Assembly
|   +-- final order list          [NEXT]
|   +-- full MOD compilation      [NEXT]
|   +-- whole-track audition      [NEXT]
|   +-- runtime / size / PT2 QA   [NEXT]
|
+-- Testing
    +-- PikaOS
    +-- MilkyTracker
    +-- custom MOD compiler
```

### Version Log

#### Current Consolidated Bootstrap

- Title locked as **Clockwork Picnic**.
- Baseline speed and tempo locked at `06` / `84`.
- Eight-sample ST-01 instrument set auditioned and accepted.
- Instrument volumes, finetunes, and Strings7 loop settings accepted.
- Piano architecture revised from one channel per hand to three/four independent piano voices.
- Compiler notation locked to decimal row numbers with omitted empty rows.
- `E00`, `E01`, `ED1`, `ED2`, and final `Fxx` effects accepted by audition.
- PingBell timing corrected to the established four-row pulse.
- Patterns `00`–`0f` composed and auditioned.
- Every pattern and every designed transition block has passed.
- Final order list remains the only outstanding musical assembly decision.

Superseded sample choices, rejected pattern drafts, and abandoned channel architectures are intentionally omitted.

---

## 4. Golden Code Blocks

### Project Metadata

```yaml
project:
  title: Clockwork Picnic
  status: patterns-complete-order-pending
  tracker: MilkyTracker
  platform: Linux / PikaOS
  format: ProTracker MOD
  compatibility: ProTracker 2
  channels: 4
  rows_per_pattern: 64
  row_number_base: decimal
  omit_empty_rows: true
  speed: 0x06
  bpm: 0x84
  looping_composition: false
  ending: deliberate-coda
  highest_pattern: 0x0f
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
    loop_type: forward

  - id: 8
    source: st01
    name: ST-01/PingBells
    volume: 0x38
```

### Pattern 00 — Winding the Clock

| RR | CH1 | CH2 | CH3 | CH4 |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | E-3 01 E00 | G-3 01 ED1 | C-4 01 ED2 | C-3 01 --- |
| 04 | G-3 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 08 | E-3 01 --- | C-3 01 --- | --- -- --- | G-3 01 --- |
| 12 | C-4 01 --- | E-3 01 --- | G-3 01 --- | --- -- --- |
| 16 | C-3 01 --- | E-3 01 ED1 | C-4 01 ED2 | A-3 01 --- |
| 20 | A-3 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 24 | C-3 01 --- | G-3 01 ED1 | C-4 01 ED2 | E-3 01 --- |
| 28 | G-3 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 32 | A-3 01 --- | C-3 01 --- | --- -- --- | F-3 01 --- |
| 36 | C-4 01 --- | A-3 01 --- | C-4 06 --- | --- -- --- |
| 40 | A-3 01 --- | F-3 01 --- | C-4 06 --- | C-4 01 --- |
| 44 | G-3 01 --- | E-3 01 --- | C-4 06 --- | --- -- --- |
| 48 | F-3 01 --- | B-3 01 --- | C-4 04 --- | G-3 01 --- |
| 52 | A-3 01 --- | C-4 01 --- | C-4 06 --- | --- -- --- |
| 56 | B-3 01 --- | G-3 01 --- | C-4 05 --- | D-4 01 --- |
| 58 | G-3 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 60 | A-3 01 --- | C-4 01 --- | C-4 04 --- | G-3 01 --- |
| 62 | B-3 01 --- | D-4 01 --- | C-4 06 --- | --- -- --- |

### Pattern 01 — The Picnic Tune, Phrase A

| RR | CH1 | CH2 | CH3 | CH4 |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | C-4 01 ED2 | E-3 01 ED1 | C-4 04 --- | C-3 01 --- |
| 04 | --- -- --- | --- -- --- | C-4 06 --- | --- -- --- |
| 06 | E-4 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 08 | --- -- --- | B-3 01 --- | C-4 05 --- | G-3 01 --- |
| 12 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 16 | E-4 01 --- | C-4 01 --- | C-4 04 --- | E-3 01 --- |
| 20 | --- -- --- | --- -- --- | C-4 06 --- | --- -- --- |
| 22 | D-4 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 24 | --- -- --- | B-3 01 --- | C-4 05 --- | G-3 01 --- |
| 28 | C-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 32 | E-4 01 --- | C-4 01 --- | C-4 04 --- | A-3 01 --- |
| 36 | --- -- --- | --- -- --- | C-4 06 --- | --- -- --- |
| 40 | A-4 01 --- | B-3 01 --- | C-4 05 --- | E-3 01 --- |
| 44 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 48 | A-3 01 ED2 | F-3 01 ED1 | C-4 04 --- | C-3 01 --- |
| 52 | C-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 56 | A-3 01 --- | F-3 01 --- | C-4 05 --- | C-3 01 --- |
| 58 | G-3 01 --- | E-3 01 --- | --- -- --- | C-3 01 --- |
| 60 | B-3 01 --- | G-3 01 --- | C-4 04 --- | D-3 01 --- |

### Pattern 02 — The Picnic Tune, Phrase B

| RR | CH1 | CH2 | CH3 | CH4 |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | E-4 01 ED2 | G-3 01 ED1 | C-4 01 --- | C-3 01 --- |
| 04 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 08 | E-4 01 --- | C-4 01 --- | C-4 05 --- | G-3 01 --- |
| 12 | C-4 01 --- | G-3 01 --- | C-4 06 --- | --- -- --- |
| 16 | D-4 01 --- | A-3 01 --- | C-4 04 --- | F-3 01 --- |
| 20 | F-4 01 --- | C-4 01 --- | C-4 06 --- | --- -- --- |
| 24 | E-4 01 --- | G-3 01 --- | C-4 05 --- | C-3 01 --- |
| 28 | C-4 01 --- | E-3 01 --- | C-4 06 --- | --- -- --- |
| 32 | D-4 01 --- | B-3 01 --- | C-4 04 --- | G-3 01 --- |
| 36 | G-4 01 --- | D-4 01 --- | C-4 06 --- | --- -- --- |
| 40 | F-4 01 --- | B-3 01 --- | C-4 05 --- | D-3 01 --- |
| 44 | D-4 01 --- | G-3 01 --- | C-4 06 --- | --- -- --- |
| 48 | E-4 01 --- | G-3 01 --- | C-4 04 --- | C-3 01 --- |
| 52 | G-4 01 --- | C-4 01 --- | C-4 06 --- | --- -- --- |
| 56 | E-4 01 --- | C-4 01 --- | C-4 05 --- | E-3 01 --- |
| 58 | D-4 01 --- | B-3 01 --- | --- -- --- | G-3 01 --- |
| 60 | C-4 01 ED2 | G-3 01 ED1 | E-3 01 --- | C-3 01 --- |

### Pattern 03 — Main Theme Development A

| RR | CH1 | CH2 | CH3 | CH4 |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | A-3 01 E01 | F-3 01 --- | C-4 04 --- | C-3 01 --- |
| 04 | C-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 08 | F-4 01 --- | C-4 01 --- | C-4 05 --- | F-3 01 --- |
| 12 | E-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 16 | D-4 01 --- | F-3 01 --- | C-4 04 --- | D-3 01 --- |
| 20 | F-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 24 | A-4 01 --- | F-3 01 --- | C-4 05 --- | D-3 01 --- |
| 28 | F-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 32 | G-4 01 --- | B-3 01 --- | C-4 04 --- | G-3 01 --- |
| 36 | D-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 40 | B-3 01 --- | G-3 01 --- | C-4 05 --- | D-3 01 --- |
| 44 | D-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 48 | E-4 01 --- | G-3 01 --- | C-4 04 --- | C-3 01 --- |
| 52 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 56 | E-4 01 --- | C-4 01 --- | C-4 05 --- | G-3 01 --- |
| 60 | D-4 01 --- | B-3 01 --- | C-4 04 --- | G-3 01 --- |

### Pattern 04 — Main Theme Development B

| RR | CH1 | CH2 | CH3 | CH4 |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | C-4 01 ED2 | A-3 01 ED1 | C-4 04 --- | E-3 01 --- |
| 04 | E-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 08 | A-4 01 --- | C-4 01 --- | C-4 05 --- | A-3 01 --- |
| 12 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 16 | F-4 01 --- | A-3 01 --- | C-4 04 --- | F-3 01 --- |
| 20 | A-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 24 | C-4 01 --- | F-3 01 --- | C-4 05 --- | C-3 01 --- |
| 28 | E-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 32 | D-4 01 --- | B-3 01 --- | C-4 04 --- | G-3 01 --- |
| 36 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 40 | F-4 01 --- | B-3 01 --- | C-4 05 --- | D-3 01 --- |
| 44 | D-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 48 | E-4 01 --- | G-3 01 --- | C-4 04 --- | C-3 01 --- |
| 52 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 56 | C-4 01 --- | G-3 01 --- | C-4 05 --- | E-3 01 --- |
| 58 | B-3 01 --- | G-3 01 --- | --- -- --- | D-3 01 --- |
| 60 | C-4 01 ED2 | G-3 01 ED1 | E-3 01 --- | C-3 01 --- |

### Pattern 05 — Clockwork Games A

| RR | CH1 | CH2 | CH3 | CH4 |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | E-4 01 ED2 | G-3 01 ED1 | C-4 04 --- | C-3 01 --- |
| 04 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 08 | E-4 01 --- | B-3 01 --- | C-4 05 --- | G-3 01 --- |
| 12 | D-4 01 --- | G-4 08 --- | C-4 06 --- | --- -- --- |
| 16 | E-4 01 --- | C-4 01 --- | C-4 04 --- | A-3 01 --- |
| 20 | A-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 24 | G-4 01 --- | B-3 01 --- | C-4 05 --- | E-3 01 --- |
| 28 | E-4 01 --- | B-4 08 --- | C-4 06 --- | --- -- --- |
| 32 | F-4 01 ED2 | C-4 01 ED1 | C-4 04 --- | F-3 01 --- |
| 36 | A-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 40 | F-4 01 --- | A-3 01 --- | C-4 05 --- | D-3 01 --- |
| 44 | D-4 01 --- | A-4 08 --- | C-4 06 --- | --- -- --- |
| 48 | G-4 01 --- | B-3 01 --- | C-4 04 --- | G-3 01 --- |
| 52 | D-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 56 | B-3 01 --- | G-3 01 --- | C-4 05 --- | D-3 01 --- |
| 60 | D-4 01 --- | B-3 01 --- | C-4 06 --- | G-3 01 --- |

### Pattern 06 — Clockwork Games B

| RR | CH1 | CH2 | CH3 | CH4 |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | C-4 01 ED2 | G-3 01 ED1 | C-4 04 --- | C-3 01 --- |
| 04 | E-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 08 | A-4 01 --- | C-4 01 --- | C-4 05 --- | A-3 01 --- |
| 12 | G-4 01 --- | B-4 08 --- | C-4 06 --- | --- -- --- |
| 16 | E-4 01 --- | G-3 01 --- | C-4 04 --- | E-3 01 --- |
| 20 | C-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 24 | F-4 01 --- | A-3 01 --- | C-4 05 --- | F-3 01 --- |
| 28 | E-4 01 --- | A-4 08 --- | C-4 06 --- | --- -- --- |
| 32 | D-4 01 --- | A-3 01 --- | C-4 04 --- | D-3 01 --- |
| 36 | F-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 40 | G-4 01 --- | B-3 01 --- | C-4 05 --- | G-3 01 --- |
| 44 | D-4 01 --- | B-4 08 --- | C-4 06 --- | --- -- --- |
| 48 | E-4 01 --- | G-3 01 --- | C-4 04 --- | C-3 01 --- |
| 52 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 56 | D-4 01 --- | B-3 01 --- | C-4 05 --- | G-3 01 --- |
| 58 | B-3 01 --- | G-3 01 --- | --- -- --- | D-3 01 --- |
| 60 | C-4 01 ED2 | E-3 01 ED1 | G-3 01 --- | C-3 01 --- |

### Pattern 07 — Into the Strange Little Wood

| RR | CH1 | CH2 | CH3 | CH4 |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | E-4 01 --- | G-3 01 --- | C-4 04 --- | C-3 01 --- |
| 04 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 08 | E-4 01 --- | C-4 01 --- | C-4 05 --- | G-3 01 --- |
| 12 | C-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 16 | E-4 01 --- | C-4 01 --- | C-4 04 --- | A-3 01 --- |
| 20 | C-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 24 | A-3 01 --- | C-4 01 --- | C-4 05 --- | E-3 01 --- |
| 28 | C-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 32 | F-4 01 --- | A-3 07 E00 | D-4 03 --- | D-3 01 --- |
| 40 | E-4 01 --- | F-3 07 --- | A-4 03 --- | A-3 01 --- |
| 48 | D-4 01 --- | B-3 07 --- | E-4 03 --- | E-3 01 --- |
| 56 | B-3 01 --- | G#3 07 --- | B-4 03 --- | --- -- --- |
| 60 | G#3 01 --- | --- -- --- | --- -- --- | --- -- --- |

### Pattern 08 — The Woodwind Question

| RR | CH1 | CH2 | CH3 | CH4 |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | A-3 02 --- | C-4 07 --- | A-4 03 --- | E-3 01 --- |
| 08 | C-4 02 --- | --- -- --- | --- -- --- | A-3 01 --- |
| 16 | E-4 02 --- | A-3 07 --- | F-4 03 --- | F-3 01 --- |
| 24 | D-4 02 --- | --- -- --- | --- -- --- | C-4 01 --- |
| 32 | F-4 02 --- | A-3 07 --- | D-4 03 --- | D-3 01 --- |
| 40 | E-4 02 --- | --- -- --- | --- -- --- | A-3 01 --- |
| 48 | D-4 02 --- | B-3 07 --- | E-4 03 --- | E-3 01 --- |
| 56 | B-3 02 --- | G#3 07 --- | B-4 03 --- | --- -- --- |
| 60 | G#3 02 --- | --- -- --- | --- -- --- | --- -- --- |

### Pattern 09 — The Woodwind Answer

| RR | CH1 | CH2 | CH3 | CH4 |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | A-3 02 --- | C-4 07 --- | A-4 03 --- | E-3 01 --- |
| 08 | C-4 02 --- | --- -- --- | --- -- --- | A-3 01 --- |
| 16 | E-4 02 --- | G-3 07 --- | C-5 03 --- | C-4 01 --- |
| 24 | G-4 02 --- | --- -- --- | --- -- --- | G-3 01 --- |
| 32 | A-4 02 --- | C-4 07 --- | F-4 03 --- | F-3 01 --- |
| 40 | G-4 02 --- | --- -- --- | --- -- --- | C-4 01 --- |
| 48 | F-4 02 --- | A-3 07 --- | D-4 03 --- | D-3 01 --- |
| 52 | E-4 02 --- | G#3 07 --- | B-4 03 --- | E-3 01 --- |
| 56 | B-3 02 --- | D-4 07 --- | E-4 03 --- | --- -- --- |
| 60 | A-3 02 --- | C-4 07 --- | A-4 03 --- | E-3 01 --- |

### Pattern 0a — Back to the Picnic

| RR | CH1 | CH2 | CH3 | CH4 |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | E-4 02 --- | C-4 07 --- | A-4 03 --- | A-3 01 --- |
| 08 | C-4 02 --- | --- -- --- | --- -- --- | E-3 01 --- |
| 16 | A-3 02 --- | C-4 07 --- | F-4 03 --- | F-3 01 --- |
| 24 | D-4 02 --- | B-3 07 --- | G-4 03 --- | G-3 01 --- |
| 28 | B-3 02 --- | --- -- --- | --- -- --- | --- -- --- |
| 32 | E-4 01 ED2 | G-3 01 ED1 | C-4 06 --- | C-3 01 E01 |
| 36 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 40 | E-4 01 --- | C-4 01 --- | C-4 06 --- | G-3 01 --- |
| 44 | C-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 48 | D-4 01 --- | B-3 01 --- | C-4 04 --- | G-3 01 --- |
| 52 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 56 | F-4 01 --- | B-3 01 --- | C-4 05 --- | G-3 01 --- |
| 60 | D-4 01 --- | B-3 01 --- | C-4 04 --- | G-3 01 --- |
| 62 | --- -- --- | --- -- --- | C-4 06 --- | --- -- --- |

### Pattern 0b — Piano Reprise A

| RR | CH1 | CH2 | CH3 | CH4 |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | C-4 01 ED2 | G-3 01 ED1 | E-3 01 --- | C-3 01 --- |
| 04 | --- -- --- | A-3 01 --- | C-4 06 --- | --- -- --- |
| 06 | E-4 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 08 | --- -- --- | B-3 01 --- | C-4 05 --- | G-3 01 --- |
| 12 | G-4 01 --- | C-4 01 --- | C-4 06 --- | --- -- --- |
| 16 | E-4 01 --- | C-4 01 --- | C-4 04 --- | E-3 01 --- |
| 20 | --- -- --- | B-3 01 --- | C-4 06 --- | --- -- --- |
| 22 | D-4 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 24 | --- -- --- | B-3 01 --- | C-4 05 --- | G-3 01 --- |
| 28 | C-4 01 --- | G-3 01 --- | C-4 06 --- | --- -- --- |
| 32 | E-4 01 --- | C-4 01 --- | C-4 04 --- | A-3 01 --- |
| 36 | --- -- --- | B-3 01 --- | C-4 06 --- | --- -- --- |
| 40 | A-4 01 --- | C-4 01 --- | C-4 05 --- | E-3 01 --- |
| 44 | G-4 01 --- | B-3 01 --- | C-4 06 --- | --- -- --- |
| 48 | A-3 01 ED2 | F-3 01 ED1 | C-4 04 --- | C-3 01 --- |
| 52 | C-4 01 --- | A-3 01 --- | F-3 01 --- | C-3 01 --- |
| 56 | A-3 01 --- | F-3 01 --- | C-4 05 --- | C-3 01 --- |
| 58 | G-3 01 --- | E-3 01 --- | --- -- --- | C-3 01 --- |
| 60 | B-3 01 --- | G-3 01 --- | C-4 04 --- | D-3 01 --- |

### Pattern 0c — Piano Reprise B

| RR | CH1 | CH2 | CH3 | CH4 |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | E-4 01 ED2 | G-3 01 ED1 | C-4 01 --- | C-3 01 --- |
| 04 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 08 | E-4 01 --- | C-4 01 --- | C-4 05 --- | G-3 01 --- |
| 12 | C-4 01 --- | G-3 01 --- | C-4 06 --- | --- -- --- |
| 16 | D-4 01 --- | A-3 01 --- | C-4 04 --- | F-3 01 --- |
| 20 | F-4 01 --- | C-4 01 --- | C-4 06 --- | --- -- --- |
| 24 | E-4 01 --- | G-3 01 --- | C-4 05 --- | C-3 01 --- |
| 28 | C-4 01 --- | E-3 01 --- | C-4 06 --- | --- -- --- |
| 32 | D-4 01 --- | B-3 01 --- | C-4 04 --- | G-3 01 --- |
| 36 | G-4 01 --- | D-4 01 --- | C-4 06 --- | --- -- --- |
| 40 | F-4 01 --- | B-3 01 --- | C-4 05 --- | D-3 01 --- |
| 44 | D-4 01 --- | G-3 01 --- | C-4 06 --- | --- -- --- |
| 48 | E-4 01 --- | G-3 01 --- | C-4 04 --- | C-3 01 --- |
| 52 | G-4 01 --- | C-4 01 --- | C-4 06 --- | --- -- --- |
| 56 | E-4 01 --- | C-4 01 --- | C-4 05 --- | E-3 01 --- |
| 58 | D-4 01 --- | B-3 01 --- | --- -- --- | G-3 01 --- |
| 60 | C-4 01 ED2 | G-3 01 ED1 | E-3 01 --- | C-3 01 --- |

### Pattern 0d — Piano Reprise Lift

| RR | CH1 | CH2 | CH3 | CH4 |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | G-4 01 --- | E-4 01 --- | C-4 04 --- | C-3 01 --- |
| 04 | E-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 08 | C-4 01 --- | G-3 01 --- | C-4 05 --- | E-3 01 --- |
| 12 | D-4 01 --- | G-4 08 --- | C-4 06 --- | --- -- --- |
| 16 | A-4 01 --- | C-4 01 --- | C-4 04 --- | F-3 01 --- |
| 20 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 24 | F-4 01 --- | A-3 01 --- | C-4 05 --- | D-3 01 --- |
| 28 | D-4 01 --- | A-4 08 --- | C-4 06 --- | --- -- --- |
| 32 | E-4 01 --- | C-4 01 --- | C-4 04 --- | A-3 01 --- |
| 36 | C-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 40 | F-4 01 --- | A-3 01 --- | C-4 05 --- | F-3 01 --- |
| 44 | E-4 01 --- | G-4 08 --- | C-4 06 --- | --- -- --- |
| 48 | D-4 01 --- | B-3 01 --- | C-4 04 --- | G-3 01 --- |
| 52 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 56 | F-4 01 --- | B-3 01 --- | C-4 05 --- | D-3 01 --- |
| 60 | D-4 01 --- | B-3 01 --- | F-3 01 --- | G-3 01 --- |

### Pattern 0e — The Clockwork Winds Down

| RR | CH1 | CH2 | CH3 | CH4 |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | C-4 01 ED2 | G-3 01 ED1 | C-4 04 --- | C-3 01 --- |
| 04 | E-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 08 | G-4 01 --- | C-4 01 --- | C-4 05 --- | E-3 01 --- |
| 12 | E-4 01 --- | G-4 08 --- | C-4 06 --- | --- -- --- |
| 16 | A-3 01 --- | F-3 01 --- | C-4 04 --- | C-3 01 --- |
| 20 | C-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 24 | D-4 01 --- | B-3 01 --- | C-4 05 --- | G-3 01 --- |
| 28 | B-3 01 --- | G-4 08 --- | C-4 06 --- | D-4 01 --- |
| 32 | E-4 01 E00 | C-4 07 --- | C-4 03 --- | C-3 01 --- |
| 40 | C-4 01 --- | A-3 07 --- | F-4 03 --- | F-3 01 --- |
| 48 | B-3 01 --- | D-4 07 --- | G-4 03 --- | G-3 01 --- |
| 56 | F-4 01 --- | B-3 07 --- | G-4 03 --- | D-3 01 --- |
| 60 | D-4 01 --- | B-3 07 --- | G-4 03 --- | G-3 01 --- |

### Pattern 0f — The Clock Springs Loose

| RR | CH1 | CH2 | CH3 | CH4 |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | E-4 01 E01 | G-3 01 --- | C-4 04 --- | C-3 01 --- |
| 04 | G-4 01 --- | C-4 01 --- | C-4 06 --- | --- -- --- |
| 08 | C-5 01 --- | E-4 01 --- | C-4 05 --- | E-3 01 --- |
| 12 | G-4 01 --- | E-4 08 --- | C-4 06 --- | G-3 01 --- |
| 16 | A-4 01 --- | C-4 01 --- | C-4 04 --- | F-3 01 --- |
| 20 | F-4 01 --- | A-3 01 --- | C-4 06 --- | C-4 01 --- |
| 24 | D-4 01 --- | A-3 01 --- | C-4 05 --- | D-3 01 --- |
| 28 | G-4 01 --- | B-4 08 --- | C-4 06 --- | G-3 01 --- |
| 32 | E-4 01 --- | C-4 01 --- | G-3 01 --- | C-3 01 --- |
| 36 | G-4 01 --- | E-4 01 --- | C-4 01 --- | E-3 01 --- |
| 40 | A-4 01 --- | F-4 01 --- | C-4 01 --- | F-3 01 --- |
| 44 | E-4 01 --- | C-4 01 --- | G-3 01 --- | C-3 01 --- |
| 46 | F-4 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 48 | G-4 01 F78 | B-3 01 --- | F-3 01 --- | G-3 01 --- |
| 50 | A-4 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 52 | C-5 01 F70 | D-4 01 --- | G-3 01 --- | D-3 01 --- |
| 54 | B-4 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 56 | C-5 01 ED2 | E-4 01 ED1 | G-3 01 --- | C-3 01 F68 |

---

## 5. Tested & Passing Status Confirmation

### Passed

- [x] Project title and thematic identity.
- [x] Baseline speed and BPM.
- [x] Eight final sample identities.
- [x] Auditioned sample volumes.
- [x] Pitched-sample finetunes.
- [x] Strings7 forward-loop start and length.
- [x] Decimal compiler row notation.
- [x] Omission of entirely empty rows.
- [x] Three/four-voice piano architecture.
- [x] Consolidated percussion architecture.
- [x] Beat-aligned PingBell timing.
- [x] Filter-on and filter-off transitions.
- [x] Rolled piano voicings using `ED1` and `ED2`.
- [x] Main piano theme, Patterns `01–04`.
- [x] Clockwork Games, Patterns `05–06`.
- [x] Transition into the woodwind section, Pattern `07`.
- [x] Two-pattern PanFlute solo, Patterns `08–09`.
- [x] Transition back, Pattern `0a`.
- [x] Piano reprise, Patterns `0b–0c`.
- [x] Reprise lift, Pattern `0d`.
- [x] Coda setup, Pattern `0e`.
- [x] Final flourish and rallentando, Pattern `0f`.
- [x] All individual pattern auditions.
- [x] All requested paired and sectional auditions.
- [x] Definite non-fade ending at pattern level.

### Not Yet Tested

- [ ] Final order list.
- [ ] Complete order-list audition from beginning to end.
- [ ] Full compiled `.mod`.
- [ ] Exact final runtime.
- [ ] Final file size.
- [ ] Full ProTracker 2 compatibility pass on the assembled module.
- [ ] Playback-stop behavior after the final order entry.

### Current Status

**Pattern-composition stage: PASSING.**

All patterns `00`–`0f` are authoritative and audition-approved. The project is ready for final order-list assembly.

---

## Tools Used

- **Testing OS:** PikaOS
- **Testing tracker:** MilkyTracker
- **Pattern entry:** custom Markdown-compatible pattern compiler
- **Build path:** accepted pattern tables compile into the final `.mod`

