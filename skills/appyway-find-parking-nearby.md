---
name: appyway-find-parking-nearby
description: Answer "where can I park here, for how long, and what will it cost" for a point in the UK, using the AppyWay Explorer API with a specific vehicle and driver context.
api: AppyWay Explorer API
base_url: https://api.appyway.com/v1/explorer
generated: '2026-09-04'
method: generated
source: >-
  Grounded in the provider-published contract AppyWay-YlpExplorerApi-v1.oas.json
  (github.com/YellowLineParking/Public-Api-Specs) and the guides Key Concepts and
  How to Search for Parking using Explorer at docs.appyway.com. Every operationId below
  was read out of that contract; none is invented.
operations:
- post-fetchallvehicletypes
- post-fetchallfueltypes
- post-fetchallactivitytypes
- post-fetchallpermittypes
- post-findparkingquotesbycentreandviewportsize
- post-findparkingquotesbyviewport
- post-fetchparkingquotebyid
- post-fetchpaymentprovidersbyparkingentityid
---

# Find parking near a point

Read-only. Nothing in this flow changes state, so there is nothing to confirm with the
user before calling and nothing to undo afterwards.

## Before you start

Send `API-KEY: <key>` on every request. Keys come from AppyWay by email
(apisupport@appyway.com) — an agent cannot obtain one itself, so if you get a 401, stop
and tell the user they need a key rather than retrying.

## 1. Build the vehicle operator context

AppyWay's answer depends on who is asking. Resolve the ids first from the Reference API
at `https://api.appyway.com/v1/reference` — these are controlled vocabularies, not free text:

- `post-fetchallactivitytypes` — parking vs loading
- `post-fetchallvehicletypes` — car, motorcycle, goods vehicle
- `post-fetchallfueltypes` — petrol, diesel, electric
- `post-fetchallpermittypes` — resident, disabled badge, car club

Cache these. They change rarely and all 25 Reference reads support conditional requests
(304 Not Modified), so re-fetch with the eTag rather than pulling the whole list again.

If the user has not told you the vehicle, ask. Guessing a fuel type can change whether a
bay is usable and what it costs.

## 2. Search around the point

Call `post-findparkingquotesbycentreandviewportsize` with the centre lat/lng, a viewport
size, the vehicle operator context, and the time window the user cares about. Use
`post-findparkingquotesbyviewport` instead when you already have a bounding box — for
example when you are following a map the user is panning.

## 3. Read the answer honestly

Each result carries `cost`, `currency`, `minCost`, `maxStay`-style bounds
(`minStayUntil`, `canExtendUntil`, `pricedUntil`), `noReturnUntil`, `freeUntil`,
`becomesFreeAt` and `isFreeParking`. Report the time bounds, not just the price — "£2.40,
maximum stay two hours, no return within one hour" is the useful answer.

The response also carries `generalOnStreetPolicy` for kerb AppyWay has not mapped:
`Restricted`, `LikelyRestricted`, `LikelyUnrestricted` or `Unknown`. This is an
inference, not a rule. Never present it as a regulation; say the area is unmapped and
that the driver must check the signs on the street.

## 4. Tell them how to pay

`post-fetchpaymentprovidersbyparkingentityid` returns the provider name, a card payment
URL, a payments telephone number and app deep links for the chosen entity.

## Errors

- 401 — key missing or invalid. Not retryable by the agent.
- 403 — the key is not entitled to that local authority. Not retryable; the user must ask
  AppyWay to extend the key.
- 400 — validation failure. `errors[]` names each offending `property` with a `code`
  (`Format`, `Other`, `CannotPerformAction`). Fix and retry; never retry unchanged.
- 404 — on a by-id read, the entity is not known. Re-resolve through a viewport search.
- 429 — rate limited. Limits are unpublished and differ per endpoint, and no
  `Retry-After` header is guaranteed. Back off exponentially with jitter.

Errors are not RFC 9457. The envelope is
`{"success": false, "message": "...", "errors": [...]}`.
