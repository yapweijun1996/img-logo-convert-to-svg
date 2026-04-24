# img-logo-convert-to-svg

A browser-only tool for converting simple PNG/JPG logo images into SVG files.

The app runs as a single static `index.html` file. There is no backend, database, API key, CDN dependency, or server upload.

## Current MVP

- Upload PNG, JPG, or JPEG logo images
- Reject unsupported file types, including WEBP for V1
- Reject files larger than 5 MB
- Preview the original image
- Convert the image locally with Canvas
- Adjust threshold before converting
- Preview the generated SVG
- Copy SVG markup
- Download SVG
- Export SVG with common display sizes
- Reset the page state

## Run Locally

Open `index.html` directly in a modern browser.

No install step is required.

## Export Sizes

The export size selector changes the SVG `width` and `height` attributes while preserving the `viewBox`.

Common sizes:

- Original traced size
- 16 px longest side
- 32 px longest side
- 48 px longest side
- 64 px longest side
- 128 px longest side
- 256 px longest side
- 512 px longest side
- 1024 px longest side

SVG file size may stay nearly the same across export sizes because the path data remains the main file-size driver. For example, a 128 x 128 SVG and a 512 x 512 SVG can both be around the same KB size if they contain the same paths.

## Limits

This MVP is best for simple, high-contrast logos and single-color marks. It is not intended to perfectly vectorize photos, gradients, shadows, or detailed illustrations.

## Documentation

- [MVP Scope](docs/mvp.md)
- [Export Sizes](docs/export-sizes.md)
- [Testing Checklist](docs/testing.md)
