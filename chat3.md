[x] find loop points
[x] finetune samples
[x] report back any finetune decisions and loop points
[x] final sample audition

First issue: despite the name, **Steinway** is *not* a piano sample. It's some sort of guitar by the sound of it. I've found a replacement: **ST-01/RingPiano**. I'd like you to analyse and confirm the default volume for **RingPiano**.

---

You're correct about `Steinway`. We should remove it from the set and substitute **ST-01/RingPiano**. The filename has finally managed to describe the instrument. Progress.

I've analysed the actual `RingPiano` file from your uploaded ST-01 archive:

| Property                   |   RingPiano |
| -------------------------- | ----------: |
| Size                       | 9,900 bytes |
| Peak                       |   127 / 128 |
| Overall RMS                |       39.10 |
| 1st-quarter RMS            |       68.01 |
| 2nd-quarter RMS            |       29.48 |
| 3rd-quarter RMS            |       22.82 |
| 4th-quarter RMS            |        9.95 |
| Recommended default volume |    **`30`** |
| Loop recommendation        |      **No** |

The envelope is strongly piano-like in structural terms: a very pronounced attack followed by a continuous decay:

**68.01 → 29.48 → 22.82 → 9.95 RMS**

It also reaches almost full 8-bit amplitude, with a peak of `127`, so there is no reason to compensate with an unusually high instrument volume.

I recommend **default volume `30` hex (48 decimal)**.

That's deliberately below ProTracker's maximum `40`. At `30`, RingPiano retains a strong presence while leaving useful headroom for the kick/snare and, importantly, for volume shaping within patterns. Since this is our principal melodic instrument, I'd rather start at `30` and make occasional notes louder than establish `40` as its normal state and leave ourselves nowhere to go. The laws of dynamics remain inconvenient even with only 64 possible volume levels.

I would also **not loop RingPiano**. Its natural decay is useful musical information, and the final quarter is already down to about 15% of the RMS energy of the attack. Looping that tail would work against the crisp, jaunty piano articulation we're after.

So the revised slot is:

**`01` — ST-01/RingPiano — main piano — default volume `30` — unlooped**

This replaces `Steinway` outright.

---

All good so far. Here are the promised finetune values. I'm not sure if you can use them in any way but they're here for posterity. 
 
``` 
  - id: 1 
    name: ST-01/RingPiano 
    finetune: 0x0  # 0 or +1 
  - id: 2 
    name: ST-01/PanFlute 
    finetune: 0xe  # -2 or -3 
  - id: 3 
    name: ST-01/SoftBass 
    finetune: 0xf 
  - id: 7 
    name: ST-01/Strings7 
    finetune: 0x2  # +2 to +4 
    start: 0x00f0   # loop start
    length: 0x25bc   # loop length
``` 

Optional adjustments provided as a comment on the finetune line.

---

Those are useful. They remove the tuning uncertainty from Step 2 and give us one authoritative loop definition as well.

I'll record the pitched samples as:

| Slot | Sample            | Base finetune | Acceptable adjustment | Loop                        |
| ---- | ----------------- | ------------: | --------------------- | --------------------------- |
| `01` | `ST-01/RingPiano` |           `0` | `0` or `+1`           | None                        |
| `02` | `ST-01/PanFlute`  |           `e` | `-2` or `-3`          | None currently              |
| `03` | `ST-01/SoftBass`  |           `f` | —                     | None                        |
| `07` | `ST-01/Strings7`  |           `2` | `+2` to `+4`          | Start `00f0`, length `25bc` |

In ProTracker's 4-bit signed finetune representation, that means `e` corresponds to **−2** and `f` to **−1**, while `2` is **+2**. So the supplied base values are internally consistent.

The `Strings7` information is particularly valuable. We no longer need to hunt blindly for a loop: **start `00f0`, length `25bc`** becomes our initial audition setting. Since the bootstrap says exact loop points and finetunes ultimately defer to the auditioned project files, we can adjust those later if your ears disagree with the historical settings. 

I'll use these values from here onward, including the optional ranges as **audition alternatives rather than uncertainty about the base setting**.

