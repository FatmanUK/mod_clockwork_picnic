# Pattern 00 — Winding the Clock

The opening is essentially a two-handed piano performance. It establishes C major, briefly colours it with A minor and F, and then uses G to prepare the next pattern.

`F84` sets BPM `84` hex (132 decimal) on the opening note.

There are only **20 right-hand piano attacks across the entire pattern**, compared with the barrage in the rejected version. More importantly, the hands now move in recognisable harmonic groups.

Rows `00–0f` form the opening C-major phrase. Rows `10–1f` answer through A minor. Rows `20–2f` move through F. Rows `30–3f` establish G while the percussion quietly arrives. The final G in the left hand deliberately leaves the phrase unresolved so `01` can satisfy it.

# Pattern `00` — Winding the Clock, revised

Solo piano for the first three quarters. The rhythm section merely hints at its arrival near the end.

| RR | CH1        | CH2        | CH3        | CH4        |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | E-3 01 --- | --- -- --- | --- -- --- | C-3 01 --- |
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
