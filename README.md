
# NZ Index of Deprivation + Fire Service Localities

## Overview

The [New Zealand Index of Deprivation](http://www.ehinz.ac.nz/indicators/population-vulnerability/socioeconomic-deprivation-profile/) is a census based measure of socioeconomic deprivation. It is tied to [StatsNZ Statistical Area 1](https://www.stats.govt.nz/methods/geographic-hierarchy) blocks. These are small areas which aim to contain around 100-200 people.

Sometimes it is useful to have a measure for a larger area. The New Zealand Index of Deprivation _does_ provide mean values for Statistical Area 2 blocks. These come closer to the informal notion of a suburb. However, they still divide up into quite small blocks (often dividing suburbs into, say, eastern and western parts).

The New Zealand Fire Service has a [localities database](https://data.linz.govt.nz/layer/104830-fire-and-emergency-nz-localities/) which provides a set of areas which, in cities, correspond more closely to everyday suburb divisions.

**NB:** As of March 2022, StatsNZ are investigating a new statistical area, SA3, which sits between SA2 and territorial authorities and is designed with shortcomings of the fire and emergency localities in mind. It is likely these new areas will supercede any need for the use of file localities of the sort in this repository.

The script `sa1_to_fie_localities` uses the R `sf` package to generate weighted averages of New Zealand Index of deprivation 2018 scores at the NZ Fire Service Locality level. It finds all Statistical Area 1 (SA1) blocks which intersect with a given NZ Fire Service Locality, determines what proportion of each intersecting SA1 block is in the locality, and uses these proportions to produce a weighted average of the SA1 deprivation scores.

The motivation for this is a sociolinguistic study in which participants have been asked what area they have lived in at various times. The areas given in these answers are closer to the Fire Service localities than to either of the Statistical Areas offered by StatsNZ. It is likely that this is true for other studies in which participants are asked to say where they come from or have lived.

## Usage

### To run the script

Create a 'data' folder in the project folder. Inside, place the following:

* The Fire and Emergency NZ Localities .shp file available at <https://data.linz.govt.nz/layer/104830-fire-and-emergency-nz-localities/>.
	- Ensure you use the EPSG:2193 projection and get vectors as a Shapefile.
* The StatsNZ SA1 .shp file available at <https://datafinder.stats.govt.nz/layer/92210-statistical-area-1-2018-generalised/>.
	- Ensure you use the EPSG:2193 projection and get vectors as a Shapefile.
* The SA1 NZ deprivation Index 2018 data <https://www.otago.ac.nz/wellington/otago730395.xlsx>, and convert to CSV.

### To use the processed data

The `processed_data` folder contains (a) a csv file of the resulting Fire Service locality deprivation scores and (b) the Fire Service locality shape file augmented with the deprivation scores in a compressed file (`fire_dep2018.zip`).
