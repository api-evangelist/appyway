---
name: appyway-check-realtime-availability
description: Check live bay occupancy for parking entities you have already identified, using the AppyWay Availability RealTime API.
api: AppyWay Availability RealTime API
base_url: https://api.appyway.com/v1/availability-realtime
generated: '2026-09-04'
method: generated
source: >-
  Grounded in the provider-published contract
  AppyWay-YlpAvailabilityRealTimeApi-v1.oas.json
  (github.com/YellowLineParking/Public-Api-Specs) and
  https://docs.appyway.com/docs/public-docs/dc52a602db4c8-availability-real-time
operations:
- post-findparkingentitiesbyviewport
- post-queries-fetchavailabilitybyentityids
- get-ping
---

# Check real-time availability

Read-only, and the smallest API AppyWay publishes: two operations.

## 1. You need entity ids first

`post-queries-fetchavailabilitybyentityids` does not search. It takes a list of entity ids
you already hold. Get them from the Explorer API — `post-findparkingentitiesbyviewport`
for an area, or ids you cached from an earlier search.

Do not call this API to find parking. Use `appyway-find-parking-nearby` for that, then
bring the ids here.

## 2. Ask for the ids in one call

Send the whole id list in a single request rather than one call per entity. There is no
pagination in this API, and per-endpoint rate limits are unpublished — batching is the
only lever you have.

## 3. Treat the answer as perishable

This is a live occupancy reading, not a reservation and not a guarantee. It tells the
driver what was true when you asked. Nothing in the AppyWay API can hold a bay: there is
no booking operation anywhere in the four published contracts.

Coverage for real-time availability is narrower than coverage for parking rules. An entity
that returns rules from Explorer may return nothing here, and that means unmonitored, not
full.

## 4. Liveness

`get-ping` is the health check. It still requires a valid `API-KEY`, so it is not a public
status signal — AppyWay publishes no status page, and a failing ping is the only signal
you have.

## Errors

401 missing/invalid key, 403 not entitled, 400 validation, 429 rate limited. The error
envelope is `{"success": false, "message": "...", "errors": [{"property","code","message"}]}`,
not RFC 9457 problem+json.
