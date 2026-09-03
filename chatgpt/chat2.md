```
[x] repack the archives as tarballs
```

Here are the archives in tarball format.

---

Both tarballs extracted successfully. They contain **126 ST-01 samples and 121 ST-02 samples**, so we now have the real source material rather than having to divine musical truth from filenames.

I’ve also confirmed that the samples are readable as the expected raw 8-bit sample data. Initial analysis already gives us some promising candidates: `Steinway`, `EPiano`, `PanFlute`, `SoftBass`, `BassDrum3`, `Snare1`, `CloseHiHat`, `Strings7`, plus several useful character sounds such as `PingBells` and `WoodBlock`. ST-02 also gives us alternatives including `AcoPiano`, `TeaPiano`, `stringsc`, and `WarmBells`.

There are meaningful differences in the actual envelopes. For example, `Steinway` has a strong attack followed by a gradual decay, `PanFlute` remains comparatively sustained, `SoftBass` decays cleanly, and `Strings7` actually maintains/increases its energy toward the end, making it an obvious loop candidate. `CloseHiHat` is extremely short and low-level, while `BassDrum3` has a very strong transient and rapid decay. So analysing the files rather than trusting their names was worth doing.

One useful historical cross-check also lines up: the archived ST-01 distribution lists the same sample sizes as your files, including `Steinway` at 6900 bytes, `SoftBass` at 4900, `Snare1` at 2000, and `PanFlute` at 9900. That strongly indicates we're dealing with the canonical ST-01 versions rather than some later mangled collection. ([AmiNet][1])

I'll treat these uploaded archives as our **actual sample source of truth**, as required by the bootstrap. 

The next part of Step 2 is therefore properly unlocked: selecting the final **eight candidate samples** and producing their volume/envelope analysis, loop recommendations, finetune values, PT2 note-range maps and audition criteria.

[1]: https://aminet.net/package/mods/inst/st-01?utm_source=chatgpt.com "Aminet - mods/inst/st-01.lha"

---

Proceed.

---

I’ve done the first-pass selection against the actual raw samples you uploaded, not merely the filenames. The aim is a compact palette in which every instrument earns its bytes. The bootstrap wants eight samples, including a piano lead and a haunting woodwind passage, with strong pattern reuse and PT2 constraints. 

My proposed **Clockwork Picnic** sample set is:

| Slot | Sample             | Role                      | Size | Default vol. | Loop?       | Practical range |
| ---- | ------------------ | ------------------------- | ---: | -----------: | ----------- | --------------- |
| `01` | ST-01 `Steinway`   | Main piano                | 6900 |       `0x30` | No          | C-3–C-5         |
| `02` | ST-01 `PanFlute`   | Haunting woodwind solo    | 9900 |       `0x28` | Probably no | G-3–B-4         |
| `03` | ST-01 `SoftBass`   | Main bass                 | 4900 |       `0x38` | No          | C-4–B-5         |
| `04` | ST-01 `BassDrum3`  | Kick                      | 3400 |       `0x30` | No          | fixed pitch     |
| `05` | ST-01 `Snare1`     | Snare                     | 2000 |       `0x34` | No          | fixed pitch     |
| `06` | ST-01 `CloseHiHat` | Closed hat                | 1200 |       `0x40` | No          | fixed pitch     |
| `07` | ST-01 `Strings7`   | Sustained harmonic bed    | 9900 |       `0x20` | **Yes**     | C-3–B-4         |
| `08` | ST-01 `PingBells`  | Mechanical sparkle/accent | 5400 |       `0x28` | No          | C-3–B-4         |

That's **43,600 bytes of raw sample material**, before the MOD's patterns and headers. So the bootstrap's sub-40KB bonus target is already out of reach unless we shorten samples later. I would not optimise for that yet. Musical quality gets first refusal; byte-count masochism can come afterward. 

The selection being entirely ST-01 is deliberate, not an oversight. I inspected the ST-02 alternatives as well, but none displaced these eight strongly enough for this particular piece. ST-01 is also historically appropriate: `Steinway`, `Strings7` and `PingBells` appear together in very early Soundtracker material, and historical sample research identifies `Steinway` with the Yamaha DX21 "Deep Grand", `Strings7` with the Roland D-50 "Legato Strings", and `PingBells` with the Juno-106 "Pingbell". ([modsamplemaster.org][1])

