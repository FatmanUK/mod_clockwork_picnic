# Pattern 01 — The Picnic Tune, Phrase A

Now the rhythm section joins, but it has to work around the pianist rather than the reverse.

Channel 2 takes hats. Channel 3 combines kick and snare. SoftBass is deliberately **absent** from this first main-theme pattern because Channel 4 is already doing real bass work.

This version gives the piano much more physical logic. The left hand generally changes every four rows and alternates between root/fifth/chord-tone shapes a pianist could actually play. The right hand uses longer gestures and rests, with only occasional quicker movement such as `18 → 1a → 1c → 1e`. Those little runs should consequently sound like deliberate flourishes rather than the pianist having suffered an electrical malfunction.

There's another intentional feature: **pattern `01` does not resolve to C**. Its final four bars lean strongly onto G. That makes `01` genuinely **Phrase A**, not a self-contained 64-row tune. Pattern `02` can be Phrase B and provide the satisfying return home. This is exactly where accepting a longer runtime helps us. We no longer have to cram an entire melodic argument into seven seconds.

For the first audition, I'd compile simply:

```text
00, 01
```

The important test is no longer merely whether the samples balance. Listen specifically to whether **Channels 1 and 4 register psychologically as the right and left hands of one pianist**. If that illusion works, we've found the central arranging technique for the whole piece. If it doesn't, there is no point building `02` on top of it.

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