Current Slot `01` is therefore firmly:

**`RingPiano`, volume `30`, finetune `0`, unlooped.**

One correction to my earlier work also follows from your data: my claim that we couldn't establish historical finetunes is now obsolete. We can stop asking the internet to remember things you've supplied directly, which is generally an improvement.

---

Finally to the sample audition. I've passed them all. I had to make significant adjustments to the volumes to make sure everything was audible in the test pattern. Here are the instrument data I ended up with:

```
```

---

It looks like the instrument data got eaten by the Markdown gods. The message contains an opening code fence, but no actual data.

Please paste the instrument block again. Once it's here, I'll treat your auditioned **volumes, finetunes, and loop settings as authoritative**, per the bootstrap's source-of-truth hierarchy. 

---

Yeah, I wasn't expecting the opening code fence to get eaten straight away. Let me try again.

```
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
    # possibly loop but probably no
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
  - id: 8
    source: st01
    name: ST-01/PingBells
    volume: 0x38
```

---

That came through intact. These audition results now supersede my analytical volume recommendations. Per the bootstrap, the auditioned project settings are authoritative for exact sample volumes, loop points, finetunes, and by-ear edits. 

So the **approved Clockwork Picnic sample set** is:

|   ID | Instrument | Volume | Finetune | Loop                        |
| ---: | ---------- | -----: | -------: | --------------------------- |
| `01` | RingPiano  |   `10` |      `0` | No                          |
| `02` | PanFlute   |   `10` |      `e` | No, provisionally           |
| `03` | SoftBass   |   `40` |      `f` | No                          |
| `04` | BassDrum3  |   `28` |        — | No                          |
| `05` | Snare1     |   `2c` |        — | No                          |
| `06` | CloseHiHat |   `40` |        — | No                          |
| `07` | Strings7   |   `20` |      `2` | Start `00f0`, length `25bc` |
| `08` | PingBells  |   `38` |        — | No                          |

The volume changes are substantial but quite believable in context. In particular, **RingPiano and PanFlute at `10`** tell us their raw amplitudes aren't representative of how prominently they actually sit perceptually in the four-channel mix. Conversely, **SoftBass and CloseHiHat at `40`** need all the help available. This is exactly why auditioning the combined set matters more than normalising waveforms on paper. Computers measure amplitude beautifully and remain stubbornly mediocre at having ears.

I'd preserve the optional tuning notes as annotations rather than bake them into the current settings: RingPiano `0` with `+1` available; PanFlute `e` with `d` worth trying; Strings7 `2` with `3`–`4` available. Likewise, PanFlute remains **unlooped unless later composition exposes a genuine need for sustained notes**.

That completes the substantive requirements of **Step 2**: eight samples selected, actual envelopes considered, default volumes established by audition, finetunes established, Strings7's forward loop established, practical ranges considered, and the complete set auditioned and accepted. 

We can therefore move to **Step 3: write the structural arc and motif map**, with *Clockwork Picnic* itself serving as the narrative and thematic seed. 

---

Proceed.

---

Now we can do Step 3 properly. The bootstrap says the structural arc should grow from the title and guide both pattern construction and later pattern reuse. Each motif should have a distinct musical character, with patterns formed by recombining those motifs. 

For **Clockwork Picnic**, I'd interpret the title as two interacting musical ideas: **clockwork** gives us precise little mechanisms, repeated figures, interlocking rhythms and deliberate pattern reuse; **picnic** supplies warmth, melody, playfulness and the sense that none of this machinery takes itself terribly seriously. The PanFlute section introduces the slight strangeness already requested by the brief.

### Structural arc

I propose six broad sections:

**I. Winding the Clock**
A compact opening that assembles the tune piece by piece. Start with a small RingPiano figure and mechanical percussion rather than immediately presenting everything. Bass enters, then the complete groove snaps into place. It should feel like a title screen waking up.

**II. The Picnic Sets Off**
The main RingPiano theme arrives in full. Bright, memorable and rhythmically nimble rather than virtuosic. Bass and percussion establish the tune's characteristic bounce, while PingBells provide occasional punctuation. This is the material we want the listener unconsciously waiting to hear again.