The envelope measurements explain most of the choices. These are measurements from **your uploaded raw samples**, with peak on the signed 8-bit ±128 scale:

| Sample     | Peak | Overall RMS | Envelope behaviour                               |
| ---------- | ---: | ----------: | ------------------------------------------------ |
| Steinway   |  127 |        32.6 | Strong attack → steady natural decay             |
| PanFlute   |  116 |        45.9 | Strong sustained body → moderate tail            |
| SoftBass   |  101 |        24.0 | Firm attack → rapid, clean decay                 |
| BassDrum3  |  128 |        65.8 | Huge transient → very rapid decay                |
| Snare1     |  111 |        53.1 | Strong transient → noisy short tail              |
| CloseHiHat |   34 |         5.9 | Very quiet, extremely rapid decay                |
| Strings7   |   86 |        33.0 | Sustained; tail is actually stronger than attack |
| PingBells  |  100 |        16.2 | Clear attack → long but rapidly diminishing ring |

Those volume recommendations therefore aren't simple peak normalisation. For instance, `CloseHiHat` needs the full `40` available to it because the source itself is extraordinarily quiet, whereas `BassDrum3` absolutely does **not** need `40`: its transient already hits the signed 8-bit limit. Likewise, `Strings7` should sit substantially below the piano so four-channel arrangements don't turn into a woolly soup.

`Steinway` is an especially strong choice. Its quarter-by-quarter RMS falls approximately **48.0 → 30.8 → 24.5 → 19.8**. That's precisely the sort of naturally decaying piano envelope we want for a melodic voice. I would leave it unlooped. It should make short jaunty figures articulate while allowing held notes enough tail to breathe.

`PanFlute` is our oboe substitute. There is no literal `Oboe` in these archives, and the bootstrap explicitly permits an oboe **or similar woodwind**.  Its envelope is much more sustained than the piano, approximately **60.1 → 47.3 → 42.1 → 28.3 RMS** across its quarters. That should contrast nicely with the percussive piano. I initially considered looping it, but I'd audition the natural sample first. A finite breath-like decay may make the two-pattern solo more expressive than an indefinitely held tracker flute.

`SoftBass` gets the bass job because its envelope falls **38.8 → 22.7 → 13.9 → 9.4**. That's useful here: enough initial definition to survive beneath the piano without creating a permanent low-frequency drone. Because the bootstrap specifically says low-pitched samples should be restricted to octaves 4–5, that's where we'll keep it. 

`BassDrum3` is aggressive enough to provide the rhythmic engine without effects or layering. Its RMS collapses from **108.5 in the first quarter to 13.3 in the last**. That is an excellent compact tracker kick envelope.

`Snare1` behaves similarly, falling from **86.6 to 20.6 RMS**. It's short, crisp and only 2000 bytes. No compelling reason to spend four kilobytes on one of the larger snares unless the audition reveals a tonal problem.

`CloseHiHat` is almost comically tiny and quiet: peak **34**, just **1200 bytes**, with its final quarter down around **0.2 RMS**. That's actually useful. At `40` it can provide busy subdivisions without competing with the melodic channels.

`Strings7` is the one definite **forward-loop candidate**. Unlike the decaying samples, its quarter RMS progresses **28.5 → 32.5 → 33.5 → 37.0**. The sustained tail is exactly where we'd expect to hunt for a stable loop. Independent historical sample indexing also classifies the 9900-byte ST-01 `Strings7` as looped, so the waveform evidence and historical usage agree. ([modsamplemaster.org][2]) You should determine the exact loop start and length by ear in MilkyTracker, as required by our source-of-truth rules. 

Finally, `PingBells` is where the title starts paying rent. It's a genuine historical ST-01 voice identified with the Juno-106 Pingbell preset. ([namelessalgorithm.com][3]) Its sharp attack and rapidly declining tail make it ideal for sparse clockwork punctuation, little answering figures, transitions and perhaps the final coda. It should **not** become a constant arpeggio machine. Humanity has committed enough crimes with bell patches already.

On **finetune**, I've hit an evidentiary snag worth being explicit about. The bootstrap says historical ST-01/ST-02 finetunes are well established online and asks me to find them.  I can verify the sample identities and historical use online, but I have **not found a reliable source that establishes canonical PT2 finetune values for these exact raw files**. The raw samples themselves contain no metadata from which such values could be recovered. I therefore won't manufacture eight numbers and call them historical facts. For the first audition, set all eight to **finetune `0`**. We can subsequently establish corrections empirically against the piano/reference pitch and record the accepted values in the project files.

