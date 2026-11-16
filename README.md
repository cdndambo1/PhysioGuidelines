# PhysioGuidelines 1.1 – expanded clinical scope

A free, installable Progressive Web App (PWA) starter for international physiotherapists. The MVP includes a responsive clinical reference library, searchable guideline summaries, discipline and population filters, local bookmarks, shareable guideline links, and service-worker caching for offline access after the first successful visit.

## Included clinical starter summaries

1. **Neurology – Adult stroke rehabilitation and recovery**: linked to the 2026 AHA/ASA guideline resource.
2. **Musculoskeletal – Low back pain and sciatica**: linked to NICE NG59, updated 29 July 2026, and the 2021 APTA/JOSPT CPG.
3. **Paediatrics – Cerebral palsy in under 25s**: linked to NICE NG62, last reviewed 19 September 2024, and APTA Pediatrics CPG resources.

The summaries are short educational orientations, not a substitute for reading the original guidance. Evidence grades are not invented: users are directed to the original source for its recommendation class, certainty and evidence tables.

## Run locally

This is a static site and requires no build step, package manager, API key, database, or paid service.

```bash
python3 -m http.server 8080
```

Then open `http://localhost:8080` in a modern browser. Service workers require HTTPS or localhost. `file://` will not enable offline caching.

## Deploy free

Upload the contents of this folder to any static host that supports HTTPS, such as GitHub Pages, Cloudflare Pages, or Netlify's free static hosting tier. Set the publish directory to the project root. No environment variables are required.

## Install on Android

1. Open the deployed HTTPS URL in Chrome on Android.
2. Use the browser menu and choose **Install app** or **Add to Home screen** (the exact label varies by browser/version).
3. Open the installed app once while online. The service worker caches the application shell for later offline use.

## Offline and storage behaviour

- The app shell is cached by `sw.js` after first load.
- Guideline content is bundled in `app.js`, so the three starter summaries remain available offline once the app shell is cached.
- Bookmarks are stored in browser `localStorage` on the current device; they do not sync between devices.
- External reference pages need an internet connection.

## Clinical governance before public launch

This is an MVP prototype and its starter summaries have not yet been independently peer reviewed by a named international clinical editorial board. Before clinical deployment, appoint qualified reviewers for each discipline, verify all recommendation wording against the live source, add source-specific evidence grades and full citations, document review dates, add a change log, establish a correction process, and confirm local regulatory/privacy requirements. Do not collect patient-identifiable data in this app.

## Planned next disciplines

Orthopaedics, burns, cardiopulmonary, sports, geriatrics, pelvic health, amputee rehabilitation and critical care physiotherapy.

## Project structure

- `index.html` – app shell and page structure
- `styles.css` – responsive interface
- `app.js` – guideline content, search, filters, bookmarks and detail views
- `manifest.webmanifest` – install metadata
- `sw.js` – offline application-shell cache
- `assets/icon.svg` – app icon
