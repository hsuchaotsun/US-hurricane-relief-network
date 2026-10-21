# Constructing an Intermodal U.S. Hurricane Relief Network

**Generative AI Note:** Generative AI was not used in the development of the rail, intermodal, population, or truck-routing portions of this project. Generative AI was used in portions of the hurricane and weather analysis. A detailed disclosure is provided at the end of the notebook.

## Data Sources

| Data | Source | License / Terms | Access |
|---|---|---|---|
| Historical Hurricane Tracks | NOAA National Hurricane Center, Atlantic HURDAT2 | NOAA public data; data may be used and redistributed. | https://www.nhc.noaa.gov/data/ |
| Atlantic Sea Surface Temperature | NOAA Climate Prediction Center, Monthly Atlantic SST Indices (North, South and Tropical Atlantic) | NOAA public data; data may be used and redistributed. | https://www.cpc.ncep.noaa.gov/data/indices/sstoi.atl.indices |
| Ocean Temperature | NSF NCAR Climate Data Guide | Publicly accessible research data; responsible use and citation of the original dataset are encouraged. | https://climatedataguide.ucar.edu/climate-data |
| U.S. Rail Network | Federal Railroad Administration / Bureau of Transportation Statistics, North American Rail Network | Public-domain federal geospatial data (CC0 / U.S. Public Domain). | https://catalog.data.gov/dataset/north-american-rail-network-lines |
| Intermodal Facilities | Bureau of Transportation Statistics, Intermodal Freight Facilities Rail TOFC/COFC | U.S. Public Domain. | https://catalog.data.gov/dataset/intermodal-freight-facilities-rail-tofc-cofc-c0c43 |
| Population Estimates | U.S. Census Bureau, Vintage 2025 Population Estimates | Public-use U.S. Census Bureau data; source should be cited and analysis should not imply Census Bureau endorsement. | https://www.census.gov/data/tables/time-series/demo/popest/2020s-total-cities-and-towns.html |
| City Coordinates | Simple Maps (via US Census Data)| Public-use data| https://simplemaps.com/data/us-cities |
**Data Access:** All datasets are publicly accessible through the links above. Data were downloaded from the respective source websites and imported into Python for cleaning, integration, and analysis.

## Executive Summary

This project examines how historical hurricane activity, population, intermodal terminals, rail infrastructure, and modeled trucking routes can inform U.S. hurricane-relief planning. We clean and integrate the source datasets, compare historical county-level storm-center exposure with population, and assess route distances, travel times, and alternative supply origins. The transportation screening evaluates **241 intermodal hubs across six destinations (1,446 hub–destination routes)**: five exposure-priority locations plus New Orleans as a separate Hurricane Katrina case.

**Key findings:** Historical storm-center exposure and population represent different prioritization criteria; straight-line distances cannot substitute for road-network routing; and the fastest modeled trucking option is not always the only practical candidate. Rail ownership and network connectivity add constraints that a truck-only analysis cannot capture. The rail–truck optimization section presents Julian's submitted modeling workflow and outputs, subject to the limitations described below.

**Decision implication:** Use these results to prioritize which candidate routes and hubs warrant operational verification—not to claim that routes will remain open after a hurricane. The next step is to validate destination coordinates and assess disruption, access, and transfer assumptions before treating modeled travel times as deployment commitments.

## 1. Problem Definition

When a hurricane affects a city, getting relief supplies there quickly can become difficult because the same storm can disrupt the transportation network needed to reach it. This project aims to determine how supplies can be moved from large, safe U.S. supply hubs to hurricane-affected cities using truck and rail transportation. The main decision is which available route can deliver those supplies most efficiently while accounting for the location of the storm, the population being served, and whether the transportation network remains accessible. This is especially important for humanitarian and disaster-relief organizations that need to make transportation decisions quickly after a hurricane. We will measure success by the percentage of selected relief routes that can reach affected cities within three days.

We will:

- Identify hurricane-affected cities in the nine-state study area using historical hurricane and population data.
- Identify large population centers that can serve as supply hubs outside the affected area.
- Evaluate truck-only and intermodal rail-truck transportation options between supply hubs and affected cities.
- Compare available routes based on estimated transportation time and accessibility.
- Determine the most efficient relief route and whether it can reach the affected city within the three-day target.

## 2. Data Overview

We are using several datasets to cover the different parts of the relief network. Hurricane and climate data tell us about the storms, Census population data help us identify cities that may need relief or could serve as supply hubs, and the rail and intermodal data show the transportation network available between them.

So far, we have prepared the hurricane, population, intermodal facility, and rail network data. The remaining climate and routing pieces will be added as the rest of the analysis is completed.

**Section Takeaway:** These datasets give us information on both sides of the problem: where relief may be needed and what transportation options are available to get it there.