For the pitched instruments, these are deliberately **practical composition ranges**, not merely everything PT2 is capable of playing:

* `01 Steinway`: **C-3–C-5**. Main melodic centre roughly C-4–C-5.
* `02 PanFlute`: **G-3–B-4**. Keep most solo writing in the middle rather than making it shriek.
* `03 SoftBass`: **C-4–B-5**, complying with the bootstrap's special low-sample rule.
* `07 Strings7`: **C-3–B-4**. Prefer restrained chord tones and counterlines.
* `08 PingBells`: **C-3–B-4**, but mainly C-4 upward for accents.

All remain inside the mandated global **C-3 through B-5** PT2 range. 

For percussion, I'd initially audition the three samples at their natural/default tracker pitch rather than pretending a "note range" has musical significance. Once we know which note produces the intended timbre in your compiler/MilkyTracker setup, we should standardise each drum to one note and use it consistently.

For your **audition**, I'd test these specific things rather than merely deciding whether each sample sounds pleasant in isolation:

1. Play `Steinway` around C-4–C-5 and check whether repeated eighth-note figures remain articulate. Also hold notes long enough to hear whether the tail becomes objectionably grainy.
2. Play `PanFlute` around G-3–B-4. Check pitch stability, breath/noise character, and whether sustained notes feel haunting rather than cheesy. This is the sample I regard as least certain.
3. Play `SoftBass` underneath the piano. It must be clearly audible without swallowing the piano attack.
4. Alternate `BassDrum3` and `Snare1` at moderate density. Listen for whether they read as a coherent kit rather than two unrelated pieces of 1987 archaeology.
5. Run sixteenth-note `CloseHiHat` figures. At `40`, confirm it is audible but doesn't become irritating.
6. Find a clean forward loop for `Strings7`. Hold a chord for several seconds and listen specifically for clicks, obvious cyclic pulsing and pitch wobble.
7. Play occasional `PingBells` notes over piano/bass/drums. We want a distinctive sparkle at low density. If it immediately demands attention every time it appears, reduce its volume rather than discarding it.
8. Most importantly, audition **all eight together**. Four-channel music is about sounds surrendering territory to one another. A glorious solo sample that masks everything else is considerably less useful than a modest one that slots neatly into the mix.

So my recommendation is to treat these as the **eight provisional candidates**, with `Strings7` provisionally looped and the other seven unlooped. The two samples I would scrutinise most closely are **PanFlute** and **CloseHiHat**. Everything else looks unusually well suited to *Clockwork Picnic* on both sonic and economy grounds.

Once you've auditioned them, your accepted volumes, loop decision/points and any tuning corrections become authoritative rather than my measurements. That's the bootstrap's intended division of labour. 

[1]: https://modsamplemaster.org/module.php?sha1=e271461a9009ff7755c7e2b09f8b470e7d270ec4&utm_source=chatgpt.com ".mod Sample Master :: Module \"rallyemaster\" [Ultimate Soundtracker] (e271461a9009ff7755c7e2b09f8b470e7d270ec4)"
[2]: https://www.modsamplemaster.org/sample.php?hash=33ac04e7089d9ac7a196d56782057785cdfc2e8b&utm_source=chatgpt.com ".mod Sample Master :: Sample 33ac04e7089d9ac7a196d56782057785cdfc2e8b (aa955b25af7132968da9b5bafaf24f2a)"
[3]: https://namelessalgorithm.com/game_audio/blog/trackers/?utm_source=chatgpt.com "Nameless Algorithm: Game Audio"

---

```
[x] select eight samples ... which will accomplish the goal and achieve the desired character
[x] state which samples are to be looped, if any... forward loops are the only kind of loops allowed
[x] analyse the samples' envelopes and recommend default volume ... note recorded peak and envelope behaviour
[x] find and report [finetune values] for audition by the user... [or] make a note
[x] generate note-range maps
[x] suggest audition criteria
```

```
TODO:
  [x] find loop points
  [x] finetune samples
  [ ] report back any finetune decisions and loop points
  [x] final sample audition
```
