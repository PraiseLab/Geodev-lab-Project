# Project brief

**Week 1 deliverable.** GeoDev Lab Africa, Cohort One.
Author: Praise Soremekun

## 1. The question

> What is the spatial distribution of health facilities in Okura Ward, Dekina LGA, Kogi State, and how accessible are these facilities relative to the ward's existing road network?

## 2. Why this question

Getting to a health facility quickly can decide whether a treatable illness stays treatable, and in a large, mostly rural ward like Okura, distance and poor roads can make that hard. Mapping where the facilities are and how the roads connect people to them shows which communities may be left out, so that decisions about new clinics or road improvements can be based on evidence instead of guesswork. I want to keep building on this work over the year, because it can grow to include population, travel time and other wards.

## 3. Study area

The study area will be **Okura Ward, in Dekina Local Government Area (LGA), Kogi State, Nigeria**.

I will define the boundary as the official administrative ward boundary from the GRID3 Nigeria Operational Wards dataset. I will use it to clip all my other data, such as health facilities and roads, so the analysis only covers what lies inside the ward. I will work in a projected coordinate system that uses metres, so that distances and buffers are measured correctly.

## 4. What I mean by the terms

- **Health facility:** any point in the GRID3 Nigeria health facilities dataset that falls inside Okura Ward. This includes hospitals, primary health centres and health posts, whether public or private. I will not judge the quality of care, only the location.

- **Spatial distribution:** where the facilities are placed across the ward, for example whether they are spread out evenly or bunched together, and whether they sit near roads or settlements.

- **Accessible:** a place counts as accessible if it is within **2 km of a health facility**, which is roughly a 25 to 30 minute walk. I will measure this first as straight-line distance, using a buffer around each facility. I may also test 5 km as a second distance, because people in rural areas often travel further.

- **Road network:** the roads for the ward taken from OpenStreetMap, including the major highway and the minor roads. I will use them to see how the facilities connect to the rest of the ward.

- **Limits of these definitions:** a facility on the map may not be open or working, and a road on the map may not be passable all year. I will note these gaps where my data cannot answer them.

## 5. Datasets

| # | Dataset | What it gives me | Source |
|---|---|---|---|
| 1 | GRID3 NGA – Operational State Boundaries (December 2020) | The Kogi State boundary, to place the study area in its state | [State Boundary](https://data.grid3.org/datasets/GRID3::grid3-nga-operational-state-boundaries-/about) |
| 2 | GRID3 NGA – Operational LGA Boundaries (December 2020) | The Dekina LGA boundary, to place the ward inside its LGA | [Local Governement Area Boundary](https://data.grid3.org/datasets/GRID3::grid3-nga-operational-lga-boundaries/about) |
| 3 | GRID3 NGA – Operational Wards v3.0 (July 2026) | The Okura Ward boundary, which defines my study area and which I will clip all other data to | [Ward Boundary](https://data.grid3.org/datasets/GRID3::grid3-nga-operational-wards-v3-0/about) |
| 4 | GRID3 NGA – Health Facilities v3.0 | The location of health facilities as points, with their name, type, ownership and functional status. The dataset is non-exhaustive and non-validated, so some facilities may be missing | [Health Facilities](https://data.grid3.org/datasets/827e3638dc204f4b9ddbbd19b00954d6/about) |
| 5 | OpenStreetMap roads, extracted with the QuickOSM plugin in QGIS | The road network of the ward (major highway and minor roads), to see how facilities connect to the rest of the ward | [data](https://www.openstreetmap.org)  and [QuickOSM Plugin](https://plugins.qgis.org/plugins/QuickOSM/) |

## 6. What "done" looks like

The finished project will be a map of Okura Ward showing the ward boundary, the health facilities, the roads and the reach zones around each facility. I will export the map as a PNG image and, if time allows, as an interactive web map people can zoom and click. Anyone with QGIS should be able to repeat the work from my GitHub repository, which will hold the data, the notes on each step and a README explaining how to follow them.

## 7. Known risks

**The health facility data may not be complete.** The data says it is not fully checked, so some facilities may be missing or in the wrong place. I will look at the points on the map to see if they make sense, and I will say in my results that I only used the facilities in the dataset.

**The road data may have gaps.** OpenStreetMap is made by volunteers, so some roads may be missing or have no details like name or type. I will check the roads on the map and remove anything that is not a road.

**Straight-line distance is not the same as the distance people travel.** A buffer measures in a straight line, but people have to follow roads, which are longer. I will say clearly that my first result is based on straight-line distance, and try to use the roads later.

---

**Status:** Week 1 complete. Data acquisition in Week 2, see
[02-data-notes.md](02-data-notes.md).