## Pattern 0f — The Clock Springs Loose

| RR | CH1        | CH2        | CH3        | CH4        |
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

`E01` switches the low-pass filter off immediately, so the final pattern emerges from the filtered dominant with a clear tonal lift.

Rows `00–28` give the full ensemble one last bright statement. The two bells occur on rows `12` and `28`, aligned with the beat and used as punctuation rather than loose crockery falling down a staircase.

At row `32`, the drums and bells withdraw. All four channels become RingPiano:

```text
row 32: C-E-G-C
row 36: E-C-E-G
row 40: F-C-F-A
row 44: C-E-G-C
```

The final flourish then accelerates briefly:

```text
E-4 → F-4 → G-4 → A-4 → C-5 → B-4 → C-5
```

It is quick enough to sound like a deliberate pianist’s flourish, but short enough that we have not quietly reintroduced the earlier caffeinated typewriter problem.

The last three tempo commands create the rallentando:

* `F78`: 120 BPM
* `F70`: 112 BPM
* `F68`: 104 BPM

Because each value is at least `20` hex, ProTracker interprets it as a BPM change rather than a speed change.

Rows `48–56` harmonically form:

```text
G7 → Gsus4/D → G/D → C
```

The final chord is:

```text
CH4  C-3
CH3  G-3
CH2  E-4, delayed 1 tick
CH1  C-5, delayed 2 ticks
```

That produces a broad low-to-high rolled C-major chord. It begins at row `56`, leaving the remaining eight rows for the RingPiano sample to decay naturally at the slower final tempo.

For the ending audition, use:

```text
0b, 0c, 0d, 0e, 0f
```

For the complete final act:

```text
09, 0a, 0b, 0c, 0d, 0e, 0f
```

Pattern `0f` should be the final order-list entry. No pattern jump, no restart, and no fade. The composition simply lands, rings, and ends like it meant to.
