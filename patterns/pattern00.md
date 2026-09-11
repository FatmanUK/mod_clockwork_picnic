# Pattern 00 — Winding the Clock

The opening is essentially a two-handed piano performance. It establishes C major, briefly colours it with A minor and F, and then uses G to prepare the next pattern.

`F84` sets BPM `84` hex (132 decimal) on the opening note.

There are only **20 right-hand piano attacks across the entire pattern**, compared with the barrage in the rejected version. More importantly, the hands now move in recognisable harmonic groups.

Rows `00–0f` form the opening C-major phrase. Rows `10–1f` answer through A minor. Rows `20–2f` move through F. Rows `30–3f` establish G while the percussion quietly arrives. The final G in the left hand deliberately leaves the phrase unresolved so `01` can satisfy it.

# Pattern 00 — Winding the Clock, revised

Solo piano for the first three quarters. The rhythm section merely hints at its arrival near the end.

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

# Pattern 00 — Winding the Clock, replacement

| RR | CH1        | CH2        | CH3        | CH4        |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | E-3 01 E00 | --- -- --- | --- -- --- | C-3 01 --- |
| 04 | G-3 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 08 | E-3 01 --- | --- -- --- | --- -- --- | G-3 01 --- |
| 12 | C-4 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 16 | C-3 01 --- | --- -- --- | --- -- --- | A-3 01 --- |
| 20 | A-3 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 24 | C-3 01 --- | --- -- --- | --- -- --- | E-3 01 --- |
| 28 | G-3 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 32 | A-3 01 --- | --- -- --- | --- -- --- | F-3 01 --- |
| 36 | C-4 01 --- | C-4 06 --- | --- -- --- | --- -- --- |
| 40 | A-3 01 --- | C-4 06 --- | --- -- --- | C-4 01 --- |
| 44 | G-3 01 --- | C-4 06 --- | --- -- --- | --- -- --- |
| 48 | F-3 01 --- | C-4 06 --- | C-4 04 --- | G-3 01 --- |
| 52 | A-3 01 --- | C-4 06 --- | --- -- --- | --- -- --- |
| 56 | B-3 01 --- | C-4 06 --- | C-4 05 --- | D-4 01 --- |
| 58 | G-3 01 --- | --- -- --- | --- -- --- | --- -- --- |
| 60 | A-3 01 --- | C-4 06 --- | C-4 04 --- | G-3 01 --- |
| 62 | B-3 01 --- | C-4 06 --- | --- -- --- | --- -- --- |

This should connect much more naturally to `01`.

The first half now has a clear piano pulse rather than isolated notes floating in space. The phrasing is:

```text
E-3 → G-3 → C-4
B-3 → A-3 → E-3 → G-3
A-3 → C-4 → A-3 → G-3
F-3 → A-3 → B-3 → G-3 → A-3 → B-3
```

There's also a deliberate increase in activity. Rows `00–32` establish the piano; `36` introduces the hat on the same four-row grid that Pattern `01` subsequently uses; `48` adds the kick; `56` introduces the snare; and by `60` we're effectively playing the rhythm-section vocabulary that continues into `01`.

Crucially, the drums don't suddenly invent a beat. **The hat establishes the subdivision for twelve rows before the kick appears.** The listener should already understand the pulse by the time the heavier percussion joins.

CH4 also prepares Pattern `01` more deliberately. Its final movement is:

```text
48  G-3
56  D-4
60  G-3
```

Pattern `01` then lands:

```text
00  C-3
```

So we get a clear **G/D → G → C** dominant-to-tonic handoff across the pattern boundary.

The revised audition sequence remains:

```text
00, 01
```

This `00` is now much closer to `01` in note density, but still has an introductory trajectory: **piano → pulse → rhythm section → main theme**.
