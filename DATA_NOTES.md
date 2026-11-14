# Data notes

## Included demonstration data

`public/geojson/Histori_Banjir_Clean.geojson` contains six synthetic points, one per year from 2020 to 2025. They all use the illustrative coordinate [106.8, -6.2] and explicitly synthetic place labels. These records do not describe actual flood events.

`public/geojson/batas_indonesia.json` is an empty FeatureCollection. The boundary overlay will therefore contain no province polygons until you supply permitted boundary data.

## Original local datasets excluded from this folder

- The original application flood GeoJSON contains 7,489 records. Its properties are `tanggal`, `kabupaten`, `provinsi`, `year`, `latitude`, and `longitude`.
- The original boundary file contains 34 features with `source`, `id`, and `name` properties. Its source property references https://simplemaps.com.
- Raw coordinate CSVs, manual-review CSVs, alternate converted outputs, and duplicate GeoJSON files are excluded.

The inspected flood property fields describe dates and administrative areas, with no direct personal identifiers in their field names. That does not establish permission to redistribute them. Record the actual source, download date, coverage, corrections, and applicable redistribution terms before adding real data to a public repository.

## Use your original data locally

From the parent directory containing both the original folder and this package, run the following in PowerShell:

```powershell
Copy-Item -LiteralPath '.\histori banjir\TPBW HOho\TPBW\public\geojson\Histori_Banjir_Clean.geojson' -Destination '.\histori-banjir-github\public\geojson\Histori_Banjir_Clean.geojson'
Copy-Item -LiteralPath '.\histori banjir\TPBW HOho\TPBW\public\geojsonatas_indonesia.json' -Destination '.\histori-banjir-github\public\geojsonatas_indonesia.json'
```

These commands replace the demonstration files. **Do not commit the replacements unless you have established permission to redistribute them.** To keep local replacements out of future commits, skip these paths during staging and inspect `git diff --cached` before committing. `.gitignore` does not protect changes to files that are already tracked.

## Flood feature schema

```json
{
  "type": "Feature",
  "geometry": { "type": "Point", "coordinates": [106.8, -6.2] },
  "properties": {
    "tanggal": "1 01 2020",
    "kabupaten": "DEMO LOCATION (SYNTHETIC)",
    "provinsi": "DEMO (SYNTHETIC)",
    "year": 2020,
    "latitude": -6.2,
    "longitude": 106.8
  }
}
```

Coordinates use longitude, latitude order. Store features inside a GeoJSON FeatureCollection.

## Optional CSV conversion

Install Python dependencies in a virtual environment:

```bash
python -m venv .venv
# Activate the environment using the command appropriate for your shell.
python -m pip install -r requirements.txt
```

Place your permitted input at `scripts/Koordinat Fix Fix.csv`. The converter expects semicolon-separated columns: `Tanggal Kejadian`, `Kabupaten`, `Provinsi`, `Latitude`, and `Longitude`.

```bash
cd scripts
python csvtogeojson.py
```

The generated `scripts/Histori_Banjir_Clean.geojson` is ignored by Git. Review its coordinate corrections, dates, and rejected records before manually copying it to `public/geojson/Histori_Banjir_Clean.geojson`. The converter uses hardcoded regional coordinate corrections and heuristic normalization, so its output must not be treated as independently verified observations.