**III. Clockwork Games**
Reuse the established material but recombine it. The melody can fragment into shorter piano phrases while Strings7 and PingBells become more active. Bass/drum patterns inherited from Section II should appear underneath altered melodic patterns. This is where the order list begins doing real compositional work instead of merely counting upward like an accountant.

**IV. The Strange Little Wood**
The requested two-pattern PanFlute solo. The energy drops without stopping the tune. Strings7 becomes important here, with SoftBass providing restrained motion underneath. Percussion thins considerably. The harmony can become slightly wistful or ambiguous, but this should remain recognisably part of *Clockwork Picnic*, not suddenly turn into *Funeral in a Swamp*.

The two solo patterns should form a genuine pair: the first poses an idea, the second develops and resolves it.

**V. Back to the Picnic**
A brisk transition brings the RingPiano theme back. Crucially, this should reuse earlier patterns rather than require an entirely rewritten reprise. The listener now hears familiar material differently because of the PanFlute excursion. One or two strategically altered patterns can increase the energy toward the ending.

**VI. The Clock Springs Loose**
The coda. Rather than fading or simply playing the tonic chord, the established mechanical motifs progressively misbehave: compressed piano fragments, PingBell answers, bass punctuation and a final coordinated flourish. The last few rows should sound deliberately composed as an ending. The bootstrap explicitly requires a definite, interesting coda rather than a fade. 

### Motif map

I'd establish six reusable motifs.

**Motif A: The Picnic Tune**
RingPiano. A jaunty, syncopated melodic cell with a clear upward gesture followed by a cheeky downward answer. This becomes the melodic DNA of the main theme. It should be simple enough to recognise after only a few notes and capable of fragmentation, transposition and rhythmic displacement.

**Motif B: The Clockwork Step**
SoftBass + BassDrum3. A short alternating bass figure tightly coupled to the kick. Rather than continuous eighth notes, use strategically placed gaps so the groove seems to "tick". This should survive underneath several otherwise different patterns and become one of our principal reuse mechanisms.

**Motif C: The Cutlery Rattle**
CloseHiHat + Snare1. A light, asymmetric percussion figure. Hats provide the small mechanical subdivisions; snare accents give it bounce. Variants can omit hats or shift a snare without requiring a wholly different rhythmic identity.

**Motif D: The Glint**
PingBells. Sparse two- or three-note punctuation, usually answering rather than doubling the piano. It represents the little metallic part of the clockwork world. Because PingBells is at volume `38`, restraint matters. One well-placed bell is charming. Thirty-two of them constitute an industrial accident.

**Motif E: The Long Grass**
Strings7. Sustained harmonic support, generally appearing underneath transitions and the PanFlute section rather than throughout the main theme. Its forward loop makes it our natural long-duration voice. It can also bridge sections while other channels change function.

**Motif F: The Woodwind Question**
PanFlute. A longer-breathed, more legato phrase contrasting deliberately with Motif A. Its melodic contour should contain a subtle reference to the main piano motif, probably by preserving a characteristic interval while slowing or reversing its direction. That prevents the solo from sounding pasted in.

This gives us useful recombination possibilities without demanding endless unique material:

| Section | Dominant motifs                         | Character           |
| ------- | --------------------------------------- | ------------------- |
| Winding | B, C, fragments of A/D                  | Assembly            |
| Picnic  | A + B + C, occasional D                 | Main identity       |
| Games   | A fragments + B + C + D/E               | Recombination       |
| Wood    | F + E + restrained B/C                  | Haunting contrast   |
| Return  | A + B + C + D                           | Recognition/release |
| Coda    | fragments A/B/D, final ensemble gesture | Clockwork breakdown |

There is also an important four-channel consequence. These aren't six simultaneous layers. They're **roles that migrate between channels**. A typical main-theme pattern might allocate RingPiano / RingPiano-or-PingBell / SoftBass / drums, while the woodwind section might become PanFlute / Strings7 / SoftBass / sparse drums. That keeps the arrangement genuinely tracker-like rather than designing eight imaginary channels and subsequently discovering, with characteristic human surprise, that ProTracker only supplied four. The four-channel constraint is explicit in the bootstrap. 

