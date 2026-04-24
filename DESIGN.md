
# DESIGN.md

````md
# DESIGN.md

# img-logo-convert-to-svg

## 1. Project Overview

`img-logo-convert-to-svg` is a browser-only tool that allows users to upload a logo image and convert it into an SVG file.

The tool is designed for simple logos, icons, marks, symbols, and high-contrast graphics. It is not intended to perfectly convert photos, complex gradients, shadows, or detailed illustrations.

The main goal is to make image-to-SVG conversion simple, private, and easy for non-technical users.

---

## 2. Product Goal

The product should help users:

- Upload a PNG/JPG/JPEG logo
- Preview the original image
- Convert the logo into SVG
- Adjust conversion settings
- Preview the generated SVG
- Download the SVG file
- Copy the SVG code

The tool should run completely inside the browser.

No backend.
No database.
No API key.
No file upload to server.

---

## 3. Core User Problem

Many users have only a PNG or JPG version of a logo.

When they use that logo on websites, documents, dashboards, ERP systems, or printed materials, the image may become blurry when resized.

SVG solves this problem because it is vector-based and can scale without losing quality.

This tool helps users convert simple logo images into editable and scalable SVG files.

---

## 4. Target Users

### Primary Users

- Web developers
- Designers
- ERP system users
- Admin users
- Small business owners
- Marketing staff
- SaaS product builders

### User Skill Level

The tool should be usable by non-technical users.

Users should not need to understand:

- SVG path syntax
- Canvas API
- Image tracing algorithm
- Vector graphics theory

---

## 5. Product Positioning

This project is a:

> Browser-only logo vectorizer tool.

It is not a:

- Logo redesign tool
- AI logo generator
- Professional Illustrator replacement
- Photo-to-perfect-SVG converter

---

## 6. Design Principle

## 6.1 Simple First

The user should understand the page within 5 seconds.

The main flow should be:

