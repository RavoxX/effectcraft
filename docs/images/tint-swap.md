# Tint Swap Colors captures

Original EffectCraft UI captures with a procedurally created solid. Both screenshots are
MIT OR Apache-2.0; each has an attribution sidecar and a row in `ATTRIBUTION.md`.

- `tint-swap-before.png`: upstream source at `9efe7533`. Tint has red Map Black To and blue
  Map White To, with no Swap Colors control.
- `tint-swap-after.png`: the same composition with this fix, after clicking Swap Colors.
  Both swatches and the rendered solid change.

Rendered with the `effectcraft-ui-egui` offscreen `snapshot` example, `--empty`,
`--size 1100x760`, `--scale 1`, on Linux with Vulkan llvmpipe.

The JSON-lines script for the before capture:

```jsonl
{"method":"engine.execute","params":{"command":"comp.new","params":{"name":"Tint swap","width":640,"height":360,"frameRate":30,"duration":5}}}
{"method":"engine.execute","params":{"command":"layer.newSolid","params":{"name":"Tint sample","color":"#000000","width":200,"height":120}}}
{"method":"engine.execute","params":{"command":"effect.apply","params":{"effect":"ec.color.tint"}}}
{"method":"engine.execute","params":{"command":"prop.set","params":{"path":"effects/#1/black","value":[1,0,0,1]}}}
{"method":"engine.execute","params":{"command":"prop.set","params":{"path":"effects/#1/white","value":[0,0.25,1,1]}}}
{"method":"engine.execute","params":{"command":"window.panel","params":{"panel":"effectControls"}}}
```

For the after capture, append the following step (the newly applied effect has UID 27 in
this empty-session script):

```jsonl
{"method":"ui.click","params":{"id":"effectControls.effect.27.swapColors"}}
```