I would also resist creating the order list yet. The structural arc tells us **what needs to happen**, but we haven't written enough actual musical material to know exactly which pattern deserves repetition, which deserves a variant, and where a reused pattern produces the best transition. We should let the eventual order list exploit the patterns rather than designing patterns merely to fill a predetermined sequence.

With this, **Step 3 is complete**: *Clockwork Picnic* now has a structural narrative and six motifs that can drive pattern creation and reuse.

And the bootstrap explicitly asks for one final housekeeping action at this point: **now is a good time to generate an updated bootstrap Markdown file** containing everything we've locked down so far. 

---

Summarize our progress into a single, comprehensive Bootstrap Markdown File.

Include:
1. Current Goal & Next 3 Steps;
2. State of Play (key logic, architecture and/or decisions);
3. Dependency Map & Version Log;
4. 'Golden' Code Blocks (latest working logic);
5. Tested & Passing Status Confirmation.

Do not include previous attempts.

---

(increased to High for this response, decreased to Instant immediately after)

Done. I consolidated the current authoritative state, included the requested five sections, and omitted superseded attempts and rejected settings.

---

I believe the appropriate phrase at this point would be: "Take it away, Maestro".

---

Precisely.

**Take it away, Maestro.**

Bootstrap locked. Instruments auditioned. Motifs established. Four channels standing by, each already resentful about the lack of elbow room.

Next comes the part where *Clockwork Picnic* stops being project documentation and starts becoming music: **the initial pattern inventory, followed by the opening and main-theme patterns in compiler-ready 64-row format.**

---

Proceed.

---

Then we compose.

I’m going to establish a deliberately small pattern inventory first, then write **pattern `00` and pattern `01`**. Pattern `00` winds the mechanism up; pattern `01` is the first complete statement of the Picnic Tune. These become the musical vocabulary against which later variants can be judged.

The initial inventory is:

| Pattern | Role                              | Expected reuse |
| ------- | --------------------------------- | -------------- |
| `00`    | Winding the Clock / introduction  | Once           |
| `01`    | Main theme A                      | Heavy          |
| `02`    | Main theme B / answer             | Heavy          |
| `03`    | Clockwork Games A                 | Moderate       |
| `04`    | Clockwork Games B                 | Moderate       |
| `05`    | Transition into wood              | Once or twice  |
| `06`    | PanFlute solo A                   | Once           |
| `07`    | PanFlute solo B                   | Once           |
| `08`    | Reprise lift / main-theme variant | Moderate       |
| `09`    | Coda setup                        | Once           |
| `0a`    | Final flourish                    | Once           |

Eleven patterns gives us plenty of room for an interesting 85–105 second order list while still making reuse structural rather than cosmetic.

A couple of conventions before the rows begin:

* `--- 00 000` means an empty channel.
* `000` means no effect.
* `F84` on row `00` of pattern `00` sets the ProTracker tempo to **`84` hex = 132 BPM**. Because `84 >= 20` hex, `F84` sets tempo rather than speed. Speed remains `06`.
* Percussion is initially triggered at `C-4`. We can alter those fixed pitches after hearing the compiled result.
* The opening deliberately leaves space. Four-channel tracker writing benefits from resisting the apparently irresistible human urge to fill every available box.

### Pattern `00` — Winding the Clock

This introduces Motif A in fragments, then B and C progressively. The full four-channel mechanism only arrives in the second half.

