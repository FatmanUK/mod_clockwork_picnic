I'm at a bit of a loss here. The composition just doesn't sound right. The patterns are nice but I can't imagine a pianist playing them. Pianists don't usually play two notes at a time. It's like I'm asking the pianist to play using just one finger on each hand, which is weird. I don't know how to fix this.

[kicked up to Pro for some real architectural muscle]

---

You’ve found the real problem. It is not the tempo now. It is the **polyphony model**.

We mapped:

* CH1 = right hand
* CH4 = left hand

But each tracker channel is monophonic. That means the “pianist” can produce only two notes at once, one per hand. The result is exactly what you described: two fingers poking at a keyboard with admirable discipline and no convincing reason.

A believable piano texture usually needs at least three independent voices:

* a top melody;
* one or more inner chord tones;
* a bass or lower accompaniment voice.

So we should stop treating a tracker channel as an entire hand. A channel is one **piano voice**. Several voices together imply the two hands.

## Revised channel architecture

For the piano-led sections:

| Channel | Role                                                         |
| ------- | ------------------------------------------------------------ |
| CH1     | Piano top voice / melody                                     |
| CH2     | Piano inner voice / right-hand harmony                       |
| CH3     | Combined percussion, yielding to piano at important cadences |
| CH4     | Piano lowest voice / left-hand anchor                        |

That gives us three-note piano voicings while retaining one percussion channel. At important phrase endings, CH3 can temporarily become a **fourth piano voice**, with the drums simply resting. A human drummer can survive four rows of unemployment. They may even cherish them.

SoftBass should remain absent during the core piano theme. PingBells should also wait until the piano texture deliberately thins. Otherwise we are spending scarce channels on decoration while the featured instrument still sounds anatomically improbable.

## How the piano writing changes

The existing melodies can survive. What needs changing is the voicing underneath them.

Instead of this:

```text
RH: E-4
LH: C-3
```

we need textures such as:

```text
Top voice:    E-4
Inner voice:  G-3
Bass voice:   C-3
```

That produces a complete C-major sonority.

The inner voice should not mechanically move with every melody note. It can sustain while the melody changes, then move smoothly to the nearest chord tone. That creates actual **voice leading**, which is one of the things our patterns currently lack.

The left hand should also use recognisable accompaniment shapes:

* bass note followed by a chord;
* root followed by fifth;
* broken triads;
* occasional octaves or open fifths;
* fuller cadential chords at phrase endings.

Not every moment needs a three-note chord. Human piano playing alternates between full harmony, held tones, broken chords and exposed melodic notes. The difference is that fuller voicings are available when the phrase calls for them.

## Rolled chords

We can also use ProTracker’s `EDx` note-delay command sparingly.

* `ED1` delays the note by one tick.
* `ED2` delays it by two ticks.

At speed `06`, that lets us spread a chord across a fraction of a row, producing a restrained rolled-chord effect instead of three notes landing with machine-perfect simultaneity.

For example:

```text
| RR | CH1        | CH2        | CH3        | CH4        |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | E-4 01 ED2 | G-3 01 ED1 | --- -- --- | C-3 01 --- |
| 04 | G-4 01 --- | --- -- --- | C-4 04 --- | --- -- --- |
| 08 | C-4 01 ED2 | A-3 01 ED1 | --- -- --- | F-3 01 --- |
| 12 | B-3 01 ED2 | G-3 01 ED1 | C-4 05 --- | D-3 01 --- |
```

Musically, those rows imply:

* C major: `C–G–E`
* continued C harmony with a moving top voice;
* F major: `F–A–C`
* G major: `D–G–B`

That already resembles piano writing far more than a melody note plus an isolated bass note.

The rolling should be occasional. If every chord uses `ED1` and `ED2`, the pianist starts sounding less human and more as though they are perpetually tumbling downstairs.

## What to retain and what to discard

Patterns `00`, `01`, and `02` have useful melodic pacing and phrase shapes. Their audition passes were not wasted. They should now be treated as **melodic and rhythmic skeletons**, then revoiced with a third piano voice.

Patterns `03` and `04` should be discarded in their current form. Writing further patterns before fixing the piano texture would simply reproduce the same architectural mistake with increasingly attractive melodies.

The proper next move is therefore a **revoicing pass over `00–02`**:

* preserve the accepted melody and pacing;
* move the existing hi-hat activity out of CH2;
* add an inner RingPiano voice on CH2;
* consolidate kick, snare and occasional hat into CH3;
* let CH3 become piano briefly at important cadences;
* keep CH4 as the lowest piano voice rather than pretending it represents the whole left hand.

That is the fix. We do not need a new tune. We need to give the current tune enough fingers.

---

Agreed. Since 01, 02, 03 and 04 are all the same main theme, can you write them all together?

---

These versions supersede every earlier `01–04`.

The piano is now treated as **three or four independent voices**, not one tracker channel per hand:

* **CH1:** top piano voice and melody
* **CH2:** inner piano voice
* **CH3:** consolidated percussion; temporarily becomes a fourth piano voice at major cadences
* **CH4:** lowest piano voice

`ED1` and `ED2` delay a note by one or two ticks. They are used only on selected phrase-opening and cadential chords to create a light low-to-high roll. The pianist is now allowed several fingers, an innovation the instrument industry has apparently supported for centuries.

The low-pass filter remains on through `01–02`. Pattern `03` switches it off with `E01`, giving the second half of the theme a natural lift.

## Pattern 01 — The Picnic Tune, Phrase A

| RR | CH1        | CH2        | CH3        | CH4        |
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

The final two piano groups are:

```text
row 58: C-E-G
row 60: D-G-B
```

So the pattern moves from a complete C-major triad onto a complete G-major triad and deliberately leaves the theme unresolved for `02`.

## Pattern 02 — The Picnic Tune, Phrase B

| RR | CH1        | CH2        | CH3        | CH4        |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | E-4 01 ED2 | G-3 01 ED1 | C-4 04 --- | C-3 01 --- |
| 04 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 08 | E-4 01 --- | C-4 01 --- | C-4 05 --- | G-3 01 --- |
| 12 | C-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 16 | D-4 01 --- | A-3 01 --- | C-4 04 --- | F-3 01 --- |
| 20 | F-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 24 | E-4 01 --- | G-3 01 --- | C-4 05 --- | C-3 01 --- |
| 28 | C-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 32 | D-4 01 --- | B-3 01 --- | C-4 04 --- | G-3 01 --- |
| 36 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 40 | F-4 01 --- | B-3 01 --- | C-4 05 --- | D-3 01 --- |
| 44 | D-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 48 | E-4 01 --- | G-3 01 --- | C-4 04 --- | C-3 01 --- |
| 52 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 56 | E-4 01 --- | C-4 01 --- | C-4 05 --- | E-3 01 --- |
| 58 | D-4 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 60 | C-4 01 ED2 | G-3 01 ED1 | E-3 01 --- | C-3 01 --- |

At row `60`, CH3 yields the drum part and becomes the second inner piano voice:

```text
C-3 / E-3 / G-3 / C-4
```

That is the first full four-note piano cadence.

## Pattern 03 — Main Theme Development A

| RR | CH1        | CH2        | CH3        | CH4        |
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

`E01` turns the low-pass filter off at row `00`.

The large-scale movement is:

```text
F/C → D minor → G → C → G
```

The closing G chord prepares `04`, so `03` behaves as the first half of a pair rather than reaching a premature conclusion.

## Pattern 04 — Main Theme Development B

| RR | CH1        | CH2        | CH3        | CH4        |
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

The final three harmonic events are deliberately explicit:

```text
row 56: C/E
row 58: G/D
row 60: C major
```

Again, CH3 abandons percussion at the final cadence so the pianist can land on a full four-note chord instead of being contractually restricted to two fingers.

For the joint audition, use:

```text
01, 02, 03, 04
```

The main things to judge are whether CH1 and CH2 read as a coordinated right hand, whether CH4 gives the piano enough lower-body movement, whether the rolled chords sound natural rather than gimmicky, and whether losing a few drum hits at the cadences makes those arrivals feel played rather than sequenced.

---

You forgot pattern00.

---

Correct. I rewrote the main theme and somehow left the entrance hall attached to the old architecture. An impressively literal omission.

This replacement preserves **every CH1 and CH4 note from your accepted Pattern `00`**, including `E00`. The changes are confined to revoicing:

* CH2 now supplies piano harmony.
* CH3 acts as a fourth piano voice through row `32`.
* CH3 becomes the consolidated percussion channel from row `36`.
* Where a kick or snare occurs, the simultaneous hi-hat from the old arrangement is omitted. One percussion channel remains stubbornly one percussion channel.

## Pattern 00 — Winding the Clock, polyphonic revoicing

| RR | CH1        | CH2        | CH3        | CH4        |
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

The opening now establishes fuller piano harmony:

```text
row 00: C-E-G-C
row 08: C-E-G
row 12: E-G-C
row 16: C-E-A-C
row 24: C-E-G-C
row 32: C-F-A
```

The transition into the rhythm section is also harmonically continuous:

```text
row 36: F-A-C
row 40: F-A-C
row 44: E-G-C
row 48: G-B-F       G7 shell
row 52: G-A-C       suspended dominant colour
row 56: G-B-D
row 60: G-A-C       suspension returns
row 62: G-B-D       resolves before Pattern 01
```

Rows `60–62` therefore create a small dominant suspension and resolution, after which Pattern `01` lands on C. The drums arrive without forcing the piano back into two-note anatomy.

The complete main-theme audition order is now:

```text
00, 01, 02, 03, 04
```

Patterns `00–04` should be treated as one revised polyphonic set.