```text
Upload Image → Adjust Settings → Convert → Preview → Download
````

Do not overload the user with too many advanced settings at the beginning.

---

## 6.2 Private by Default

The uploaded image must stay inside the browser.

The system should clearly tell the user:

> Your image is processed locally in your browser. Nothing is uploaded.

This is important because logos may be private company assets.

---

## 6.3 Preview Before Export

The user should always see the result before downloading.

The UI should show:

* Original image
* Generated SVG result
* Conversion settings
* Download button

---

## 6.4 Honest Output Expectation

The tool should clearly explain what works well and what does not.

Best for:

* Simple logo
* Single-color icon
* High-contrast image
* Transparent background logo
* Black/white mark

Not ideal for:

* Photos
* Complex gradients
* Shadows
* Blurry images
* Low-resolution screenshots
* Multi-layer artwork

---

## 6.5 User Control

The conversion should not be fully automatic only.

Users should be able to adjust:

* Threshold
* Detail level
* Smoothness
* Invert color
* Fill color
* Background removal

---

## 7. Main User Flow

```text
1. User opens the page
2. User uploads PNG/JPG/JPEG logo
3. System displays original image preview
4. User adjusts settings if needed
5. User clicks Convert
6. System processes image in browser
7. System generates SVG
8. User previews SVG result
9. User downloads SVG or copies SVG code
```

---

## 8. MVP Scope

## 8.1 Included in MVP

The first version should include:

* Image upload
* Drag and drop upload
* Original image preview
* Canvas image processing
* Basic threshold control
* Basic image tracing
* SVG preview
* SVG download
* Copy SVG code
* Reset button
* Basic error handling

---

## 8.2 Not Included in MVP

The first version should not include:

* User login
* Cloud storage
* Backend upload
* AI logo redesign
* Manual SVG path editor
* Multi-user account system
* Payment system
* Full professional vector editor

---

## 9. Page Layout

The UI should use a two-panel layout.

```text
┌──────────────────────────────────────────────┐
│ Header                                       │
│ img-logo-convert-to-svg                      │
│ Convert simple logo images into SVG locally  │
├──────────────────────────────────────────────┤
│ Upload Area                                  │
│ Drag & drop or choose file                   │
├───────────────────────┬──────────────────────┤
│ Original Preview      │ SVG Preview          │
│                       │                      │
├───────────────────────┴──────────────────────┤
│ Settings                                     │
│ Threshold | Detail | Smoothness | Color      │
├──────────────────────────────────────────────┤
│ Actions                                      │
│ Convert | Download SVG | Copy SVG | Reset    │
└──────────────────────────────────────────────┘
```

---

## 10. UI Sections

## 10.1 Header Section

Purpose:

Explain what the tool does immediately.

Content:

```text
Image Logo to SVG Converter
Convert simple PNG/JPG logos into clean SVG files directly in your browser.
```

Supporting note:

```text
Private by default. Your image is processed locally and never uploaded.
```

---

## 10.2 Upload Section

Purpose:

Let user upload the source image.

Requirements:

* Support PNG
* Support JPG
* Support JPEG
* Optional: support WEBP
* Support drag and drop
* Support click to upload
* Show file name after upload
* Show file size
* Show warning if image is too large

Accepted file types:

```text
image/png
image/jpeg
image/jpg
image/webp
```

Recommended file size limit:

```text
5 MB for MVP
```

---

## 10.3 Original Preview Section

Purpose:

Show the uploaded image.

Requirements:

* Display image inside a preview card
* Preserve aspect ratio
* Show checkerboard background for transparent PNG
* Show image dimensions
* Show file type

Example metadata:

```text
File: company-logo.png
Size: 320 KB
Dimension: 800 × 400
Type: PNG
```

---

## 10.4 SVG Preview Section

Purpose:

Show generated SVG result.

Requirements:

* Display generated SVG
* Allow zoom preview if possible
* Show SVG code size
* Show path count if available
* Show empty state before conversion

Empty state message:

```text
Your SVG preview will appear here after conversion.
```

---

## 10.5 Settings Section

Purpose:

Allow user to control conversion quality.

### Threshold

Controls black/white separation.

Recommended range:

```text
0 - 255
```

Default:

```text
128
```

User explanation:

```text
Higher threshold keeps more dark areas. Lower threshold removes lighter areas.
```

---

### Detail Level

Controls how much detail is preserved.

Options:

```text
Low
Medium
High
```

Default:

```text
Medium
```

User explanation:

```text
Higher detail keeps more shape information but may create a larger SVG file.
```

---

### Smoothness

Controls path smoothing.

Options:

```text
Low
Medium
High
```

Default:

```text
Medium
```

User explanation:

```text
Higher smoothness creates cleaner curves but may remove small details.
```

---

### Invert Color

Purpose:

Useful when the logo is white on dark background.

Options:

```text
On / Off
```

Default:

```text
Off
```

---

### Background Remove

Purpose:

Try to remove white or near-white background.

Options:

```text
On / Off
```

Default:

```text
On
```

---

### SVG Fill Color

Purpose:

Allow user to choose output SVG color.

Default:

```text
#111111
```

Common options:

```text
Black
White
Brand Color
Custom Color
```

---

## 11. Action Buttons

## 11.1 Convert to SVG

Primary button.

Behavior:

* Disabled before image upload
* Enabled after valid image upload
* Shows loading state during conversion
* Generates SVG preview after conversion

Button text:

```text
Convert to SVG
```

Loading text:

```text
Converting...
```

---

## 11.2 Download SVG

Secondary button.

Behavior:

* Disabled before conversion
* Downloads generated SVG file
* File name should be based on uploaded file name

Example:

```text
company-logo.svg
```

---

## 11.3 Copy SVG Code

Secondary button.

Behavior:

* Copies SVG markup to clipboard
* Shows success message

Success message:

```text
SVG code copied.
```

---

## 11.4 Reset

Tertiary button.

Behavior:

* Clears uploaded image
* Clears preview
* Resets settings to default

---

## 12. Error Handling

## 12.1 Invalid File Type

Message:

```text
Unsupported file type. Please upload PNG, JPG, JPEG, or WEBP.
```

---

## 12.2 File Too Large

Message:

```text
This image is too large. Please upload an image smaller than 5 MB.
```

---

## 12.3 Conversion Failed

Message:

```text
Conversion failed. Try using a clearer, higher-contrast logo image.
```

---

## 12.4 Empty SVG Result

Message:

```text
No clear shape was detected. Try adjusting the threshold setting.
```

---

## 13. Technical Design

## 13.1 Frontend Stack

MVP should use:

* HTML
* CSS
* JavaScript
* Canvas API
* SVG generation logic

Optional library:

* ImageTracer.js

---

## 13.2 Browser-Only Architecture

```text
User Image
   ↓
