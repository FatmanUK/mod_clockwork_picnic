As charming as these patterns are, I have to reject them. I've not mentioned this, so my fault, but my intention is that the mod should sound like a human is playing the piano part. The current patterns would be too fast for a human pianist, and they're too staccato. The RingPiano sample doesn't sound right played that fast, and a human pianist would group the notes rather than playing one-at-a-time. I think we also need to designate Channel 4 as "piano left hand" to give a better impression that a human is playing (most pianists have two hands). To do that, we'll need to distribute the instruments currently in Channel 4 across Channels 2 and 3.

I'm happy for you to extend the track runtime if you need to add more patterns to slow the roll.

---

That rejection is musically justified, and it changes the architecture in a useful way. The previous patterns treated RingPiano as a tracker lead that happened to contain a piano sample. What we actually need is to treat the **piano as a two-handed instrument**, then make ProTracker accommodate it. Those are quite different propositions.

I’m discarding patterns `00` and `01`. They are not part of the composition.

The revised channel architecture should be:

| Channel | Primary responsibility                                                                                       |
| ------- | ------------------------------------------------------------------------------------------------------------ |
| **1**   | Piano right hand: melody, upper chord tones, occasional dyads implied through rapid but natural articulation |
| **2**   | Bass / PingBells / Strings / selected percussion                                                             |
| **3**   | Drums / Bass / Strings / PanFlute support as required                                                        |
| **4**   | **Piano left hand: bass notes, fifths, chordal support, cadential movement**                                 |

Channel 4 therefore becomes permanently reserved for the pianist's left hand whenever piano is present. That is a much stronger organising principle.

There is one important wrinkle: ProTracker gives us one note per channel at a time, so we cannot literally play conventional three- and four-note piano chords. Instead, we'll create the *perception* of two-handed piano playing through **voicing and grouping**. Right-hand notes should occur in phrases, with longer note values, rests and repeated rhythmic shapes. The left hand can land roots, fifths and occasional passing tones at harmonically meaningful points. Together, Channels 1 and 4 can imply chords convincingly without machine-gunning chord tones.

The main melody should also slow substantially. At speed `06` / BPM `84`, I want the ordinary melodic unit to become roughly the **quarter-note and eighth-note level**, with sixteenth-like tracker movement reserved for ornaments, pickups and short flourishes. A phrase might breathe something like this conceptually:

```text
RH:  C-5 .... E-5 .... G-5 ........ | E-5 .... D-5 .... C-5 ........
LH:  C-4 ............ G-4 .......... | C-4 ............ G-4 ..........
```

rather than the previous:

```text
RH: C-5 .. E-5 G-5 E-5 D-5 C-5 G-4 ...
```

That distinction is central. The first sounds like somebody sitting at a keyboard. The second sounds like a tracker composer discovering that empty rows don't consume disk space and becoming frightened of them.

I also want to revise the structural inventory. We no longer need to squeeze the piece into eleven patterns:

| Pattern group | Purpose                                      |
| ------------- | -------------------------------------------- |
| `00`          | Piano introduction, genuinely spacious       |
| `01–02`       | Main theme, phrase A + phrase B              |
| `03–04`       | Main theme continuation/development          |
| `05–06`       | Clockwork Games                              |
| `07`          | Transition / preparation                     |
| `08–09`       | PanFlute solo                                |
| `0a`          | Transition back                              |
| `0b–0c`       | Piano reprise, substantially reused material |
| `0d`          | Reprise lift / development                   |
| `0e`          | Coda setup                                   |
| `0f`          | Final flourish                               |

That's **16 available patterns**, though some may ultimately prove unnecessary. More importantly, a musical thought is now allowed two patterns where one previously had to do everything. Runtime can exceed 105 seconds if necessary. The original bootstrap already makes exact runtime subordinate to musical flow, authenticity and compatibility. 

There is also a useful orchestration consequence. **SoftBass no longer has to play constantly.** During piano-dominant passages, Channel 4's left hand can supply the bass register and Channel 2 can carry sparse percussion or PingBells while Channel 3 handles the rest of the kit. When SoftBass enters, it can feel like an arrangement change rather than permanent furniture.

