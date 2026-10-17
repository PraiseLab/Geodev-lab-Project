# Health Facility Accessibility in Okura Ward

A GIS project that maps how far people in Okura Ward, Dekina LGA, Kogi State, Nigeria, live from a health facility, using health facility locations, the road network and a 2 km reach zone.

**GeoDev Lab Africa, Cohort One.** Praise Soremekun

---

## The question

> What is the spatial distribution of health facilities in Okura Ward, Dekina LGA, Kogi State, and how accessible are these facilities relative to the ward's existing road network?

## Main result

**36.2% of Okura Ward (about 129.6 of 357.9 sq km) lies within 2 km, in a straight line, of one of its 15 health facilities. The other 63.8% is more than 2 km from any facility.** Most facilities sit along the roads, and large parts of the west and centre of the ward have none within reach.

[Okura Ward areas within 2 km of a health facility](..GeoDev Project/image/health_facilities_2km_okura.png)

This is straight-line distance, not travel distance along roads, so real journeys are longer.

## What's in here

```
Geodev-lab-Project/
├── README.md
├── Month1/
│   ├── 01-project-brief.docx        Week 1
│   ├── 02-data-notes.md             Week 2
│   ├── 03-data-preparation.md       Week 3
│   └── 04-month-1-summary.md        Week 4
├── data/
│   ├── raw/                         downloaded files, as extracted for Okura Ward
│   └── processed/
│       └── okura_ward_analysis.gpkg reprojected and clipped, analysis-ready
├── image/
│   └── health_facilities_2km_okura.png
└── qgis_project/
```

## Where to find each week

| Week | What it is | Link |
|---|---|---|
| 1 | Project brief, with a source link for every dataset | [Month1/01-project-brief.docx](Project/Month1/01-project-brief.md) |
| 2 | Data notes: what I downloaded, with sources, feature counts, columns and gaps | [Project/Month1/02-data-notes.md](Project/Month1/02-data-notes.md) |
| 3 | Data preparation and the five quality checks | [Month1/03-data-preparation.md](Project/Month1/03-data-preparation.md) |
| 3 | Analysis-ready data (EPSG:32632) | [data/processed/okura_ward_analysis.gpkg](Project/Data/processed/okura_ward_analysis.gpkg) |
| 4 | Analysis, checks and results (2 km buffer) | [Month1/04-month-1-summary.md](Project/Month1/04-month-1-summary.md) |
| 4 | Map image | [image/health_facilities_2km_okura.png](Project/image/health_facilities_2km_okura.png) |

## How to repeat it

This project was done by hand in QGIS, so there are no scripts to run. To repeat it:

1. Download the datasets listed in [the project brief](Project/Month1/01-project-brief.docx) and [the data notes](Project/Month1/02-data-notes.md), or use the files in `data/raw/`.
2. Open QGIS and add `data/processed/okura_ward_analysis.gpkg` (drag it into QGIS, or use *Layer → Add Layer → Add Vector Layer*).
3. Run *Vector → Geoprocessing Tools → Buffer* on the health facilities layer with a distance of 2000 (metres) and 20 segments.
4. Dissolve the result, clip it to the Okura Ward boundary, and compare its area with the ward area.

The data sources are GRID3 Nigeria (facilities and boundaries) and OpenStreetMap, downloaded with QuickOSM (roads).

## Progress

- [x] Week 1, project brief with a source link for every dataset
- [x] Week 2, data downloaded, opened and described
- [x] Week 3, reprojected, clipped and quality checked
- [x] Week 4, first spatial analysis, checked four ways

## Limits

- A buffer measures straight-line distance, not distance along roads.
- 7 of the 15 facilities have an unknown functional status.
- Most road attributes (name, surface, lanes) are empty in the OpenStreetMap data.
- There is no population data yet, so the result is about land area, not number of people.

---

Praise Soremekun · GeoDev Lab Africa
Learn. Build. Collaborate. Transform.