FileReader API
   ↓
Image Object
   ↓
Canvas
   ↓
ImageData
   ↓
Preprocessing
   ↓
Tracing Algorithm
   ↓
SVG String
   ↓
Preview / Download
```

---

## 13.3 Main Modules

If the project is split into files:

```text
src/
├── main.js
├── image-loader.js
├── canvas-preview.js
├── image-preprocess.js
├── tracer.js
├── svg-generator.js
├── svg-exporter.js
└── ui-state.js
```

If MVP is single file:

```text
index.html
```

The single file should still separate code using clear sections:

```text
HTML structure
CSS styling
JavaScript constants
JavaScript state
Image upload logic
Canvas processing logic
SVG conversion logic
Export logic
UI event binding
```

---

## 14. Image Processing Logic

## 14.1 Load Image

Use `FileReader` to read the uploaded image as Data URL.

```text
File → Data URL → Image element → Canvas
```

---

## 14.2 Draw to Canvas

The image should be drawn to canvas before processing.

Canvas allows access to pixel data.

```text
canvas.getContext("2d")
ctx.drawImage(image, 0, 0)
ctx.getImageData(...)
```

---

## 14.3 Preprocess Image

Recommended preprocessing steps:

```text
1. Resize if image is too large
2. Convert to grayscale
3. Apply threshold
4. Remove background if enabled
5. Invert if enabled
6. Send processed ImageData to tracer
```

---

## 14.4 Trace Image to SVG

The tracing logic should convert pixel areas into vector paths.

For MVP, use an existing tracing library if possible.

Recommended MVP route:

```text
ImageTracer.js
```

Alternative route:

```text
Potrace-style monochrome tracing
```

---

## 14.5 Generate SVG

The generated SVG should include:

```text
<svg>
  <path />
</svg>
```

Required SVG attributes:

```text
xmlns="http://www.w3.org/2000/svg"
viewBox="0 0 width height"
width="..."
height="..."
```

The SVG should scale correctly.

---

## 15. SVG Output Requirement

The output SVG should be:

* Valid SVG markup
* Scalable
* Downloadable
* Previewable in browser
* Copyable as text
* Clean enough for web usage

Example output shape:

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512">
  <path fill="#111111" d="..." />
</svg>
```

---

## 16. UX Copywriting

## 16.1 Main Title

```text
Image Logo to SVG Converter
```

## 16.2 Subtitle

```text
Convert simple PNG/JPG logos into scalable SVG files directly in your browser.
```

## 16.3 Privacy Message

```text
Your image stays private. Conversion happens locally in your browser.
```

## 16.4 Best Result Hint

```text
Best for simple logos, icons, and high-contrast images.
```

## 16.5 Poor Result Hint

```text
Photos, gradients, shadows, and blurry images may not convert well.
```

---

## 17. Visual Design Direction

The UI should feel:

* Clean
* Simple
* Modern
* SaaS-like
* Lightweight
* Trustworthy
* Practical

Avoid:

* Overly decorative UI
* Heavy animation
* Confusing technical controls
* Too many options in first view
* Fake AI claims

Recommended visual style:

```text
White or light gray background
Rounded cards
Clear upload area
Two-column preview
Simple controls
Strong primary convert button
Subtle border and shadow
```

---

## 18. Accessibility

The tool should support:

* Keyboard upload trigger
* Clear button labels
* Visible focus states
* Sufficient color contrast
* Error messages in text
* Semantic HTML where possible

