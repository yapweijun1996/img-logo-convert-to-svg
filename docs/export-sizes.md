# Export Sizes

## How It Works

SVG is vector-based. The app keeps the original traced coordinate system in the `viewBox`, then changes only the exported `width` and `height`.

Example:

```svg
<svg viewBox="0 0 512 256" width="128" height="64">
```

This means the same SVG shape can display at different sizes without changing the underlying path data.

## Common Sizes

- Original traced size
- 16 px longest side
- 32 px longest side
- 48 px longest side
- 64 px longest side
- 128 px longest side
- 256 px longest side
- 512 px longest side
- 1024 px longest side

The app uses longest-side scaling to preserve aspect ratio. A wide logo exported at 512 px longest side may become `512 x 256`, not `512 x 512`.

## Why File Size Can Stay The Same

Changing SVG display size usually changes only a few characters in `width` and `height`.

The main file-size driver is the `<path d="...">` data. If the path data is the same, `128 x 128` and `512 x 512` downloads can have nearly identical file sizes.

To make smaller SVG files, the app needs path simplification, lower processing resolution, or SVG optimization.

## When To Use PNG Instead

Use PNG export when the requirement is fixed raster pixels and naturally different file sizes per dimension. PNG export is not included in V1.
