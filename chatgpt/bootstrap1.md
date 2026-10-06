# Clockwork Picnic - Final Project Bootstrap

**Project:** Clockwork Picnic  
**Status:** Complete; final build compiled, fully auditioned, and passing  
**Tracker:** MilkyTracker  
**Testing platform:** Linux / PikaOS  
**Target format:** 4-channel ProTracker MOD  
**Compatibility target:** ProTracker 2  
**Pattern length:** 64 rows  
**Baseline speed:** `06`  
**Baseline BPM:** `84` hex (132 decimal)  
**Pattern inventory:** `00`-`0f`  
**Order length:** `16` hex (22 positions)  
**Final order position:** `15` hex  
**Exact runtime:** `02:26` (146 seconds)  
**Final file size:** `59.07 kB`  
**Final audition:** Passed on multiple sound systems  

---

## 1. Current Goal & Next 3 Steps

### Current Goal

Preserve the final authoritative state of **Clockwork Picnic** for release, reconstruction, and future reference.

The musical work is complete. All patterns have passed, the final order list has compiled successfully, and the complete module has been auditioned on multiple sound systems. No composition, arrangement, or mix changes remain outstanding.

### Next 3 Steps

These are post-completion archival steps rather than unfinished production work:

1. **Freeze the final build and source.**  
   Keep the accepted `.mod`, compiler input, this bootstrap, and the exact ST-01 sample files together as one immutable release set.

2. **Record checksums and backups.**  
   Generate checksums for the final `.mod`, bootstrap, compiler source, and sample inputs, then retain at least two independent copies.

3. **Tag the release.**  
   Assign a final version or release tag and distribute the compiled module without further musical edits unless a genuine defect is discovered. The traditional post-release urge to adjust one harmless note is not, regrettably, a genuine defect.

---

## 2. State of Play

### Source-of-Truth Hierarchy

Use this hierarchy whenever records disagree:

1. **The final compiled and auditioned `.mod` is authoritative** for:
   - actual playback;
   - final order-list behavior;
   - audible filter state;
   - exact runtime;
   - final file size;
   - the accepted complete-track result.

2. **The accepted compiler source and this bootstrap are authoritative** for:
   - pattern rows;
   - project architecture;
   - instrument assignments;
   - sample volumes and finetunes;
   - loop settings;
   - order-list structure;
   - effect usage;
   - tested status.

3. **The ST-01/ST-02 archives are sample-file sources only.**

### Completed Outcome

**Clockwork Picnic** is an original early-1990s Amiga-game-style `.mod` built under ProTracker 2 constraints with:

- four channels;
- authentic ST-01 samples;
- a human-feeling, three- and four-voice piano texture;
- compact but audible pattern reuse;
- a filtered two-pattern PanFlute feature;
- sparse, beat-aligned PingBell accents;
- deliberate low-pass-filter transitions;
- a composed final flourish and rallentando;
- a definite ending with no fade and no compositional loop.

The finished track is jaunty, cheerful, and suitable for a game title or attract screen, with the PanFlute episode supplying the intended haunting contrast.

### Final Build Metrics

| Metric | Final value | Status |
|---|---:|---|
| Runtime | `02:26` / 146 seconds | Accepted |
| File size | `59.07 kB` | Accepted |
| Pattern count | `10` hex / 16 patterns | Complete |
| Order length | `16` hex / 22 positions | Complete |
| Final order position | `15` hex | Locked |
| Final pattern | `0f` | Locked |
| Full-build audition | Multiple sound systems | Passed |