For example:

```text
PIANO-LED PASSAGE

CH1  RingPiano RH
CH2  HiHat / PingBells
CH3  Kick + Snare
CH4  RingPiano LH
```

Then:

```text
FULL BAND PASSAGE

CH1  RingPiano RH
CH2  SoftBass
CH3  combined drum kit
CH4  RingPiano LH
```

And the PanFlute section can redistribute completely:

```text
WOODWIND PASSAGE

CH1  PanFlute
CH2  Strings7
CH3  sparse drums / SoftBass
CH4  RingPiano LH or sparse piano accompaniment
```

I particularly like retaining **piano left hand underneath parts of the PanFlute solo**. It means the human pianist doesn't mysteriously evaporate when the woodwind appears, and it gives us a way to connect Motif F to the rest of the piece.

One other change follows from your feedback: the RingPiano's natural decay needs to become part of the composition. We should allow notes enough time to **ring**. Repeated notes should usually represent actual rhythmic intention, not compensate for decay. Phrases need breathing spaces, and cadences need room to land.

So the new governing rule for the piano writing is:

> **Compose something a competent human pianist could plausibly perform with two hands first; encode that performance into two tracker channels second.**

That should produce a markedly different *Clockwork Picnic*.

The next version of pattern `00` should therefore be a genuine **solo/two-handed piano introduction**, perhaps with only a tiny amount of percussion entering toward its end. Pattern `01` can then introduce the rhythm section while preserving the same human piano vocabulary. No PingBell fireworks, no frantic eighth-row gymnastics, and considerably more empty space.

That is the architecture I’ll use for the replacement patterns.

---

This sounds good. Let's go for it.

---

Good. Then the replacement `00` and `01` should establish the rule rather than merely promise it.

I’m treating the previous versions as discarded. These are the new candidates.

A few compositional decisions first. The piano now gets **Channels 1 and 4 as a coordinated pair**. Right-hand phrases generally move every four rows, with longer holds at phrase boundaries. The left hand moves more slowly and outlines the harmony rather than mechanically shadowing the melody. In the opening, the pianist gets most of the stage to themselves. Percussion only begins late enough to feel like the rest of the arrangement has joined in.

### Pattern `00` — Winding the Clock

The opening is essentially a two-handed piano performance. It establishes C major, briefly colours it with A minor and F, and then uses G to prepare the next pattern.

`F84` sets BPM `84` hex (132 decimal) on the opening note.

| RR | CH1        | CH2        | CH3        | CH4        |
| -- | ---------- | ---------- | ---------- | ---------- |
| 00 | E-4 01 F84 | --- 00 000 | --- 00 000 | C-3 01 000 |
| 01 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 02 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 03 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 04 | G-4 01 000 | --- 00 000 | --- 00 000 | G-3 01 000 |
| 05 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 06 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 07 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 08 | C-5 01 000 | --- 00 000 | --- 00 000 | E-3 01 000 |
| 09 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 0a | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 0b | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 0c | B-4 01 000 | --- 00 000 | --- 00 000 | G-3 01 000 |
| 0d | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 0e | A-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 0f | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 10 | E-4 01 000 | --- 00 000 | --- 00 000 | A-3 01 000 |
| 11 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 12 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 13 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 14 | A-4 01 000 | --- 00 000 | --- 00 000 | E-3 01 000 |
| 15 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 16 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 17 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 18 | C-5 01 000 | --- 00 000 | --- 00 000 | A-3 01 000 |
| 19 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 1a | B-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 1b | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 1c | A-4 01 000 | --- 00 000 | --- 00 000 | E-3 01 000 |
| 1d | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 1e | G-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 1f | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 20 | A-4 01 000 | --- 00 000 | --- 00 000 | F-3 01 000 |
| 21 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 22 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 23 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 24 | C-5 01 000 | --- 00 000 | --- 00 000 | C-4 01 000 |
| 25 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 26 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 27 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 28 | A-4 01 000 | --- 00 000 | --- 00 000 | F-3 01 000 |
| 29 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 2a | G-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 2b | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 2c | F-4 01 000 | --- 00 000 | --- 00 000 | C-4 01 000 |
| 2d | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 2e | A-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 2f | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 30 | G-4 01 000 | --- 00 000 | C-4 04 000 | G-3 01 000 |
| 31 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 32 | --- 00 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 33 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 34 | B-4 01 000 | --- 00 000 | C-4 05 000 | D-4 01 000 |
| 35 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 36 | --- 00 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 37 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 38 | D-5 01 000 | --- 00 000 | C-4 04 000 | G-3 01 000 |
| 39 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 3a | C-5 01 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 3b | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 3c | B-4 01 000 | --- 00 000 | C-4 05 000 | D-4 01 000 |
| 3d | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 3e | G-4 01 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 3f | --- 00 000 | --- 00 000 | --- 00 000 | G-3 01 000 |

