# Monte Faeta Wildfire Early Fire Signal (Sentinel-2, 2026)

This repository contains satellite-derived data products used to analyse a wildfire event in the Monte Faeta area (Tuscany, Italy) using Sentinel-2 Level-2A imagery.

The objective is to identify the earliest detectable fire-related spectral signal in a single satellite overpass using standard remote sensing indices.

This work does not determine ignition cause or exact ignition time. It only analyses spatial fire indicators at the time of satellite acquisition.

## Data source

- Satellite: Sentinel-2 (ESA Copernicus)
- Product level: L2A (Bottom-of-Atmosphere reflectance)
- Sensor: MSI (Multispectral Instrument)
- Processing: OpenEO Python workflow
- Spatial resolution: 10 m (bands resampled where required)
- Study area: Monte Faeta, Tuscany, Italy

## Files description

### AOI definition

[aoi_monte-faeta_2026.geojson](data/aoi_monte-faeta_2026.geojson)

This file defines the Area of Interest used for analysis.

### True colour composite

![monte-faeta_2026_true_color.png](outputs/figures/monte-faeta_2026_true_color.png)

RGB composite using Sentinel-2 bands:

- B04 (red)
- B03 (green)
- B02 (blue)

This image shows general land cover, smoke presence, and visible surface changes.

### SWIR composite

![monte-faeta_2026_swir.png](outputs/figures/monte-faeta_2026_swir.png)

False colour composite using:

- B12 (SWIR2)
- B8A (NIR narrow)
- B04 (red)

Shortwave infrared is sensitive to heat and burned vegetation.  
Bright or saturated pixels indicate strong thermal anomalies or fire-affected surfaces.

### Burn severity index

![monte-faeta_2026_nbr.png](outputs/figures/monte-faeta_2026_nbr.png)

The Normalized Burn Ratio (NBR) is used to detect burned or fire-affected vegetation:

NBR = (B08 - B12) / (B08 + B12)

Lower values indicate burned or heat-affected areas.

## Method summary

1. Sentinel-2 L2A scene acquired for 29 April 2026
2. AOI applied to extract study region
3. Bands resampled to 10 m grid
4. Spectral indices computed:
   - NBR
5. RGB and SWIR composites generated
6. Spatial analysis performed to identify strongest fire-related signal

## Interpretation

The analysis identifies a single pixel with the strongest and most consistent fire-related spectral response within the study area.

This pixel represents the earliest detectable fire signal in the Sentinel-2 observation.

Due to sensor limitations:

- Exact ignition point cannot be determined
- Fire spread dynamics may shift the location of maximum signal
- Mixed pixels (10 m resolution) may contain multiple surface types

## Reproducibility

All processing was performed using Python with OpenEO and standard geospatial libraries.

The workflow is reproducible using the same Sentinel-2 scene and AOI definition.

## License

- Images and analysis content are licensed under the [Creative Commons Attribution 4.0 International License](LICENSE).
