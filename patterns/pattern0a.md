## Pattern 0a — Back to the Picnic

| RR | CH1        | CH2        | CH3        | CH4        |
| -: | ---------- | ---------- | ---------- | ---------- |
| 00 | E-4 02 --- | C-4 07 --- | A-4 03 --- | A-3 01 --- |
| 08 | C-4 02 --- | --- -- --- | --- -- --- | E-3 01 --- |
| 16 | A-3 02 --- | C-4 07 --- | F-4 03 --- | F-3 01 --- |
| 24 | D-4 02 --- | B-3 07 --- | G-4 03 --- | G-3 01 --- |
| 28 | B-3 02 --- | --- -- --- | --- -- --- | --- -- --- |
| 32 | E-4 01 ED2 | G-3 01 ED1 | C-4 06 --- | C-3 01 E01 |
| 36 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 40 | E-4 01 --- | C-4 01 --- | C-4 06 --- | G-3 01 --- |
| 44 | C-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 48 | D-4 01 --- | B-3 01 --- | C-4 04 --- | G-3 01 --- |
| 52 | G-4 01 --- | --- -- --- | C-4 06 --- | --- -- --- |
| 56 | F-4 01 --- | B-3 01 --- | C-4 05 --- | G-3 01 --- |
| 60 | D-4 01 --- | B-3 01 --- | C-4 04 --- | G-3 01 --- |
| 62 | --- -- --- | --- -- --- | C-4 06 --- | --- -- --- |

The handover occurs at row `32`:

* PanFlute, Strings7, and SoftBass withdraw.
* The three-voice RingPiano texture returns.
* CH3 begins with the hi-hat.
* `E01` switches the low-pass filter off.
* `ED1` and `ED2` roll the returning C-major piano chord upward.

The final sixteen rows rebuild the rhythm section:

```text
row 48: kick returns
row 56: snare returns
row 60: dominant G chord with kick
row 62: hi-hat pickup
```

The closing piano notes form G7 colour at row `56`, followed by a plain G-major dominant at row `60`. Pattern `01` can therefore follow directly with its opening C-major chord.

For the most useful audition, run the complete boundary sequence:

```text
06, 07, 08, 09, 0a, 01
```

That tests not only the four new patterns, but whether the transition into the filtered solo and the return to the reusable main-theme block both work as intended.
