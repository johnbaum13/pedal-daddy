# Pedal Daddy

A browser pedalboard for synths and guitar: Auto-Wah, Fuzz, Chorus, Tremolo, Delay and Reverb in a chain you can reorder. Single HTML file, no build step.

**Play it:** https://johnbaum13.github.io/pedal-daddy/

## Hook up a synth (macOS + BlackHole)
1. System Settings → Sound → Output: `BlackHole 2ch`. Browser synths (Pandemonium, Pipsqueak) now flow into BlackHole.
2. Open Pedal Daddy in Chrome, press power, allow audio input, and set **Input device** to `BlackHole 2ch`.
3. Set **Output device** to your speakers or audio interface (press **Rescan** if the list is empty).
4. Play the synth in another tab.

## Reusing the pedals
The `PedalKit` script block in `index.html` is the pedal engine with no UI. Copy it into another Web Audio page:

```js
const board = PedalKit.createBoard(ctx, ['autowah','fuzz','chorus','tremolo','delay','reverb']);
synthOutput.connect(board.input);
board.output.connect(ctx.destination);
board.pedals.delay.setEnabled(true);
```