| RR | CH1        | CH2        | CH3        | CH4        |
| -- | ---------- | ---------- | ---------- | ---------- |
| 00 | C-4 01 F84 | --- 00 000 | --- 00 000 | --- 00 000 |
| 01 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 02 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 03 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 04 | E-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 05 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 06 | G-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 07 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 08 | A-4 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 09 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 0a | G-4 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 0b | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 0c | E-4 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 0d | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 0e | D-4 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 0f | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 10 | C-4 01 000 | --- 00 000 | C-4 03 000 | C-4 04 000 |
| 11 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 12 | --- 00 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 13 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 14 | E-4 01 000 | --- 00 000 | G-4 03 000 | C-4 05 000 |
| 15 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 16 | G-4 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 17 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 18 | A-4 01 000 | --- 00 000 | A-4 03 000 | C-4 04 000 |
| 19 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 1a | --- 00 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 1b | G-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 1c | E-4 01 000 | --- 00 000 | G-4 03 000 | C-4 05 000 |
| 1d | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 1e | D-4 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 1f | G-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 20 | C-5 01 000 | --- 00 000 | C-4 03 000 | C-4 04 000 |
| 21 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 22 | G-4 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 23 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 24 | E-4 01 000 | --- 00 000 | G-4 03 000 | C-4 05 000 |
| 25 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 26 | G-4 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 27 | A-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 28 | C-5 01 000 | E-5 08 000 | A-4 03 000 | C-4 04 000 |
| 29 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 2a | --- 00 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 2b | B-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 2c | A-4 01 000 | --- 00 000 | G-4 03 000 | C-4 05 000 |
| 2d | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 2e | G-4 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 2f | E-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 30 | F-4 01 000 | --- 00 000 | F-4 03 000 | C-4 04 000 |
| 31 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 32 | A-4 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 33 | C-5 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 34 | A-4 01 000 | --- 00 000 | C-5 03 000 | C-4 05 000 |
| 35 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 36 | G-4 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 37 | F-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 38 | E-4 01 000 | G-4 08 000 | G-4 03 000 | C-4 04 000 |
| 39 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 3a | D-4 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 3b | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 3c | G-4 01 000 | --- 00 000 | G-4 03 000 | C-4 05 000 |
| 3d | A-4 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 3e | B-4 01 000 | D-5 08 000 | --- 00 000 | C-4 05 000 |
| 3f | G-4 01 000 | --- 00 000 | B-4 03 000 | C-4 06 000 |

The important feature is row `20`: that's where the opening stops introducing components and begins behaving like a proper four-channel arrangement. PingBells first appear at `28`, late enough that their colour feels like a reward rather than wallpaper.

### Pattern `01` — The Picnic Tune A

Now the main motif gets an uninterrupted 64-row statement. The harmony is intentionally straightforward: broadly C major, moving through F and G territory, because rhythmic personality and tracker voicing should carry more of the character than gratuitous harmonic cleverness.

