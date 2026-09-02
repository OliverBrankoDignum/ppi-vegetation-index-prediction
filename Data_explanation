This was copypasted from ChatGPT, I will explain better later.

## Data sources and preparation

This public dataset was prepared retrospectively for a reconstruction of a
machine-learning task completed during my 2025 student internship. It does
not contain any original internship or company data. AI assistance was used
to identify suitable public satellite data, prepare the input files and
document the procedure.

### Satellite image

The satellite imagery comes from the public Sentinel-2 Level-2A
Cloud-Optimized GeoTIFF collection hosted on AWS:

https://registry.opendata.aws/sentinel-2-l2a-cogs/

The selected Sentinel-2B product was:

`S2B_35TNJ_20190826_0_L2A`

It was acquired on 26 August 2019 and covers Sentinel-2 tile `35TNJ` in
northeastern Bulgaria.

The original true-colour GeoTIFF is available through this direct download
link:

https://sentinel-cogs.s3.us-west-2.amazonaws.com/sentinel-s2-l2a-cogs/35/T/NJ/2019/8/S2B_35TNJ_20190826_0_L2A/TCI.tif

The link points directly to a large `.tif` file and may therefore start a
download instead of displaying the image in a web browser.

The source `TCI.tif` is a true-colour image constructed from the Sentinel-2
red, green and blue bands:

- B04: red
- B03: green
- B02: blue

The source image has a spatial resolution of 10 metres and uses the
WGS 84 / UTM zone 35N coordinate reference system (`EPSG:32635`).

### Preparation of the supplied RGB GeoTIFF

The original satellite image was spatially cropped to a smaller study area
in northeastern Bulgaria. The crop has the following projected bounds:

- left: 556490 m
- right: 572810 m
- bottom: 4811030 m
- top: 4827840 m
- coordinate reference system: `EPSG:32635`

The resulting file is:

`Sentinel2_Bulgaria_2019-08-26_RGB_StudyArea.tif`

It contains:

- 3 RGB bands
- 8-bit values
- 1,632 × 1,681 pixels
- a spatial resolution of 10 × 10 metres
- the original `EPSG:32635` coordinate reference system

No reprojection, resampling or new colour transformation was applied. The
supplied GeoTIFF is only a spatial crop of the public source image and
retains the source pixels, resolution and coordinate reference system.

### Calculation of the PPI values

The PPI values were not field measurements and were not copied from an
official Copernicus PPI table. They were calculated from publicly available
Sentinel-2 observations.

For each selected Sentinel-2 scene, the Difference Vegetation Index was
calculated from bottom-of-atmosphere red and near-infrared reflectance:

`DVI = B08 - B04`

Plant Phenology Index was then calculated as:

`PPI = -0.8 × ln((DVIc - DVI) / (DVIc - 0.09))`

Here, `DVIc` represents an estimated upper DVI value for a fully developed
vegetation canopy. It was estimated separately for each pixel as the 98th
percentile of its valid DVI observations during the 2019 vegetation season.

Sixteen Sentinel-2 Level-2A scenes acquired between 26 April and
20 October 2019 were used to estimate `DVIc`. Pixels classified as invalid,
cloud, cloud shadow or snow were excluded using the Sentinel-2 Scene
Classification Layer (`SCL`). The calculated PPI values were restricted to
the range from 0 to 3.

The method was based on:

Jin, H. and Eklundh, L. (2014), *A physically based vegetation index for
improved monitoring of plant phenology*:

https://doi.org/10.1016/j.rse.2014.07.010

A description of the Copernicus PPI implementation is available here:

https://collections.eurodatacube.com/vegetation-indices/

### Creation of the point dataset

After the PPI values had been calculated for the image acquired on
26 August 2019, 1,200 valid pixels were selected without replacement using
the fixed random seed `20260901`.

The centre of every selected pixel was transformed from `EPSG:32635` to
geographic longitude and latitude coordinates in WGS 84 (`EPSG:4326`).

The resulting file is:

`PPI_Bulgaria_2019-08-26_1200_points.csv`

It contains three columns:

- `lon`: longitude in decimal degrees
- `lat`: latitude in decimal degrees
- `ppi`: satellite-derived Plant Phenology Index

The file contains 1,200 rows and 1,200 unique locations. Every location lies
within the supplied RGB GeoTIFF.

The point values should be described as **satellite-derived PPI values
sampled at point locations**, not as field measurements.

### Sentinel-2 scenes used

The following scenes were used to estimate the annual DVI ceiling:

- `S2A_35TNJ_20190426_0_L2A`
- `S2A_35TNJ_20190503_0_L2A`
- `S2A_35TNJ_20190523_0_L2A`
- `S2A_35TNJ_20190622_0_L2A`
- `S2B_35TNJ_20190627_0_L2A`
- `S2A_35TNJ_20190702_0_L2A`
- `S2B_35TNJ_20190717_0_L2A`
- `S2B_35TNJ_20190727_0_L2A`
- `S2A_35TNJ_20190811_0_L2A`
- `S2B_35TNJ_20190819_0_L2A`
- `S2B_35TNJ_20190826_0_L2A`
- `S2B_35TNJ_20190829_0_L2A`
- `S2B_35TNJ_20190915_0_L2A`
- `S2A_35TNJ_20190930_0_L2A`
- `S2A_35TNJ_20191003_0_L2A`
- `S2A_35TNJ_20191020_0_L2A`

### Reproducibility note

AI assistance was used to locate the public data, select the study area,
prepare the raster crop, calculate the satellite-derived PPI values and
draft this documentation.

The exact source product, original download link, spatial bounds,
calculation method, scene identifiers and random seed are documented above.
The original processing script was not retained, so the supplied files
cannot currently be reproduced by running code included in this repository.
