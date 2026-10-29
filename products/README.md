# Product photo folders

These directories are intentionally empty of product photographs: no verified showroom images were supplied yet. The `PUT_IMAGES_HERE.txt` notes in each department describe what belongs there.

- `tiles/` — tile close-ups and room photos
- `marble/` — marble slab and texture photos
- `granite/` — granite slab and texture photos
- `laminar/` — only Laminar images authorized for dealer use
- `categories/` — optional shared category-card images

## Add a product photo

1. Copy the approved WebP or JPG file into its department folder.
2. Open the matching product object in `../products.js`.
3. Add the exact relative file path to that product's `images` array, such as `products/tiles/my-tile-closeup.webp`.
4. Use the first image as the card photo; the second is used for card hover and as an alternate detail photo. Add more for the thumbnail gallery.

The site will otherwise show a labelled editorial fallback; that image is not a photo of showroom inventory. Product dimensions, finishes, names and availability should be verified before changing an example record into a real listing.
