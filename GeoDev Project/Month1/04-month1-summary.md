# Month 1 Summary

**Week 4 deliverable.** GeoDev Lab Africa, Cohort One.
Author: Praise Soremekun

Spatial Analysis

## 1. My question

What is the spatial distribution of health facilities in Okura Ward, Dekina LGA, Kogi State, and how accessible are these facilities relative to the ward's existing road network?

## 2. Operation I ran and why

I ran a buffer of 2,000 m (2 km) around the 15 health facilities, using 20 segments, in a projected CRS (WGS 84 / UTM Zone 32N, EPSG:32632, so distances are in metres). I chose a buffer because it shows directly which parts of the ward lie within easy reach of a facility, and which do not. I chose 2 km because it is an easy walking distance (about 25 to 30 minutes at walking pace).

I then dissolved the buffers into one shape and clipped it to the Okura Ward boundary, so I could measure the share of the ward that is covered.

## 3. What I expected and what I got

**What I expected (written before running the buffer):**

- 15 buffer features, one for each health facility.
- Each 2 km circle to cover about 12.6 sq km (12,566,000 sq m).
- Some circles to overlap, because some facilities are close together.
- The zones to follow the roads, because most facilities sit along roads. Areas without roads would have no facility within 2 km.
- Together the zones to cover less than half of the ward. Note: my very first guess (about 70%) was made for a 5 km buffer. After I switched to 2 km and looked at the map, I revised it to about 30%.

**What I got:**

- 15 features in the buffer layer, matching my expectation.
- After dissolving and clipping to the ward, the zones cover 129,597,821 sq m (about 129.6 sq km). The ward is 357,931,534 sq m (about 357.9 sq km). So **36.2% of the ward is within 2 km of a health facility**, and about 63.8% is not.
- The circles do overlap in the northwest, the east and the south.

**How I checked the result:**

- **Map:** the circles sit centered on the facilities and look the same size.
- **Row count:** 15 rows in the non-dissolved buffer layer, as expected.
- **One feature by hand:** I measured from one facility to the edge of its circle and got 1,963 m against the expected 2,000 m. The small difference comes from the circle being made of straight segments and from clicking by hand.
- **Empty geometry:** the expression `is_empty_or_null($geometry)` returned no matching features, so there are 0 empty geometries.

## 4. What surprised me

- The coverage was 36.2%, a bit higher than my 30% estimate, but still well under half the ward.
- Facilities do sit along roads, but some roads, especially in the east and across the south, still have no facility within 2 km. So being near a road does not mean being near a facility.

## 5. Data I still need

- Population or settlement data, so I can count how many people live inside and outside the 2 km zones, not just how much land.
- Travel distance along the roads (a network analysis). A buffer only measures straight-line distance, so real travel distances are longer.
- Road surface and condition. Most road attributes in my data are empty (no surface for 66 of 71 minor road segments).
- Functional status of the facilities. 7 of the 15 are marked "Unknown", so I cannot confirm they are operating.
- Cleaner road data. My minor roads layer includes 7 lines that are not roads (streams, a river and administrative boundaries).

---

**Status:** Week 4 and Month 1 complete. See the result map below.

[Okura Ward areas within 2 km of a health facility](../image/health_facilities_2km_okura.png)