| RR | CH1        | CH2        | CH3        | CH4        |
| -- | ---------- | ---------- | ---------- | ---------- |
| 00 | C-5 01 000 | --- 00 000 | C-4 03 000 | C-4 04 000 |
| 01 | --- 00 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 02 | E-5 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 03 | G-5 01 000 | --- 00 000 | G-4 03 000 | --- 00 000 |
| 04 | E-5 01 000 | --- 00 000 | --- 00 000 | C-4 05 000 |
| 05 | D-5 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 06 | C-5 01 000 | --- 00 000 | G-4 03 000 | C-4 06 000 |
| 07 | G-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 08 | A-4 01 000 | C-5 08 000 | A-4 03 000 | C-4 04 000 |
| 09 | C-5 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 0a | E-5 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 0b | --- 00 000 | --- 00 000 | E-5 03 000 | --- 00 000 |
| 0c | D-5 01 000 | --- 00 000 | --- 00 000 | C-4 05 000 |
| 0d | C-5 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 0e | A-4 01 000 | --- 00 000 | E-5 03 000 | C-4 06 000 |
| 0f | G-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 10 | F-4 01 000 | --- 00 000 | F-4 03 000 | C-4 04 000 |
| 11 | A-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 12 | C-5 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 13 | A-4 01 000 | --- 00 000 | C-5 03 000 | --- 00 000 |
| 14 | G-4 01 000 | --- 00 000 | --- 00 000 | C-4 05 000 |
| 15 | F-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 16 | A-4 01 000 | --- 00 000 | C-5 03 000 | C-4 06 000 |
| 17 | C-5 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 18 | D-5 01 000 | F-5 08 000 | G-4 03 000 | C-4 04 000 |
| 19 | B-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 1a | G-4 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 1b | A-4 01 000 | --- 00 000 | D-5 03 000 | --- 00 000 |
| 1c | B-4 01 000 | --- 00 000 | --- 00 000 | C-4 05 000 |
| 1d | D-5 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 1e | C-5 01 000 | --- 00 000 | G-4 03 000 | C-4 06 000 |
| 1f | G-4 01 000 | --- 00 000 | B-4 03 000 | --- 00 000 |
| 20 | C-5 01 000 | --- 00 000 | C-4 03 000 | C-4 04 000 |
| 21 | E-5 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 22 | G-5 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 23 | E-5 01 000 | --- 00 000 | G-4 03 000 | --- 00 000 |
| 24 | D-5 01 000 | --- 00 000 | --- 00 000 | C-4 05 000 |
| 25 | C-5 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 26 | E-5 01 000 | G-5 08 000 | G-4 03 000 | C-4 06 000 |
| 27 | G-4 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 28 | A-4 01 000 | --- 00 000 | A-4 03 000 | C-4 04 000 |
| 29 | C-5 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 2a | E-5 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 2b | A-5 01 000 | --- 00 000 | E-5 03 000 | --- 00 000 |
| 2c | G-5 01 000 | E-5 08 000 | --- 00 000 | C-4 05 000 |
| 2d | E-5 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 2e | D-5 01 000 | --- 00 000 | E-5 03 000 | C-4 06 000 |
| 2f | C-5 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 30 | F-5 01 000 | --- 00 000 | F-4 03 000 | C-4 04 000 |
| 31 | E-5 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 32 | C-5 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 33 | A-4 01 000 | --- 00 000 | C-5 03 000 | --- 00 000 |
| 34 | C-5 01 000 | A-4 08 000 | --- 00 000 | C-4 05 000 |
| 35 | D-5 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 36 | E-5 01 000 | --- 00 000 | C-5 03 000 | C-4 06 000 |
| 37 | C-5 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 38 | D-5 01 000 | --- 00 000 | G-4 03 000 | C-4 04 000 |
| 39 | G-5 01 000 | --- 00 000 | --- 00 000 | --- 00 000 |
| 3a | F-5 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 3b | D-5 01 000 | --- 00 000 | B-4 03 000 | --- 00 000 |
| 3c | B-4 01 000 | D-5 08 000 | --- 00 000 | C-4 05 000 |
| 3d | G-4 01 000 | --- 00 000 | --- 00 000 | C-4 06 000 |
| 3e | B-4 01 000 | --- 00 000 | G-4 03 000 | C-4 05 000 |
| 3f | G-4 01 000 | --- 00 000 | B-4 03 000 | C-4 06 000 |

There are several intentional decisions here.

The **RingPiano carries almost everything melodic**. Channel 2 is kept mostly empty and gets only occasional PingBell responses. That preserves the bells as Motif D rather than turning them into a second melody.

The **SoftBass is more mobile than a conventional root-note bass**. Because its auditioned volume is `40`, it should give those off-beat entries considerable definition. Its line also repeatedly uses fifths and approach notes, which should provide movement without consuming another harmony channel.

The percussion is deliberately skeletal: kick, hat and snare share Channel 4. The basic vocabulary is established strongly enough that later patterns can alter it and have the listener perceive the difference.

Most importantly, pattern `01` contains a recognisable four-part melodic architecture rather than sixty-four unrelated notes:

**rows `00–0f`: statement**
**rows `10–1f`: answer**
**rows `20–2f`: elevated restatement**
**rows `30–3f`: turnaround**

That internal organisation matters because pattern `02` can now answer the *idea* rather than merely provide another minute quantity of tracker data.

These two patterns are ready for the first compiled audition. **Pattern `00` should lead directly into `01`; pattern `01` should be allowed to repeat once during testing.** The things worth listening for are whether the main motif is memorable after two hearings, whether `RingPiano` at `10` remains sufficiently forward, whether SoftBass at `40` overwhelms it, and whether the percussion pitches actually sound like a coherent kit at `C-4`.

I would not compose `02` until those two have survived that audition. We now have actual musical assumptions worth testing, and piling ten more patterns on top before hearing them would merely allow mistakes to reproduce.