Important controls should have labels.

Example:

```html
<label for="threshold">Threshold</label>
<input id="threshold" type="range" />
```

---

## 19. Performance Consideration

Large images may slow down conversion.

Recommended behavior:

* Resize large image before processing
* Limit max canvas dimension
* Show loading state
* Avoid blocking UI for too long
* Consider Web Worker in future version

Recommended max processing size for MVP:

```text
1024px longest side
```

If image is larger, resize internally before tracing.

---

## 20. Browser Compatibility

MVP should support modern browsers:

* Chrome
* Edge
* Safari
* Firefox

Required browser APIs:

* FileReader API
* Canvas API
* Blob API
* Clipboard API
* URL.createObjectURL

Clipboard copy should have fallback if permission fails.

---

## 21. Security and Privacy

The app must not:

* Upload user image to server
* Store image remotely
* Send analytics containing image data
* Use third-party API for conversion
* Expose uploaded file content outside browser

If analytics are added in future, they should only track anonymous UI events, not file content.

---

## 22. File Naming

Downloaded SVG file name should be derived from original file name.

Example:

```text
Original: my-company-logo.png
Output: my-company-logo.svg
```

If file name is unavailable:

```text
converted-logo.svg
```

---

## 23. Empty States

Before upload:

```text
Upload a logo image to begin.
```

Before conversion:

```text
Adjust settings and click Convert to SVG.
```

After failed conversion:

```text
No clean vector shape detected. Try a higher contrast image or adjust threshold.
```

---

## 24. Future Enhancements

Future versions may include:

* Multi-color SVG tracing
* SVG optimization
* Background auto-detection
* Batch conversion
* Favicon export
* App icon export
* Black/white logo variants
* Manual path editing
* Before/after slider
* Web Worker processing
* WASM-based vectorizer
* VTracer integration
* Potrace integration
* AI cleanup suggestions

---

## 25. Suggested Version Plan

## V1 — MVP

Goal:

Basic working browser-only converter.

Features:

* Upload image
* Preview original
* Convert to SVG
* Preview SVG
* Download SVG
* Copy SVG code
* Threshold setting

---

## V2 — Better UX

Goal:

Make the tool easier for real users.

Features:

* Drag and drop
* Detail level
* Smoothness
* Invert toggle
* Background remove
* Fill color picker
* Better empty states
* Better error messages

---

## V3 — Advanced Converter

Goal:

Improve output quality.

Features:

* Multi-color tracing
* SVG optimization
* Web Worker
* Advanced presets
* Better path simplification
* Export multiple variants

---

## 26. Acceptance Criteria

The MVP is considered complete when:

* User can upload PNG/JPG/JPEG image
* Original image preview is displayed
* User can convert image to SVG
* SVG preview is displayed
* User can download SVG file
* User can copy SVG code
* User can reset the tool
* Invalid file type shows clear error
* Conversion happens locally in browser
* No backend is required
* No image is uploaded to server

---

## 27. Non-Goals

This project does not aim to:

* Replace Adobe Illustrator
* Perfectly vectorize every image
* Convert complex photos into clean SVG
* Recreate missing logo details
* Generate new brand identity
* Edit SVG paths manually in MVP

---

## 28. Key Risk

The main risk is user expectation.

Users may expect the tool to perfectly convert any image into a professional vector logo.

To reduce this risk, the UI must clearly explain:

```text
Best for simple logos and icons.
Not ideal for photos, gradients, shadows, or blurry images.
```

---

## 29. Recommended MVP Implementation Strategy

Start with the easiest working version:

```text
Single index.html
HTML + CSS + JavaScript
Canvas API
ImageTracer.js or embedded tracing logic
Download generated SVG
```

Do not start with backend, AI, account system, or complex editor.

The first goal is to prove the conversion flow works.

---

## 30. Final Product Statement

`img-logo-convert-to-svg` is a private, browser-only logo vectorizer that helps users convert simple PNG/JPG logos into scalable SVG files with preview, adjustment, and export tools.

The product should be simple, honest, fast, and practical.

````
