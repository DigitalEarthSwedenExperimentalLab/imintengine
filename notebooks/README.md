# SDL 3.0 case notebooks

Jupyter notebooks that present the Swedish Space Data Lab (SDL 3.0) use cases with
[IMINT Engine](../README.md). Each one fetches real Copernicus Sentinel-2 data from
[Digital Earth Sweden](https://digitalearth.se), runs one or more analyzers and shows the result.
The saved outputs come from a full run; see the provenance cell at the end of each notebook.

> **Experimental.** Not a validated product or service, and without support.

## Run

```bash
pip install -r requirements.txt     # IMINT Engine pinned to b183e1a, plus Jupyter and plotting
jupyter lab
```

Notebooks 030 and 070 also need `sahi` and `ultralytics` (AGPL-3.0), and 140 needs `sen2sr` and
`mlstac`; the pinned versions are in `requirements.txt`.

Each user logs in to Digital Earth Sweden with their own account in the notebook's *Log in*
cell, either with EGI in the browser (`LOGIN_METHOD = "egi"`, the default) or with a DES username
and password (`LOGIN_METHOD = "password"`, typed when asked). See
[digitalearth.se](https://digitalearth.se) for how to get access. Every data fetch goes through that
login, and nothing is saved in the notebook. No credentials are shared or
kept in the notebooks. There is no synthetic fallback: without a login the fetch stops with an error.

## Notebooks

| # | Notebook | Area | Analyzers |
|---|----------|------|-----------|
| 010 | [Getting started](sdl3-cases/070_CASE_010-Getting-Started.ipynb) | Visby, Gotland | `spectral` |
| 020 | [Wildfires: Kårböle 2018](sdl3-cases/070_CASE_020-Wildfire-Karbole.ipynb) | Ljusdal, Gävleborg | `spectral` (dNBR) |
| 030 | [Marine vessels: Sotenäs](sdl3-cases/070_CASE_030-Marine-Vessels-Sotenas.ipynb) | Bohuslän | `marine_vessels` (YOLO11s, AGPL-3.0) |
| 040 | [Grazing: Munkarp](sdl3-cases/070_CASE_040-Grazing-Munkarp.ipynb) | Höör, Skåne | `GrazingAnalyzer` with LPIS |
| 050 | [Coastline: Sandhammaren](sdl3-cases/070_CASE_050-Coastline-Ystad.ipynb) | east of Ystad, Skåne | `shoreline` |
| 060 | [Vegetation edge](sdl3-cases/070_CASE_060-Vegetation-Edge.ipynb) | Vänern, Lidköping–Läckö | `vegetation_edge` |
| 070 | [Commercial shipping: Öresund](sdl3-cases/070_CASE_070-Commercial-Marine-Oresund.ipynb) | Helsingborg–Helsingør | `marine_vessels` (YOLO11s, AGPL-3.0) |
| 080 | [Cloud optical thickness](sdl3-cases/070_CASE_080-COT-Cloud-Filtering.ipynb) | Västerbotten | `cot` (SDL 2.0 models) |
| 100 | [Write your own analyzer](sdl3-cases/070_CASE_100-Custom-Analyzer.ipynb) | Skåne | tutorial |
| 120 | [Water quality: Stigfjorden](sdl3-cases/070_CASE_120-Water-Quality-Stigfjorden.ipynb) | Tjörn, Bohuslän | `water_quality` (NDCI, MCI) |
| 130 | [Coregistration](sdl3-cases/070_CASE_130-Coregistration.ipynb) | Eslöv, Skåne | `imint.coregistration` |
| 140 | [Super-resolution: Stockholm](sdl3-cases/070_CASE_140-Super-Resolution-Stockholm.ipynb) | central Stockholm | `sr` (SEN2SR, CC0) |

There is no 090: the multitemporal land-cover case was removed because its model checkpoint is
not public. A further case, weather-based image selection (110), is in
[space-datalab-metafilter](https://github.com/DigitalEarthSwedenExperimentalLab/space-datalab-metafilter)
under `notebooks/`.

The maps in the notebooks are interactive in Jupyter; GitHub's viewer shows only a placeholder.

The `070_CASE_` prefix follows the naming in the Digital Earth Sweden
[community repository](https://github.com/DigitalEarthSweden/digital-earth-sweden-community).

## License

The notebooks are source code under the Apache License 2.0, like the rest of
the repository's code; their saved outputs are CC0 1.0. See the
[License section of the root README](../README.md#license). Models and data keep their own
licences; each notebook names them.
