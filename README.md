# p5-genetic-painter

> Evolve a painting from a photo: a genetic algorithm breeds brush strokes — colour, position, curve, pressure — and scores each generation on the actual painted pixels, rendered with p5.brush.

## How it works

The genome is a set of brush strokes. Each stroke carries genes for colour, start and end location, curve, width, pressure, opacity, and a random seed. Evolution hill-climbs one challenger at a time: a mutated genome is painted, scored against the source image, and kept only if it matches better.

Crucially, fitness is measured on the **p5.brush output itself** — every candidate is brushed onto a small fitness canvas with p5.brush and scored on those actual pixels (pixel error plus an edge term), so what you see is literally what was scored. There is no proxy renderer. Renders are seeded, so a genome always paints identically.

- **Stroke bounds:** widths and lengths are clamped to a realistic brush range, and evolution picks the size.
- **Adaptive growth:** when the match stagnates, new finer strokes are added to the genome over time.
- **Fitness chart:** full run history, up to 20,000 generations.
- **Sources:** three built-in images, or upload your own photo.
- **Download:** paint the champion at 1024px as a PNG.

## Run it

Live at https://adamstirtan.github.io/p5-genetic-painter/ (GitHub Pages serves the `docs/` folder), or open `docs/index.html` in a browser (WebGL2 required). The app is a single self-contained file.

## Credits

Brush rendering by [p5.brush](https://github.com/acamposuribe/p5.brush) by Alejandro Campos (MIT licensed), vendored into the page.

## License

MIT — see [LICENSE](LICENSE).