There are only **20 right-hand piano attacks across the entire pattern**, compared with the barrage in the rejected version. More importantly, the hands now move in recognisable harmonic groups.

Rows `00–0f` form the opening C-major phrase. Rows `10–1f` answer through A minor. Rows `20–2f` move through F. Rows `30–3f` establish G while the percussion quietly arrives. The final G in the left hand deliberately leaves the phrase unresolved so `01` can satisfy it.

### Pattern `01` — The Picnic Tune, Phrase A

Now the rhythm section joins, but it has to work around the pianist rather than the reverse.

Channel 2 takes hats. Channel 3 combines kick and snare. SoftBass is deliberately **absent** from this first main-theme pattern because Channel 4 is already doing real bass work.

| RR | CH1        | CH2        | CH3        | CH4        |
| -- | ---------- | ---------- | ---------- | ---------- |
| 00 | C-5 01 000 | --- 00 000 | C-4 04 000 | C-3 01 000 |
| 01 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 02 | --- 00 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 03 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 04 | E-5 01 000 | --- 00 000 | C-4 05 000 | G-3 01 000 |
| 05 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 06 | --- 00 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 07 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 08 | G-5 01 000 | --- 00 000 | C-4 04 000 | E-3 01 000 |
| 09 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 0a | E-5 01 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 0b | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 0c | D-5 01 000 | --- 00 000 | C-4 05 000 | G-3 01 000 |
| 0d | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 0e | --- 00 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 0f | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 10 | C-5 01 000 | --- 00 000 | C-4 04 000 | A-3 01 000 |
| 11 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 12 | --- 00 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 13 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 14 | E-5 01 000 | --- 00 000 | C-4 05 000 | E-3 01 000 |
| 15 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 16 | A-5 01 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 17 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 18 | G-5 01 000 | --- 00 000 | C-4 04 000 | A-3 01 000 |
| 19 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 1a | E-5 01 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 1b | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 1c | D-5 01 000 | --- 00 000 | C-4 05 000 | E-3 01 000 |
| 1d | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 1e | C-5 01 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 1f | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 20 | A-4 01 000 | --- 00 000 | C-4 04 000 | F-3 01 000 |
| 21 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 22 | --- 00 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 23 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 24 | C-5 01 000 | --- 00 000 | C-4 05 000 | C-4 01 000 |
| 25 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 26 | --- 00 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 27 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 28 | F-5 01 000 | --- 00 000 | C-4 04 000 | A-3 01 000 |
| 29 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 2a | E-5 01 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 2b | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 2c | C-5 01 000 | --- 00 000 | C-4 05 000 | C-4 01 000 |
| 2d | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 2e | A-4 01 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 2f | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 30 | B-4 01 000 | --- 00 000 | C-4 04 000 | G-3 01 000 |
| 31 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 32 | --- 00 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 33 | D-5 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 34 | --- 00 000 | --- 00 000 | C-4 05 000 | D-4 01 000 |
| 35 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 36 | G-5 01 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 37 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 38 | F-5 01 000 | --- 00 000 | C-4 04 000 | G-3 01 000 |
| 39 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 3a | D-5 01 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 3b | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 3c | B-4 01 000 | --- 00 000 | C-4 05 000 | D-4 01 000 |
| 3d | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 3e | G-4 01 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 3f | --- 00 000 | --- 00 000 | --- 00 000 | G-3 01 000 |

