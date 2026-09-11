No, you're doing it again. That's too fast and staccato. Slow the roll.

And while we're at it, drop ch1 by an octave in all patterns. That way we don't risk bumping up against the ceiling.

---

Agreed. I was still treating “slower” as “put a note every two rows instead of every row,” which rather misses the point.

Two changes are now hard rules:

1. **CH1 RingPiano is transposed down one octave in all piano patterns.** That gives the right hand comfortable headroom and puts its normal register closer to `C-4`–`C-5`.
2. **The piano rhythm slows substantially.** Normal right-hand attacks should be separated by roughly **4–8 rows**, with longer held notes and actual rests. Two-row movement becomes an occasional ornament, not the basic pulse. The left hand should generally change only every **8 rows or more**.

I’d also make the piano less relentlessly synchronized with the drums. A human performance needs phrases that cross the accompaniment rather than a new piano note obediently appearing at every percussion landmark.

So Pattern `02` is discarded, and `00`/`01` need revision too. Rather than patching them note-by-note, here is the corrected musical density demonstrated with a replacement opening.

### Pattern `00` — Winding the Clock, revised

Solo piano for the first three quarters. The rhythm section merely hints at its arrival near the end.

| RR | CH1        | CH2        | CH3        | CH4        |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | E-3 01 F84 | --- -- --- | --- -- --- | C-3 01 --- |
| 06 | G-3 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 12 | C-4 01 --- | --- -- --- | --- -- --- | G-3 01 --- |
| 18 | B-3 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 22 | A-3 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 28 | E-3 01 --- | --- -- --- | --- -- --- | A-3 01 --- |
| 36 | A-3 01 --- | --- -- --- | --- -- --- | E-3 01 --- |
| 42 | C-4 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 48 | A-3 01 --- | --- -- --- | --- -- --- | F-3 01 --- |
| 54 | G-3 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 58 | F-3 01 --- | C-4 06 --- | --- -- --- | C-4 01 --- |
| 60 | --- -- --- | --- -- --- | C-4 04 --- | --- -- --- |
| 62 | A-3 01 --- | C-4 06 --- | --- -- --- | --- -- --- |

That's closer to the intended grammar. The right hand has **11 attacks in 64 rows**, not thirty-odd. Some notes get six or eight rows to decay naturally. The left hand supplies broad harmonic gestures instead of behaving like an automated bass sequencer.

The opening phrase now has room to be heard as:

```text
RH: E-3   G-3      C-4   B-3 A-3
LH: C-3             G-3

RH: E-3       A-3   C-4       A-3 G-3 F-3   A-3
LH: A-3       E-3             F-3      C-4
```

That is much closer to something a pianist might phrase with two hands.

For **Pattern `01`**, I’ll use the same density target but introduce the accompaniment gradually. It should probably contain only about **12–14 right-hand attacks**, with the left hand changing perhaps six to eight times across the entire pattern. The drums can establish a pulse independently in Channels 2/3 rather than forcing the piano onto their grid.

And the octave rule is retroactive: every existing CH1 piano note that survives into the rewritten material comes down exactly one octave. So, for example, old `C-5` becomes `C-4`, `G-5` becomes `G-4`, and `A-4` becomes `A-3`.

This revised `00` is the density benchmark I'll use for the rest of the piano writing.

---

Go ahead and give me pattern01 now. I'll review the new pattern00 and pattern01 together.

---

Pattern `01` should now feel like the same pianist continuing after `00`, except the rhythm section has quietly arrived. I’m keeping the right hand at the new density and letting the left hand provide the harmonic weight. No SoftBass or PingBells yet.

### Pattern `01` — The Picnic Tune, Phrase A

The harmonic path is broadly **C → Am → F → G**, with the final G left unresolved so the eventual Pattern `02` has somewhere meaningful to go.

| RR | CH1        | CH2        | CH3        | CH4        |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | C-4 01 --- | --- -- --- | C-4 04 --- | C-3 01 --- |
| 04 | --- -- --- | C-4 06 --- | --- -- --- | --- -- --- |
| 06 | E-4 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 08 | --- -- --- | --- -- --- | C-4 05 --- | G-3 01 --- |
| 12 | G-4 01 --- | C-4 06 --- | --- -- --- | --- -- --- |
| 16 | E-4 01 --- | --- -- --- | C-4 04 --- | C-3 01 --- |
| 20 | --- -- --- | C-4 06 --- | --- -- --- | --- -- --- |
| 22 | D-4 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 24 | --- -- --- | --- -- --- | C-4 05 --- | G-3 01 --- |
| 28 | C-4 01 --- | C-4 06 --- | --- -- --- | --- -- --- |
| 32 | E-4 01 --- | --- -- --- | C-4 04 --- | A-3 01 --- |
| 36 | --- -- --- | C-4 06 --- | --- -- --- | --- -- --- |
| 40 | A-4 01 --- | --- -- --- | C-4 05 --- | E-3 01 --- |
| 44 | G-4 01 --- | C-4 06 --- | --- -- --- | --- -- --- |
| 48 | A-3 01 --- | --- -- --- | C-4 04 --- | F-3 01 --- |
| 52 | C-4 01 --- | C-4 06 --- | --- -- --- | --- -- --- |
| 56 | A-3 01 --- | --- -- --- | C-4 05 --- | C-4 01 --- |
| 58 | G-3 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 60 | B-3 01 --- | C-4 06 --- | C-4 04 --- | G-3 01 --- |
| 63 | --- -- --- | --- -- --- | --- -- --- | D-4 01 --- |

This gives CH1 **13 attacks in the whole pattern**. The ordinary spacing is four to eight rows, with only the little `56 → 58 → 60` figure accelerating toward the cadence. That is now an ornament because the surrounding music establishes a slower vocabulary.

The right-hand phrasing breaks down roughly as:

```text
00–15   C-4 → E-4 → G-4
        broad opening gesture

16–31   E-4 → D-4 → C-4
        answering descent

32–47   E-4 → A-4 → G-4
        wider, more lyrical second idea

48–63   A-3 → C-4 → A-3 G-3 B-3
        compact turnaround onto G
```

CH4 behaves much more like a left hand:

```text
00  C-3
08  G-3
16  C-3
24  G-3

32  A-3
40  E-3

48  F-3
56  C-4

60  G-3
63  D-4
```

The first half deliberately establishes a simple C/G accompaniment. The second half then moves through A minor and F before the final open-fifth G/D shape. That should make the harmony feel played rather than continuously programmed.

There is one other deliberate difference from the earlier attempts: **the drums do not dictate the piano rhythm**. Kick/snare occupy Channel 3 and the hat Channel 2, but several piano attacks fall between or across those landmarks. The pianist and rhythm section share time rather than behaving as four columns receiving orders from the same spreadsheet.

For review, the current intended sequence is simply:

```text
00, 01
```

These two patterns should now be judged as one continuous opening: `00` establishes the pianist and lets the rhythm section creep in; `01` turns that vocabulary into the first proper theme phrase while retaining the slower, two-handed character.

---

[ ] Audition the new pattern00 and pattern01
[ ] Authorise composition of pattern02
