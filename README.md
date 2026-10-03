# Bassline Lab

A Max for Live MIDI effect that generates techno, electro, and acid basslines. Create MIDI clips in Session or Arrangement View, or export a standard `.mid` file.

**[Download Bassline Lab.amxd](Bassline%20Lab.amxd?raw=true)**

## Requirements

- Ableton Live with Max for Live enabled.
- Developed with Ableton Live 12.4.6 and its bundled Max 9.1.5 on macOS. Compatibility with earlier versions and Windows has not been verified.
- A MIDI instrument on the same track to hear the generated notes.

The device is frozen with its JavaScript embedded. Only `Bassline Lab.amxd` is needed; no separate scripts or third-party Max objects are required.

## Quick start

1. Download `Bassline Lab.amxd` using the link above.
2. Drag it onto a MIDI track in Live, before a bass instrument.
3. Choose a **Style**, **Root**, **Scale**, and **Register**.
4. Set **Bars (4/4)** and adjust the rhythm controls.
5. Click **GENERATE** to choose a new seed and preview a pattern.
6. Click **NEW_CLIP**, **ARRANGE**, or **EXPORT_MIDI** to output the pattern.

The preview bars show note velocities across the pattern. Generation updates the preview; play the resulting MIDI clip in Live to hear it through your instrument.

## Output options

### Session View

Click **NEW_CLIP** to create a looping MIDI clip in the first empty Session slot on the track containing the device. If every slot is occupied, add an empty scene and try again.

### Arrangement View

1. Set **Start bar (4/4)** to the desired position. Bar numbering starts at **1**; the default is **5**.
2. Click **ARRANGE**.
3. The device creates a MIDI clip on its own track and switches Live to Arrangement View.

For example, **Start bar = 5** and **Bars = 4** fills bars **5-8**, ending at the start of bar **9**. Set the next start bar to **9** to place another pattern directly after it.

The device checks the destination range for existing clips. If they overlap, it displays `Range occupied. Choose another Start bar.` and leaves those clips intact. The start bar does not advance automatically.

All positions and lengths use a fixed **4/4 grid**, regardless of the Live Set's time signature. Use a 4/4 Set for the bar numbers to match Live's timeline.

### MIDI file

Click **EXPORT_MIDI** and choose a destination. The device appends `.mid` if needed and exports the current pattern with:

- Standard MIDI File format 0, one track, MIDI channel 1.
- 480 ticks per quarter note.
- Note pitches, velocities, timing, and durations.
- The current Live tempo and a 4/4 time signature.

Exported patterns start at the beginning of the file. **Start bar (4/4)** only controls Arrangement placement.

## Controls

| Control | Range / choices | Purpose |
| --- | --- | --- |
| Style | Techno, Electro, Acid | Selects rhythmic weights, octave-jump behavior, and accents. |
| Root | C-B | Sets the tonal root. |
| Scale | Minor, Dorian, Phrygian, Minor Pent, Major | Constrains note pitches to the selected scale. |
| Register | C0 + root, C1 + root, C2 + root | Sets the base pitch range. |
| Bars (4/4) | 1-8 | Sets the pattern length. |
| Seed | 1-999999 | Reproduces a pattern when the other generation settings are unchanged. |
| Start bar (4/4) | 1-9999 | Sets the Arrangement destination. |
| Density % | 10-100 | Adjusts the likelihood of notes on the sixteenth-note grid. |
| Swing % | 0-60 | Delays alternating sixteenth notes. |
| Gate % | 10-95 | Adjusts note duration. |
| Variation % | 0-100 | Adds rhythmic and melodic changes after the first bar. |
| GENERATE | Button | Chooses a random seed and refreshes the preview. |

Changing a generation setting refreshes the preview. Output buttons use the current settings and seed, so you can create a clip and export the same pattern without pressing **GENERATE** again. Existing clips and exported files are not updated when you change the controls.

## Troubleshooting

- **No sound:** Place a MIDI instrument after Bassline Lab and play the generated clip. The device produces MIDI patterns and passes incoming MIDI through; it has no built-in synthesizer.
- **No free Session slot:** Add an empty scene on the device's track, then click **NEW_CLIP** again.
- **Arrangement range occupied:** Choose a start bar with enough empty space for the full pattern.
- **Unexpected destination track:** Both clip buttons target the track containing Bassline Lab, even if another track is selected.
- **Export failed:** Choose a writable folder and check the status message at the bottom of the device.
