# Histori Banjir

An interactive map for exploring historical flood records in Indonesia. Built with Next.js, React, TypeScript, Mapbox GL JS, and Turf.js. The interface is primarily in Indonesian.

> This repository ships with six **synthetic demonstration records**, not real flood observations. All demo points use the same illustrative location. The Indonesia boundary file is an empty GeoJSON placeholder. Original datasets are intentionally excluded because their redistribution permissions have not been established.

## Features

- Interactive map with flood markers and date/location popups.
- Year and month filters with a reset control.
- Light/dark map styles and map navigation controls.
- Location search through Mapbox geocoding.
- Circular buffers with radii configured by year.

Buffers are illustrative visualization settings, not measured inundation boundaries. The original data conversion code includes coordinate corrections and heuristics; independently validate any converted data before use.

## Requirements

- Node.js 22 LTS and npm.
- A Mapbox account and a public browser access token.
- Internet access for Mapbox services and Google font downloads during builds.
- Optional: Python 3.10+ for CSV conversion.

## Local setup

```bash
npm ci
```

Copy `.env.example` to `.env.local`, then set:

```dotenv
NEXT_PUBLIC_MAPBOX_TOKEN=your_public_mapbox_token
```

Use a public browser token with only the permissions your map needs, and configure allowed URLs in your Mapbox account for your development and deployed origins. Variables prefixed with `NEXT_PUBLIC_` are exposed to the browser; never use a secret token here. Keep real environment files out of Git.

```bash
npm run dev
```

Open http://localhost:3000.

## Commands

```bash
npm run lint
npm run build
npm start
```

`npm start` serves a completed production build. This packaging preserves the application's existing implementation and dependency versions. A successful production build is not implied: existing TypeScript/ESLint issues may need to be resolved. Review dependency security before deploying publicly.

## Repository layout

```text
src/                   Application, map components, styles, and utilities
public/                Static assets and demonstration GeoJSON
scripts/csvtogeojson.py Optional converter from the original project
requirements.txt       Optional Python dependency
.env.example           Configuration template with no credentials
DATA_NOTES.md          Dataset provenance, schema, and replacement instructions
PUBLISHING.md          GitHub preparation and exclusions
```

The active page loads `src/components/Map/MapPolosan.tsx`. Other preserved components and the `/api/times` route include an earlier pollution/wind workflow. Its datasets are not supplied; those features are not part of the default flood map.

## Real datasets

See [DATA_NOTES.md](DATA_NOTES.md). Replacing files in `public/` makes their full contents downloadable by visitors. A private GitHub repository does not make a deployed site's public assets private.

## Attribution and licensing

This folder was prepared from the supplied project. Its existing Git configuration pointed to `https://github.com/hamdansyaif/weather-app.git`; this is a provenance clue, not proof of authorship or permission. Preserve applicable upstream attribution and establish permission for reused code/assets before public distribution. No license has been invented or assigned during packaging. Third-party dependencies retain their own licenses.

The original province boundaries identify SimpleMaps as their source. They are not included in this package. Original flood-data provenance and redistribution terms were not documented in the supplied files. Synthetic demo data must not be described as observed flood history.
