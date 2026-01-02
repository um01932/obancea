# PWA Icon Generation

The PWA requires icons in multiple sizes. You can generate them using:

## Option 1: Online Tool (Easiest)
1. Visit https://realfavicongenerator.net/
2. Upload your logo (assets/LogoSmall.webp or any high-res version)
3. Generate all sizes
4. Download and extract to `src/assets/icons/`

## Option 2: Using ImageMagick (Command Line)
If you have ImageMagick installed:

```bash
# From your logo
magick convert assets/LogoSmall.webp -resize 72x72 assets/icons/icon-72x72.png
magick convert assets/LogoSmall.webp -resize 96x96 assets/icons/icon-96x96.png
magick convert assets/LogoSmall.webp -resize 128x128 assets/icons/icon-128x128.png
magick convert assets/LogoSmall.webp -resize 144x144 assets/icons/icon-144x144.png
magick convert assets/LogoSmall.webp -resize 152x152 assets/icons/icon-152x152.png
magick convert assets/LogoSmall.webp -resize 192x192 assets/icons/icon-192x192.png
magick convert assets/LogoSmall.webp -resize 384x384 assets/icons/icon-384x384.png
magick convert assets/LogoSmall.webp -resize 512x512 assets/icons/icon-512x512.png
```

## Option 3: Node.js Script
Create icons using Sharp (already installed in backend):

```javascript
// backend/generate-pwa-icons.js
const sharp = require('sharp');
const fs = require('fs');

const sizes = [72, 96, 128, 144, 152, 192, 384, 512];
const inputImage = '../src/assets/LogoSmall.webp';
const outputDir = '../src/assets/icons';

if (!fs.existsSync(outputDir)) {
  fs.mkdirSync(outputDir, { recursive: true });
}

sizes.forEach(size => {
  sharp(inputImage)
    .resize(size, size)
    .png()
    .toFile(`${outputDir}/icon-${size}x${size}.png`)
    .then(() => console.log(`Generated icon-${size}x${size}.png`))
    .catch(err => console.error(`Error generating ${size}x${size}:`, err));
});
```

Then run: `node backend/generate-pwa-icons.js`

## Required Sizes
- 72x72
- 96x96
- 128x128
- 144x144
- 152x152
- 192x192
- 384x384
- 512x512

All should be PNG format for best compatibility.
