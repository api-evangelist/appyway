# AppyWay (appyway)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

AppyWay leverages innovative technology to transform outdated parking systems and urban mobility infrastructure. By providing real-time data and insights, they enable cities and businesses to optimize traffic flow, reduce congestion, and improve access to parking. Through their smart parking solutions, AppyWay simplifies the parking experience for drivers while also helping to create more sustainable and efficient urban environments.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/appyway/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/appyway/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party

## Tags

- Parking
- Traffic
- Urban Mobility
- Smart Cities
- EV Charging

## Timestamps

- **Created:** 2025-02-08
- **Modified:** 2026-04-19

## APIs

### AppyWay Availability RealTime API

AppyWay Availability RealTime API allows businesses to access real-time data on parking availability, traffic congestion, and road closure information. This API provides up-to-the-minute updates on parking spots, helping users find and reserve parking spaces quickly and easily. By providing this information in real-time, businesses can improve customer satisfaction and reduce the frustration of searching for parking.

- **Human URL:** [https://docs.appyway.com/docs/public-docs/dc52a602db4c8-availability-real-time](https://docs.appyway.com/docs/public-docs/dc52a602db4c8-availability-real-time)

#### Tags

- Congestion
- Parking
- Road Closure
- Traffic

#### Properties

- [OpenAPI](openapi/appyway-availability-realtime-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/appyway-availability-realtime-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/appyway-availability-realtime-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://docs.appyway.com/docs/public-docs/dc52a602db4c8-availability-real-time)
- [JSON Schema](json-schema/parking-availability-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Structure](json-structure/parking-availability-structure.json)
- [Example](examples/parking-availability-example.json)
- [JSON-LD](json-ld/appyway-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [Spectral Rules](rules/appyway-spectral-rules.yml)
- [Vocabulary](vocabulary/appyway-vocabulary.yaml)

### AppyWay Traffic Data API

The AppyWay Traffic Data API provides real-time and historical traffic data for developers to integrate into their applications. This data includes information on traffic congestion, accidents, road closures, and other key events that can impact a driver's journey. By utilizing this API, developers can provide their users with up-to-date traffic information, optimize routes for more efficient travel, and enhance overall road safety.

- **Human URL:** [https://docs.appyway.com/docs/public-docs/7cb87b08d16a7-traffic-data](https://docs.appyway.com/docs/public-docs/7cb87b08d16a7-traffic-data)

#### Tags

- Historical
- Real-Time
- Traffic

#### Properties

- [OpenAPI](openapi/appyway-traffic-data-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/appyway-traffic-data-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/appyway-traffic-data-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://docs.appyway.com/docs/public-docs)

### AppyWay Explorer API

The AppyWay Explorer API allows developers to access a wealth of data related to parking and electric vehicle charging infrastructure. With this API, developers can seamlessly integrate real-time information such as parking availability, pricing, and location details into their own applications. This allows for improved user experience and convenience for drivers seeking parking spaces or charging stations.

- **Human URL:** [https://docs.appyway.com/docs/public-docs/c655badabdcf0-explorer](https://docs.appyway.com/docs/public-docs/c655badabdcf0-explorer)

#### Tags

- Electrical Vehicle Charging
- Parking

#### Properties

- [OpenAPI](openapi/appyway-explorer-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/appyway-explorer-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/appyway-explorer-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://docs.appyway.com/docs/public-docs/c655badabdcf0-explorer-api)

### AppyWay Platform API

AppyWay Platform API allows developers to access a wide range of data related to parking, traffic, and mobility. With this API, developers can integrate real-time parking availability, traffic flow information, and electric vehicle charging locations into their own applications. This enables users to quickly find parking spaces, plan their routes to avoid congestion, and locate nearby charging stations for their electric vehicles.

- **Human URL:** [https://docs.appyway.com/docs/public-docs/f19a03a1ac8f5-reference](https://docs.appyway.com/docs/public-docs/f19a03a1ac8f5-reference)

#### Tags

- Parking
- Traffic

#### Properties

- [OpenAPI](openapi/appyway-platform-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/appyway-platform-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/appyway-platform-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://docs.appyway.com/docs/public-docs/f19a03a1ac8f5-reference)

## Common Properties

- [GitHub Organization](https://github.com/YellowLineParking)
- [LinkedIn](https://www.linkedin.com/company/appyway)
- [Blog](https://appyway.com/blog/)
- [Blog R S S](https://appyway.com/blog/feed/)
- [Events](https://appyway.com/london-council-workshop-oct-22/)
- [Case Studies](https://appyway.com/case-studies/)
- [Press Releases](https://appyway.com/press/)
- [Webinars](https://appyway.com/resources/#webinars)
- [Partners](https://appyway.com/partnerships/)
- [Authentication](https://docs.appyway.com/docs/public-docs/50055c042f423-authentication)
- [Rate Limits](https://docs.appyway.com/docs/public-docs/319adf4695d05-rate-limiting)
- [Integrations](https://appyway.com/integrations)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
