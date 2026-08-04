# Turvo (turvo)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Turvo is a collaborative cloud transportation management system (TMS) that unifies shippers, freight brokers, and carriers on a single real-time platform. Its self-service Public API is a JSON REST interface (base `https://publicapi.turvo.com`) secured with OAuth 2.0 plus a per-tenant API key, covering shipments, orders, locations, accounts (customers), and carriers, with event-driven webhooks for status changes and location updates.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/turvo/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/turvo/refs/heads/main/apis.yml)

## Access Model (Honest Note)

Turvo's Public API is **self-service but tenant-gated**, not an openly public developer program:

- The API is available to **Turvo customers**. You obtain a **Client ID, Client Secret, and API Key** from the **API profile inside your Turvo tenant** (the app), then exchange them for an OAuth 2.0 Bearer access token.
- The **interactive API reference** lives behind a Turvo login at [https://app.turvo.com/lobby/documentation](https://app.turvo.com/lobby/documentation). A **sandbox tenant** is available for testing before go-live.
- Because that reference is gated, the **endpoint paths in this catalog are honestly modeled** from Turvo's publicly described resource set (shipments, orders, locations, accounts, carriers, tracking/location updates, and webhooks) rather than copied verbatim from the live spec. Treat the OpenAPI and collections here as a faithful structural model, and confirm exact fields against your tenant's reference. See `review.yml` for the full access and transport assessment.

## Authentication

1. Retrieve `client_id`, `client_secret`, and your `x-api-key` from your Turvo tenant API profile.
2. `POST https://publicapi.turvo.com/v1/oauth/token` with the `x-api-key` header and an OAuth 2.0 grant (Turvo documents a password grant for tenant users) to receive an `access_token`.
3. Call resource endpoints with `Authorization: Bearer {access_token}` and the `x-api-key` header.

## Tags

- Logistics
- Transportation Management System
- TMS
- Supply Chain
- Freight
- Shipments
- Carriers

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs

### Turvo Shipments API

Create, retrieve, list, update, and cancel shipments (loads) - the core freight object in Turvo - including stops, items, costs, carrier assignment, and lifecycle status.

- **Human URL:** [https://help.turvo.com/hc/en-us/sections/12970447299987-API-Documentation](https://help.turvo.com/hc/en-us/sections/12970447299987-API-Documentation)
- **Base URL:** `https://publicapi.turvo.com/v1`

### Turvo Orders API

Manage orders - the customer-facing demand records that group line items and ship-from / ship-to requirements before they are planned into shipments.

- **Human URL:** [https://turvo.com/orders/](https://turvo.com/orders/)
- **Base URL:** `https://publicapi.turvo.com/v1`

### Turvo Locations API

Manage the location master - warehouses, distribution centers, and facilities used as shipment stops - including addresses, geocoordinates, contacts, and operating hours.

- **Human URL:** [https://help.turvo.com/hc/en-us/sections/12970447299987-API-Documentation](https://help.turvo.com/hc/en-us/sections/12970447299987-API-Documentation)
- **Base URL:** `https://publicapi.turvo.com/v1`

### Turvo Accounts API

Manage accounts - the customers, shippers, and business partners in a Turvo tenant - including contacts, billing details, and relationships.

- **Human URL:** [https://help.turvo.com/hc/en-us/sections/12970447299987-API-Documentation](https://help.turvo.com/hc/en-us/sections/12970447299987-API-Documentation)
- **Base URL:** `https://publicapi.turvo.com/v1`

### Turvo Carriers API

Manage carriers - the transportation providers hauling freight - including compliance data, equipment, lanes, and contacts, so loads can be tendered and assigned.

- **Human URL:** [https://turvo.com/carriers/](https://turvo.com/carriers/)
- **Base URL:** `https://publicapi.turvo.com/v1`

### Turvo Tracking API

Post and retrieve real-time tracking - location updates (GPS pings) and status milestones - against a shipment for in-transit visibility, and subscribe to the matching webhook events.

- **Human URL:** [https://help.turvo.com/hc/en-us/sections/12970447299987-API-Documentation](https://help.turvo.com/hc/en-us/sections/12970447299987-API-Documentation)
- **Base URL:** `https://publicapi.turvo.com/v1`

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/turvo)
- [Website](https://turvo.com)
- [Documentation](https://help.turvo.com/hc/en-us/sections/12970447299987-API-Documentation)
- [Plans](plans/turvo-plans-pricing.yml)
- [Rate Limits](rate-limits/turvo-rate-limits.yml)
- [Fin Ops](finops/turvo-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