The original 85-105 second runtime preference and optional sub-40 kB bonus were soft targets. The final build exceeds both, with the accepted priorities remaining musical flow, convincing piano writing, ProTracker compatibility, and the deliberate coda.

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
```

### Pattern Notation Rules

- Row numbers are **decimal**, from `00` through `63`.
- Entirely empty rows are omitted.
- Gaps in row numbering represent empty rows.
- No note: `---`
- No instrument: `--`
- No effect: `---`
- Instrument IDs and effect parameters remain hexadecimal.
- Each pattern uses this Markdown-compatible form:

```text
| RR | NNN II EEE | NNN II EEE | NNN II EEE | NNN II EEE |
```

### Locked Title, Tempo, and Ending

- **Title:** Clockwork Picnic
- **Speed:** `06`
- **Baseline BPM:** `84` hex / 132 decimal
- **Final rallentando:** `F78`, `F70`, `F68`
- **Final chord:** rolled C major at Pattern `0f`, row `56`
- **Ending:** natural RingPiano decay; no jump, restart, or fade

The title remains the thematic seed:

- **clockwork** supplies interlocking figures, repeated pattern blocks, filter-state mechanics, and precise accents;
- **picnic** supplies warmth, cheerfulness, melodic openness, and playful piano writing.

### Approved Instrument Set

All eight samples were auditioned and passed.

| ID | Sample | Role | Volume | Finetune | Loop |
|---:|---|---|---:|---:|---|
| `01` | `ST-01/RingPiano` | Principal piano voices | `10` | `0` | No |
| `02` | `ST-01/PanFlute` | Two-pattern woodwind solo | `10` | `e` | No |
| `03` | `ST-01/SoftBass` | Selective bass support | `40` | `f` | No |
| `04` | `ST-01/BassDrum3` | Kick | `28` | - | No |
| `05` | `ST-01/Snare1` | Snare | `2c` | - | No |
| `06` | `ST-01/CloseHiHat` | Closed hi-hat | `40` | - | No |
| `07` | `ST-01/Strings7` | Sustained harmonic bed | `20` | `2` | Yes |
| `08` | `ST-01/PingBells` | Beat-aligned metallic accents | `38` | - | No |

#### Finetune Notes

- `RingPiano`: accepted at `0`; `+1` remains a historical/by-ear alternative, not the final setting.
- `PanFlute`: accepted at `e` (`-2`); `d` (`-3`) remains an alternative, not the final setting.
- `SoftBass`: accepted at `f` (`-1`).
- `Strings7`: accepted at `2`; values `3`-`4` remain alternatives, not final settings.

#### Strings7 Forward Loop

```yaml
start: 0x00f0
length: 0x25bc
type: forward
```

### Accepted Channel Architecture

A tracker channel represents one voice, not an entire pianist's hand.

#### Piano-led sections

| Channel | Role |
|---|---|
| CH1 | RingPiano top voice / melody |
| CH2 | RingPiano inner voice; yields occasionally to PingBells |
| CH3 | Consolidated percussion; temporarily becomes another RingPiano voice at important cadences |
| CH4 | RingPiano lowest voice / bass anchor |

This architecture supports three- and four-note piano voicings, connected inner lines, broken-chord implications, rolled cadences, and a plausible human performance.

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

`ED1` and `ED2` are used sparingly to roll selected piano chords upward. They are not a constant humanization device.

### Final Pattern Roles

| Pattern | Role | Status |
|---|---|---|
| `00` | Winding the Clock | Passed |
| `01`-`04` | Main piano theme | Passed |
| `05`-`06` | Clockwork Games | Passed |
| `07` | Transition into the Strange Little Wood | Passed |
| `08`-`09` | PanFlute question and answer | Passed |
| `0a` | Transition back to the picnic | Passed |
| `0b`-`0c` | Richer piano reprise | Passed |
| `0d` | Reprise lift | Passed |
| `0e` | Coda setup / mechanism winds down | Passed |
| `0f` | Final flourish and rallentando | Passed |

### Final Order List

```text
00, 01, 02, 03, 04, 01, 02, 05, 06, 03, 04,
07, 08, 09, 0a, 0b, 0c, 05, 06, 0d, 0e, 0f
```

| Order position | Pattern | Function |
|---:|---:|---|
| `00` | `00` | Winding the Clock |
| `01` | `01` | Main theme A |
| `02` | `02` | Main theme B |
| `03` | `03` | Main development A |
| `04` | `04` | Main development B |
| `05` | `01` | Brighter core-theme restatement |
| `06` | `02` | Brighter core-theme answer |
| `07` | `05` | Clockwork Games A |
| `08` | `06` | Clockwork Games B |
| `09` | `03` | Development recall A |
| `0a` | `04` | Development recall B |
| `0b` | `07` | Transition into the woodwind section |
| `0c` | `08` | PanFlute question |
| `0d` | `09` | PanFlute answer |
| `0e` | `0a` | Transition back to piano |
| `0f` | `0b` | Piano reprise A |
| `10` | `0c` | Piano reprise B |
| `11` | `05` | Clockwork Games return A |
| `12` | `06` | Clockwork Games return B |
| `13` | `0d` | Reprise lift |
| `14` | `0e` | Coda setup |
| `15` | `0f` | Final flourish and ending |

### Filter-State Architecture

```text
Order 00 / Pattern 00: filter on with E00
Patterns 01-02: filter remains on
Pattern 03: filter off with E01
Patterns 04, 01, 02, 05, 06: filter remains off
Repeated Pattern 03: E01 safely reasserts filter off
Pattern 07, row 32: filter on with E00
Patterns 08-09: filter remains on
Pattern 0a, row 32: filter off with E01
Patterns 0b-0d: filter remains off
Pattern 0e, row 32: filter on with E00
Pattern 0f, row 00: filter off with E01
```

The repeated `01`-`02` pair is intentionally brighter on its second appearance because the filter has already been opened by Pattern `03`.

---

## 3. Dependency Map & Version Log

### Dependency Map

```text
Clockwork Picnic
|
+-- Format / Compatibility                         [COMPLETE]
|   +-- ProTracker 2 target
|   +-- 4 channels
|   +-- 64-row patterns
|   +-- decimal row labels in compiler input
|   +-- C-3..B-5 note range
|   +-- PT-compatible effects only
|   +-- forward loops only
|
+-- Source Samples                                 [COMPLETE]
|   +-- ST-01/RingPiano
|   +-- ST-01/PanFlute
|   +-- ST-01/SoftBass
|   +-- ST-01/BassDrum3
|   +-- ST-01/Snare1
|   +-- ST-01/CloseHiHat
|   +-- ST-01/Strings7
|   +-- ST-01/PingBells
|
+-- Musical Architecture                           [COMPLETE]
|   +-- three/four-voice piano model
|   +-- consolidated percussion
|   +-- beat-aligned bells
|   +-- filtered PanFlute episode
|   +-- final rallentando and coda
|
+-- Pattern Set 00-0f                              [COMPLETE]
|   +-- all individual auditions passed
|   +-- all paired/sectional auditions passed
|
+-- Final Assembly                                 [COMPLETE]
|   +-- 22-position order list locked
|   +-- full MOD compiled
|   +-- full composition auditioned
|   +-- multiple sound systems passed
|   +-- runtime confirmed: 146 seconds
|   +-- file size confirmed: 59.07 kB
|
+-- Archival / Release                             [OPTIONAL]
    +-- checksums
    +-- release tag
    +-- redundant backups
