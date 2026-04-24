# Testing Checklist

## Static Checks

- JavaScript syntax passes `node --check`
- Page loads in Chrome from `file://`
- No runtime CDN dependency exists
- No WEBP accept rule exists in V1

## Manual Functional Checks

- PNG upload succeeds
- JPG/JPEG upload succeeds
- WEBP upload is rejected
- Non-image upload is rejected
- File larger than 5 MB is rejected
- Original preview appears
- Threshold value updates on slider input
- Convert enables SVG preview
- SVG code contains `xmlns` and `viewBox`
- Export size changes SVG `width` and `height`
- Export size preserves aspect ratio
- Download button downloads `.svg`
- Download filename includes selected dimensions when not using original size
- Copy button copies SVG code or shows fallback message
- Reset clears file, preview, SVG code, status, and settings

## Privacy Checks

- Conversion works without a backend
- Conversion works after network is disabled
- No uploaded image data leaves the browser

## Browser Smoke Targets

- Chrome
- Edge
- Firefox
- Safari, when available
