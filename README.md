# Aashika Tiles & Marble

Static showroom website for Aashika Tiles & Marble, Nawalpur. The existing single-page app keeps markup, styles and routing in `index.html`; structured catalogue data is in `products.js`.

## Project layout

```text
index.html                 Website HTML and app entry point
css/
	styles.css               All site styling and responsive rules
products.js                Structured catalogue records (no build step)
server.js                  Small dependency-free local web server
package.json               npm start command
README.md                  Setup, content and image instructions
.editorconfig              Consistent indentation and line endings
.prettierrc.json           Consistent source formatting rules
inspiration/               Room inspiration images (currently placeholders)
products/
	categories/              Shared category images (reserved)
	tiles/                   Tile product and category photos
	marble/                  Marble product and category photos
	granite/                 Granite product and category photos
	laminar/                 Authorized Laminar photos only
projects/                  Reserved; no project gallery photos supplied yet
showroom/                  Real showroom and department photos
```

Open `index.html` from the project root. Keep `css/`, `products.js`, and all image folders beside it because the site uses relative paths. The CSS is in `css/styles.css`; edit that file for colours, typography, spacing, grids and mobile rules. The HTML and application script include section comments to help locate the site shell, catalogue logic, page templates and routing. `.editorconfig` and `.prettierrc.json` keep formatting consistent. The hidden `.notebook/` folder is local tooling, not part of the published website.

## Why image folders look empty

The `products/`, `showroom/`, `inspiration/` and `projects/` folders are **photo storage locations**, not source-code folders. The workspace currently contains only `PUT_IMAGES_HERE.txt` guides in those locations—no real product, showroom, or project photos were supplied. The site therefore uses labelled editorial fallbacks for layout preview. Replace them with approved Aashika photos and map each product image path in `products.js`. The `projects/` directory is reserved for later; the current site does not yet show a project gallery.

## Run locally

Requires Node.js and npm. From this project folder, run `npm start`, then open `http://127.0.0.1:4173` in a browser. Stop the server with Ctrl+C in the terminal. There are no npm dependencies to install.

You can also open `index.html` directly, but using the local server is recommended so relative assets and browser behavior work consistently.

## Publish

Upload this project folder to a static host such as Netlify, Vercel, cPanel or GitHub Pages. No build step is required. The local `server.js` is only for development; static hosts serve the files themselves.

## Add photos

The page checks the exact local path first, then tries the same basename with the other `.webp`/`.jpg` extension. When neither local photo exists, cards use explicitly labelled editorial interior photography from Unsplash as a visual stand-in. It is **not** a photo of Aashika inventory, showroom, projects, or a claimed installation. Supply approved local photography and it replaces the stand-in automatically. Set product filenames in `products.js` or use the fallback paths below. Aim for about 1200px wide and under 200 KB per image. Remote editorial fallbacks require an internet connection; a textured background and “Photo needed” note remain if those requests also fail.

- Homepage hero: `showroom/hero.webp`. Homepage material cards: `showroom/home-tiles.webp`, `showroom/home-marble.webp`, `showroom/home-granite.webp`.
- Department/homepage category cards: `products/<tiles|marble|granite>/category-<category-slug>.webp`, e.g. `products/tiles/category-bathroom-tiles.webp`. The legacy `products/categories/` folder may be used for shared assets, but current category cards read from their department folders.
- Product photos: paths are explicit in each record's `images` array in `products.js`, e.g. `products/tiles/tile-preview-01-1.webp`. Use 2–5 images per item (main material, detail/texture, room inspiration when licensed, another angle). The `images` paths are ordered and drive the card hover and detail thumbnails.
- Inspiration cards: `inspiration/living-room.webp`, `bathroom.webp`, `kitchen.webp`, `bedroom.webp`, `staircase.webp`, `outdoor.webp`, `commercial.webp`.
- Department banners: `products/tiles/department-hero.webp`, `products/marble/department-hero.webp`, `products/granite/department-hero.webp`. Laminar editorial/authorized imagery: `products/laminar/dealer-approved-hero.webp`, `products/laminar/authorized-catalogue.webp`, `showroom/laminar-banner.webp`.
- Room inspiration: `inspiration/living-room.webp`, `bathroom.webp`, `kitchen.webp`, `bedroom.webp`, `staircase.webp`, `outdoor.webp`, `commercial.webp`.

Use only images Laminar has given the showroom permission to use. The Laminar Nepal website was unreachable during this update, so no current official product/category names or Laminar images were added. Obtain the current dealer catalogue, verified collection/category labels and product identifiers, the technical/specification sheet, current availability confirmation, authorized hi-resolution product/room images, dealer-use permission, and any required image credits from Laminar/the showroom. Do not substitute guessed Laminar items. `projects/` is reserved; project images are not currently displayed by the website.

## Edit the product catalog

Edit `products.js` (not `index.html`). Each object has a stable unique ID, `department` (`tiles`, `marble`, or `granite`), category slug, verified details, applications, image paths, description, featured flag and availability. The initial items are clearly marked illustrative examples, not real inventory. Laminar entries must be based only on current authorized materials; none are included until verified data is available.

- Add a comma-separated product object with a permanent unique `id`; avoid changing IDs when sorting or editing.
- Remove an object to remove a listing. Set `featured: true` only when the showroom intentionally selects that verified item.
- Change an image by replacing a path in that object's `images` array. Store the image under the relevant `products/<department>/` folder.
- Change category by changing the category slug (examples: `floor-tiles`, `white-marble`, `black-granite`). Add/remove category navigation in `index.html` only to match real departments and inventory.
- Use empty strings for unknown specs, `available: null` when availability is not confirmed, and `previewOnly: true` for illustrative records. Do not invent prices, dimensions, technical information or availability.

## Replace contact placeholders

In `index.html`, replace the contact placeholders with verified details. Set `CFG.wa` to the WhatsApp number with country code and digits only, `CFG.mapUrl` to the confirmed directions URL, and `CFG.formEndpoint` to a configured form-service endpoint. WhatsApp, directions and form submission are not active until their values are supplied. Once confirmed, add the business phone and street address to the LocalBusiness schema near the top of `index.html`. Do not add unsupported awards, ratings, reviews, customer or project counts, opening hours, claims or social accounts.