```

No production dependency remains unresolved.

### Version Log

#### Final Consolidated Bootstrap

- Project title locked as **Clockwork Picnic**.
- Eight-sample ST-01 instrument set auditioned and accepted.
- Volumes, finetunes, and the Strings7 forward loop locked.
- Three/four-voice piano architecture locked.
- Decimal-row compiler notation locked.
- Patterns `00`-`0f` composed and auditioned.
- Final order list locked at `16` hex entries.
- Full module compiled successfully.
- Complete composition auditioned successfully on multiple sound systems.
- Exact runtime confirmed as `02:26`.
- Final file size confirmed as `59.07 kB`.
- Project status set to **complete**.

---

## 4. Golden Code Blocks

### Final Project Metadata

```yaml
project:
  title: Clockwork Picnic
  status: complete
  tracker: MilkyTracker
  platform: Linux / PikaOS
  format: ProTracker MOD
  compatibility_target: ProTracker 2
  channels: 4
  rows_per_pattern: 64
  row_number_base: decimal
  omit_empty_rows: true
  speed: 0x06
  baseline_bpm: 0x84
  pattern_count: 0x10
  highest_pattern: 0x0f
  order_length: 0x16
  final_order_position: 0x15
  final_pattern: 0x0f
  runtime_seconds: 146
  runtime_display: "02:26"
  file_size: "59.07 kB"
  looping_composition: false
  ending: deliberate-coda
  full_build_compiled: true
  multi_system_audition: passed
```

### Final Order List

```yaml
order:
  - 0x00
  - 0x01
  - 0x02
  - 0x03
  - 0x04
  - 0x01
  - 0x02
  - 0x05
  - 0x06
  - 0x03
  - 0x04
  - 0x07
  - 0x08
  - 0x09
  - 0x0a
  - 0x0b
  - 0x0c
  - 0x05
  - 0x06
  - 0x0d
  - 0x0e
  - 0x0f
```

### Approved Instruments

```yaml
instruments:
  - id: 1
    source: st01
    name: ST-01/RingPiano
    volume: 0x10
    finetune: 0x0

  - id: 2
    source: st01
    name: ST-01/PanFlute
    volume: 0x10
    finetune: 0xe

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
    finetune: 0x2
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
- [x] Patterns `00`-`0f` individually auditioned.
- [x] Pattern pairs and structural sections auditioned.
- [x] Final 22-position order list compiled.
- [x] Repeated-pattern transitions passed in context.
- [x] PanFlute entry and return transitions passed in context.
- [x] Final filter-state sequence passed in context.
- [x] Final rallentando passed.
- [x] Definite non-fade ending passed.
- [x] Full composition auditioned from beginning to end.
- [x] Playback passed on multiple sound systems.
- [x] Exact runtime confirmed as `02:26`.
- [x] Final file size confirmed as `59.07 kB`.

### Validation Boundary

No separate original ProTracker 2 hardware or original ProTracker 2 executable validation is recorded in this bootstrap. The module was designed within the stated PT2 constraints, compiled successfully, and passed the reported multi-system playback auditions.

### Final Status

**COMPLETE - PASSING**

The final build is authoritative. No musical or technical work remains outstanding within the accepted project scope.

---

## Tools Used

- **Testing OS:** PikaOS
- **Testing tracker:** MilkyTracker
- **Pattern entry:** custom Markdown-compatible pattern compiler
- **Build path:** accepted pattern tables compiled into the final `.mod`
- **Final playback validation:** multiple sound systems
