# Revised architecture

The revised channel architecture should be:

Channel	Primary responsibility
1	Piano right hand: melody, upper chord tones, occasional dyads implied through rapid but natural articulation
2	Bass / PingBells / Strings / selected percussion
3	Drums / Bass / Strings / PanFlute support as required
4	Piano left hand: bass notes, fifths, chordal support, cadential movement

Channel 4 therefore becomes permanently reserved for the pianist's left hand whenever piano is present. That is a much stronger organising principle.

There is one important wrinkle: ProTracker gives us one note per channel at a time, so we cannot literally play conventional three- and four-note piano chords. Instead, we'll create the perception of two-handed piano playing through voicing and grouping. Right-hand notes should occur in phrases, with longer note values, rests and repeated rhythmic shapes. The left hand can land roots, fifths and occasional passing tones at harmonically meaningful points. Together, Channels 1 and 4 can imply chords convincingly without machine-gunning chord tones.

The main melody should also slow substantially. At speed 06 / BPM 84, I want the ordinary melodic unit to become roughly the quarter-note and eighth-note level, with sixteenth-like tracker movement reserved for ornaments, pickups and short flourishes. A phrase might breathe something like this conceptually:

RH:  C-5 .... E-5 .... G-5 ........ | E-5 .... D-5 .... C-5 ........
LH:  C-4 ............ G-4 .......... | C-4 ............ G-4 ..........

rather than the previous:

RH: C-5 .. E-5 G-5 E-5 D-5 C-5 G-4 ...

That distinction is central. The first sounds like somebody sitting at a keyboard. The second sounds like a tracker composer discovering that empty rows don't consume disk space and becoming frightened of them.

I also want to revise the structural inventory. We no longer need to squeeze the piece into eleven patterns:

Pattern group	Purpose
00	Piano introduction, genuinely spacious
01–02	Main theme, phrase A + phrase B
03–04	Main theme continuation/development
05–06	Clockwork Games
07	Transition / preparation
08–09	PanFlute solo
0a	Transition back
0b–0c	Piano reprise, substantially reused material
0d	Reprise lift / development
0e	Coda setup
0f	Final flourish

That's 16 available patterns, though some may ultimately prove unnecessary. More importantly, a musical thought is now allowed two patterns where one previously had to do everything. Runtime can exceed 105 seconds if necessary. The original bootstrap already makes exact runtime subordinate to musical flow, authenticity and compatibility.

There is also a useful orchestration consequence. SoftBass no longer has to play constantly. During piano-dominant passages, Channel 4's left hand can supply the bass register and Channel 2 can carry sparse percussion or PingBells while Channel 3 handles the rest of the kit. When SoftBass enters, it can feel like an arrangement change rather than permanent furniture.

For example:

PIANO-LED PASSAGE

CH1  RingPiano RH
CH2  HiHat / PingBells
CH3  Kick + Snare
CH4  RingPiano LH

Then:

FULL BAND PASSAGE

CH1  RingPiano RH
CH2  SoftBass
CH3  combined drum kit
CH4  RingPiano LH

And the PanFlute section can redistribute completely:

WOODWIND PASSAGE

CH1  PanFlute
CH2  Strings7
CH3  sparse drums / SoftBass
CH4  RingPiano LH or sparse piano accompaniment

I particularly like retaining piano left hand underneath parts of the PanFlute solo. It means the human pianist doesn't mysteriously evaporate when the woodwind appears, and it gives us a way to connect Motif F to the rest of the piece.

One other change follows from your feedback: the RingPiano's natural decay needs to become part of the composition. We should allow notes enough time to ring. Repeated notes should usually represent actual rhythmic intention, not compensate for decay. Phrases need breathing spaces, and cadences need room to land.

So the new governing rule for the piano writing is:

Compose something a competent human pianist could plausibly perform with two hands first; encode that performance into two tracker channels second.

That should produce a markedly different Clockwork Picnic.