This version gives the piano much more physical logic. The left hand generally changes every four rows and alternates between root/fifth/chord-tone shapes a pianist could actually play. The right hand uses longer gestures and rests, with only occasional quicker movement such as `18 → 1a → 1c → 1e`. Those little runs should consequently sound like deliberate flourishes rather than the pianist having suffered an electrical malfunction.

There's another intentional feature: **pattern `01` does not resolve to C**. Its final four bars lean strongly onto G. That makes `01` genuinely **Phrase A**, not a self-contained 64-row tune. Pattern `02` can be Phrase B and provide the satisfying return home. This is exactly where accepting a longer runtime helps us. We no longer have to cram an entire melodic argument into seven seconds.

For the first audition, I'd compile simply:

```text
00, 01
```

The important test is no longer merely whether the samples balance. Listen specifically to whether **Channels 1 and 4 register psychologically as the right and left hands of one pianist**. If that illusion works, we've found the central arranging technique for the whole piece. If it doesn't, there is no point building `02` on top of it.

---

To make it easier to read the patterns, I'd like you to omit entirely empty rows.

---

Agreed. From now on, pattern tables will **omit rows where all four channels are empty**.

Row numbers will remain absolute hex row numbers, so gaps are intentional and the compiler placement remains unambiguous. For example:

```text
| RR | CH1          | CH2          | CH3          | CH4          |
|----|--------------|--------------|--------------|--------------|
| 00 | C-5 01 000   | --- 00 000   | C-4 04 000   | C-3 01 000   |
| 02 | --- 00 000   | C-4 06 000   | --- 00 000   | --- 00 000   |
| 04 | E-5 01 000   | --- 00 000   | C-4 05 000   | G-3 01 000   |
```

Rows `01` and `03` still exist; they're simply empty and therefore omitted from the Markdown representation.

I'll use this **sparse-row format for every pattern from here onward**. Much easier to inspect, and considerably less scrolling past the tracker equivalent of vacuum.

---

Oh, yes. Due to a bug in my pattern compiler, I need the row numbers to be decimal rather than hex,

---

Understood. From now on:

* **Row numbers:** decimal, `00`–`63`
* **Instrument IDs, volumes, finetunes, effects, loop values, speed/BPM:** hex as before
* **Entirely empty rows:** omitted
* Gaps in row numbering therefore represent empty rows.

So the same example becomes:

```text
| RR | CH1        | CH2        | CH3        | CH4        |
|----|------------|------------|------------|------------|
| 00 | C-5 01 000 | --- 00 000 | C-4 04 000 | C-3 01 000 |
| 02 | --- 00 000 | C-4 06 000 | --- 00 000 | --- 00 000 |
| 04 | E-5 01 000 | --- 00 000 | C-4 05 000 | G-3 01 000 |
```

Conveniently, rows `00`–`09` look identical in either notation, because apparently even bugs enjoy waiting until row 10 before becoming interesting.

I’ll apply decimal row numbering to all subsequent patterns.

---

To further aid legibility, please write "no instrument" as "--" and "no effect" as "---".

---

Agreed. The pattern notation is now:

* **No note:** `---`
* **No instrument:** `--`
* **No effect:** `---`
* **Row numbers:** decimal `00`–`63`
* **Entirely empty rows:** omitted

So an empty channel is now:

```text
--- -- ---
```

And the previous example becomes:

```text
| RR | CH1        | CH2        | CH3        | CH4        |
|----|------------|------------|------------|------------|
| 00 | C-5 01 --- | --- -- --- | C-4 04 --- | C-3 01 --- |
| 02 | --- -- --- | C-4 06 --- | --- -- --- | --- -- --- |
| 04 | E-5 01 --- | --- -- --- | C-4 05 --- | G-3 01 --- |
```

Actual effects retain their three-character ProTracker representation, such as `F84`.

This is considerably cleaner. The compiler's dialect is slowly acquiring the basic amenities of civilisation.
