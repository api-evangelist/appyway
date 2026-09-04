---
name: appyway-extract-authority-restrictions
description: Pull a whole UK local authority's kerbside traffic restrictions out of AppyWay as GeoJSON or DXF for use in GIS or CAD, using the Traffic Data API.
api: AppyWay Traffic Data API
base_url: https://api.appyway.com/v1/traffic-data
generated: '2026-09-04'
method: generated
source: >-
  Grounded in the provider-published contract AppyWay-YlpCmsDataApi-v1.oas.json
  (github.com/YellowLineParking/Public-Api-Specs) and the guides How to Fetch Parking Data
  for an Authority and How to Add Traffic Data to GIS Software at docs.appyway.com.
operations:
- post-fetchallauthorities
- post-fetchfullauthorityinfobyslug
- post-fetchfullauthoritybyslug
- get-exportauthorityrestrictionsbyslug-slug-geojson
- get-exportauthorityrestrictionsbyid-authorityid-geojson
- get-exportauthoritymovingrestrictionsbyid-authorityid-geojson
- get-exportauthorityrestrictionsbyslug-slug-dxf
- get-wfs
---

# Extract an authority's restrictions

Read-only. These are bulk extracts of a whole local authority, so they are large and they
count against an unpublished per-endpoint rate limit. Pull once and cache.

## 1. Resolve the authority

`post-fetchallauthorities` lists every authority AppyWay covers. Match the user's council
name to a `slug` — the export routes are slug-addressed, and the slug is the stable handle.
`post-fetchfullauthorityinfobyslug` gives you the metadata for one authority without
pulling its geometry.

If the authority is not in the list, AppyWay does not cover it. Say so; do not fall back
to a neighbouring authority.

## 2. Choose the format the destination actually wants

- `get-exportauthorityrestrictionsbyslug-slug-geojson` — restriction geometry as GeoJSON.
  This is the right answer for QGIS, ArcGIS, Leaflet, Mapbox or anything that speaks
  RFC 7946. No bespoke connector needed.
- `get-exportauthoritymovingrestrictionsbyid-authorityid-geojson` — moving-traffic
  restrictions rather than kerbside ones. Different dataset; addressed by authority id,
  not slug.
- `get-exportauthorityrestrictionsbyslug-slug-dxf` — the same restriction geometry as DXF,
  for a highways engineer working in CAD.
- `get-wfs` — an OGC Web Feature Service query over the same data, for a GIS client that
  prefers to connect live rather than take a file. The endpoint is
  `https://api.appyway.com/v1/traffic-data/wfs` and it is behind the same API-KEY header,
  so a plain anonymous `GetCapabilities` will return 401.

For the structured JSON rather than a geospatial file, use `post-fetchfullauthoritybyslug`.

## 3. Note what you pulled

There is no changelog on these datasets and no Sunset or Deprecation header anywhere in
the API. Record the authority slug and the date you extracted, because a later extract
that differs gives you no other way to tell what changed.

## Errors

Same envelope and same codes as every AppyWay API: 401 missing/invalid key, 403 key not
entitled to that authority (the message names the authority GUID), 400 validation with a
populated `errors[]`, 429 rate limited. Back off exponentially with jitter on 429.
