# ASCII Pattern Generator

A single-file, dependency-free tool for generating grid-based glyph patterns in the browser. Think ASCII-art-adjacent textures: fields of dots, crosses, rings and squares arranged in blocky clusters, organic scatters or uniform grids.

![Example output: neon green glyphs clustered in rectangular blocks on black](https://raw.githubusercontent.com/definegravity/ascii-pattern-generator/main/example.png)

## Use it

Open `index.html` in any modern browser. That's it. No build step, no dependencies.

## Controls

| Group | Control | What it does |
|---|---|---|
| Icons | Glyph toggles | Choose which glyphs appear in the pattern |
| Icons | Custom SVG | Paste one or more `<svg>` elements to add your own glyphs |
| Layout | Cell size | Grid resolution: smaller cells give a finer pattern |
| Layout | Icon scale | How much of each cell a glyph fills |
| Layout | Size jitter | Random per-cell size variation |
| Density | Fill | How many cells are filled overall |
| Density | Distribution | Uniform scatter, Clustered (smooth noise blobs) or Blocky (quantised rectangular clusters) |
| Density | Block size | Blocky mode: cells per block |
| Density | Solid blocks | Blocky mode: chance a dense block renders as a flat slab |
| Density | Icon mix | Blocky mode: glyph variety within each block |
| Density | Cutouts | Blocky mode: organic voids carved across the blocks |
| Canvas | Width, height, ink, ground | Output dimensions and colours |
| Seed | Seed, shuffle | Reproducible randomness |

Every slider has an editable number field next to it.

## Custom glyphs

Paste full `<svg>` tags into the Custom SVG box. Use `fill="currentColor"` (or leave paths unstyled) and your glyphs inherit the ink colour like the built-in set.

## Export

Copy the SVG to your clipboard, or download it as SVG or PNG (2x resolution).

## How it works

A seeded PRNG (mulberry32) and a value-noise field drive all placement, so the same seed always reproduces the same pattern. Blocky mode quantises the noise per block of cells into four levels (empty, sparse, dense, solid), gives each block its own small glyph palette with a dominant glyph, and layers a second smooth noise field on top as an organic cutout mask.
