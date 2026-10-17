# Data preparation

**Week 3 deliverable.** GeoDev Lab Africa, Cohort One.
Author: Praise Soremekun

What I reprojected, what I clipped, what I checked, and what I fixed.

---

## 1. Coordinate system decisions

**Working CRS:** EPSG:32632 (WGS 84 / UTM Zone 32N)

**Why this one:** My project measures distance and area (for example 2 km and 5 km reach zones around facilities, and the share of the ward they cover), so I need a CRS in metres. Okura Ward falls within UTM Zone 32N, so EPSG:32632 keeps distances accurate for this area.

| Dataset | CRS as downloaded | CRS after | Operation |
|---|---|---|---|
| Health facilities | EPSG:4326 | EPSG:32632 | Reprojected |
| Highway1 (Trunk Road A233) | EPSG:4326 | EPSG:32632 | Reprojected |
| Highway2 (other roads) | EPSG:4326 | EPSG:32632 | Reprojected |
| Okura Ward boundary | EPSG:4326 | EPSG:32632 | Reprojected |

I used **Reproject Layer**, so every coordinate was recalculated. I did not just relabel the data.

## 2. Clipping to the study area

- **Boundary used:** Okura Ward boundary, from GRID3 Nigeria Operational Wards v3.0 (`OkuraWard_DekinaLGA.gpkg`), after reprojecting it to EPSG:32632
- **Features before clipping:** health facilities 15, Highway1 1, Highway2 168
- **Features after clipping:** health facilities 15, Highway1 1 (about 14 km), Highway2 71 (about 171 km)

The health facilities were already limited to Okura Ward in Week 2, so the count did not change. Highway2 dropped from 168 to 71 segments because the rest of the road lines lay outside the ward.

## 3. The five quality checks

| Check | Result | Action taken |
|---|---|---|
| Is the CRS what I think it is? | No, the downloaded data was in a geographic CRS (EPSG:4326, degrees) | Reprojected all layers to EPSG:32632 and confirmed they match |
| Are there nulls in the fields I need? | Facilities: 0 in name, type, ownership and functional status. Roads: many (71 of 71 unnamed, 66 with no surface, 70 with no lane count in Highway2) | Flagged the road gaps (see section 4) |
| Are there duplicate features? | 0 in every layer | None needed |
| Is the geometry valid? | 0 invalid, 0 empty | None needed |
| Does coverage span the whole study area? | Yes. All features lie inside the ward, and the roads span nearly its full east-west and north-south extent | None needed |

## 4. Problems found, and what I did

1. **Wrong coordinate system for measuring distance.** The data was in degrees, which cannot give correct distances or buffers. I fixed it by reprojecting to EPSG:32632.

2. **Many road attributes are missing.** In Highway2, none of the 71 segments has a name, 66 have no surface information and 70 have no lane count. I flagged this, because it means I cannot judge road quality or whether a road is paved.

3. **Some lines in the road layer are not roads.** 7 of the 71 Highway2 segments are 4 streams, 1 river and 2 administrative boundary lines. They have no road type. I flagged them and will leave them out of the road analysis (the other 64 are roads).

4. **Unknown functional status.** 7 of the 15 facilities are marked "Unknown", so I cannot confirm they are operating. I flagged this.

5. **Warnings in the source data.** GRID3 marked 3 facilities with issues, such as "outside of ward boundary". After clipping, all 15 fall inside my ward boundary, but I flagged their positions as needing care.

6. **Empty fields in the facilities.** The settlement field is empty for all 15, and the alternative name is empty for 8. I flagged this.

## 5. The analysis-ready output

- **File:** `data/processed/okura_ward_analysis.gpkg`
- **Format:** GeoPackage
- **CRS:** EPSG:32632
- **Features:** 15 facilities, 1 Highway1 route, 71 Highway2 segments, 1 ward boundary
- **Produced by:** manually in QGIS (Reproject Layer, then Clip)

---

**Status:** Week 3 complete. First spatial analysis in Week 4, see
[04-month1-summary.md](04-month1-summary.md)