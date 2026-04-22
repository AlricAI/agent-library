# Interaction And Lasso

> `hyper-scatter` separates renderer state from input handling.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Interaction and Lasso

`hyper-scatter` separates renderer state from input handling.

- The renderer owns view math, hit testing, lasso selection, and emphasis rendering.
- The 2D `createInteractionController()` helper wires common DOM input patterns to a `Renderer`.
- 3D input handling is currently host-managed.

## 2D Interaction Controller

```ts
import { createInteractionController } from "hyper-scatter";

const controller = createInteractionController(canvas, plot, {
  lassoPredicate: (event) => event.shiftKey,
  onHover: (hit) => {
    console.log(hit?.index ?? null);
  },
  onLassoUpdate: (_dataPolygon, screenPolygon) => {
    plot.setLassoPolygon(screenPolygon);
    plot.render();
  },
  onLassoComplete: (result, _dataPolygon, screenPolygon) => {
    plot.setLassoPolygon(screenPolygon);
    if (result.kind === "indices" && result.indices) {
      plot.setSelection(result.indices);
      plot.setInactiveOpacity(result.indices.size > 0 ? 0.35 : 1);
    }
    plot.render();
  },
});
```

Supported controller options:

- `observeResize`: keep renderer size in sync with the canvas using `ResizeObserver`
- `wheelZoomScale`: customize wheel-to-zoom sensitivity
- `lassoPredicate`: choose the gesture that enters lasso mode
- `lassoMinSampleDistPx`: screen-space point sampling threshold while dragging
- `lassoMaxVertsInteraction`: polygon simplification budget during drag
- `lassoMaxVertsFinal`: polygon simplification budget on completion
- `onHover`: hover callback after hit testing
- `onLassoUpdate`: callback during drag with both data-space and screen-space polygons
- `onLassoComplete`: callback with the final `SelectionResult`

Default lasso gesture:

- `Shift` + `Meta` drag
- `Shift` + `Ctrl` drag

If you want `Shift`-drag instead, override `lassoPredicate`.

## Emphasis States

The renderer has three emphasis channels:

- `setSelection(indices)` for the primary active subset
- `setHighlight(indices)` for secondary emphasis such as neighbors or search hits
- `s

*[truncated — see source for full prompt]*