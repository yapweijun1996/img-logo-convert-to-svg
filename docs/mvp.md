# MVP Scope

## Goal

V1 proves the private browser-only conversion loop:

```text
Upload Image -> Adjust Threshold -> Convert -> Preview -> Copy or Download
```

## Included

- Static `index.html`
- PNG/JPG/JPEG upload
- 5 MB file-size limit
- Original image preview
- Canvas-based local image processing
- Threshold control
- Basic monochrome SVG generation
- SVG preview
- SVG code display
- SVG copy
- SVG download
- Common SVG export sizes
- Reset
- Basic status and error messages

## Deferred

- WEBP upload
- Drag and drop upload
- Multi-color tracing
- SVG path editing
- PNG export
- Batch export
- Web Worker processing
- Backend storage
- User accounts
- AI logo redesign

## Privacy Rule

The uploaded image must stay in the browser. V1 must not send the file name, file bytes, pixel data, generated SVG, or analytics containing image details to a server.

## Dependency Rule

V1 must not load conversion logic from a runtime CDN. If a tracing library is added later, it should be vendored locally or bundled into the app, with license notes documented.
