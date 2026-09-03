# Sample map

## Initial thoughts

Piano: primary melodic voice and the defining instrument of Clockwork Picnic.

Oboe/woodwind substitute: haunting contrasting solo voice for the specified two-pattern feature.

Bass: short, articulate bass suitable for active tracker basslines.

Kick: compact, punchy bass drum.

Snare: crisp snare that remains intelligible against piano.

Hi-hat/percussion: rhythmic subdivision without consuming much sonic space.

Sustained harmonic voice: likely strings or another economical loopable texture.

Character/percussion voice: a distinctive bell, mallet, pluck or similar sound for the little mechanical flourishes implied by Clockwork Picnic.

## Samples

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

## Envelope

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

## Finetune

Currently all zeros. No historical data found. Use Steinway as the zero level sample.
