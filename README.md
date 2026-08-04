# Fleet Complete (fleetcomplete)

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

Fleet Complete (operating under parent company Powerfleet since its 2024 rebrand) is a global connected commercial vehicle and mobile workforce management platform - GPS/telematics tracking, driver safety, dispatching, geofencing, and regulatory (HOS/ELD) compliance. Its current developer surface is the **Unity API**, a Bearer-token-authenticated GraphQL API at `api.fleetcomplete.com/graphql` covering vehicles, drivers/people, geofences, devices/cameras, groups/roles, and reports/work schedules with roughly 30 queries and 22 mutations. Fleet Complete also still references an older, regionally hosted REST "Integration WebAPI" / EcoFleet-SeeMe surface (versioned v8_5_0/v8_6_1) covering vehicle trip history, tasks/dispatch, work schedules, and logbook reporting.

Standard API access is provided **free** to existing Fleet Complete/Powerfleet clients once they create a token; custom integrations built by Fleet Complete Professional Services carry additional, separately negotiated fees. There is no self-serve, credit-card, pay-as-you-go API product - access is gated behind an active fleet management subscription.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/fleetcomplete/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/fleetcomplete/refs/heads/main/apis.yml)

## Tags

- Fleet Management
- Telematics
- GPS Tracking
- IoT
- GraphQL
- Vehicle Tracking
- Driver Safety
- Geofencing

## Timestamps

- **Created:** 2026-07-03
- **Modified:** 2026-07-03

## APIs

### Fleet Complete Unity Vehicles API

List and filter vehicles (`getVehicles` with `VehicleFilter`), fetch a vehicle by ID or VIN (`getVehicleById`, `getVehiclesByVin`), list active vehicles, read vehicle types and custom fields, inspect mapped sensors, and pull the latest or historical telemetry snapshots (`getLatestSnapshots`, `getSnapshots`) over a date range. Mutations update vehicle attributes/custom fields and move vehicles between groups.

- **Human URL:** [https://api.fleetcomplete.com/](https://api.fleetcomplete.com/)
- **Base URL:** `https://api.fleetcomplete.com/graphql`

#### Properties

- [Documentation](https://www.fleetcomplete.com/api/)
- [API Reference](https://api.fleetcomplete.com/)
- [GraphQL](graphql/fleetcomplete-graphql.md)

### Fleet Complete Unity Drivers & People API

Manage the people and drivers in a fleet - list/filter people, fetch a person by ID, read custom fields, and look up driver-to-vehicle assignments. Mutations create, update, and delete people, set custom roles, assign/unassign drivers to vehicles, and issue, update, or revoke driver identification tokens used for in-cab duty-status login.

- **Human URL:** [https://api.fleetcomplete.com/](https://api.fleetcomplete.com/)
- **Base URL:** `https://api.fleetcomplete.com/graphql`

### Fleet Complete Unity Geofences API

Fetch a geofence by ID or list/filter geofences, then create, update, or delete a geofence and move geofences between groups. Geofences back the zone-entry/exit alerts fleets use for compliance and dispatch.

- **Human URL:** [https://api.fleetcomplete.com/](https://api.fleetcomplete.com/)
- **Base URL:** `https://api.fleetcomplete.com/graphql`

### Fleet Complete Unity Devices & Cameras API

Look up telematics hardware by ID or serial (the older `getDeviceBySerial` is documented as deprecated in favor of `getDevicesBySerial`), and read or set in-cab dash-cam privacy mode.

- **Human URL:** [https://api.fleetcomplete.com/](https://api.fleetcomplete.com/)
- **Base URL:** `https://api.fleetcomplete.com/graphql`

### Fleet Complete Unity Groups & Roles API

Read the organizational groups and roles used to segment vehicles, people, and geofences, and create, update, or delete groups.

- **Human URL:** [https://api.fleetcomplete.com/](https://api.fleetcomplete.com/)
- **Base URL:** `https://api.fleetcomplete.com/graphql`

### Fleet Complete Unity Reports & Scheduling API

Pull "wrapped" report data and its input options, read work schedules by ID or in bulk, read alert/compliance rules, and look up labels, meta-sensor definitions, and the authenticated caller's own profile.

- **Human URL:** [https://api.fleetcomplete.com/](https://api.fleetcomplete.com/)
- **Base URL:** `https://api.fleetcomplete.com/graphql`

### Fleet Complete Legacy Integration WebAPI

Older, regionally hosted OAuth REST surface predating the Unity GraphQL API, still referenced in Fleet Complete/Powerfleet support materials as the "FleetComplete WebAPI" (versioned v8_5_0/v8_6_1) and, on at least one hosted instance, branded EcoFleet/SeeMe. Confirmed resource paths include `Api/Vehicles/get` (vehicle list, live location, trip/raw-data history) and `Api/Places/get` (geofences); the same instance's docs also describe people, dispatch tasks, work schedules, logbook/HOS trip approval, expense tracking, Garmin device messaging, and predefined CSV/XLS/HTML/PDF reports, though their exact paths were not individually confirmed. Standard endpoints are free; custom endpoints built by Fleet Complete Professional Services carry additional fees (contact fcapi@fleetcomplete.com).

- **Human URL:** [https://tlshosted.fleetcomplete.com/Integration/v8_5_0/Help](https://tlshosted.fleetcomplete.com/Integration/v8_5_0/Help)
- **Base URL:** `https://app.ecofleet.com/seeme/services`

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/fleet-complete)
- [Website](https://www.fleetcomplete.com/)
- [Documentation](https://www.fleetcomplete.com/api/)
- [Plans](plans/fleetcomplete-plans-pricing.yml)
- [Rate Limits](rate-limits/fleetcomplete-rate-limits.yml)
- [Fin Ops](finops/fleetcomplete-finops.yml)

## Access Model

There is no public, self-serve API signup. Standard Unity API and legacy Integration WebAPI access is free to existing Fleet Complete/Powerfleet fleet management subscribers - a token is created from the authenticated customer portal. Custom endpoints or fields require engaging Fleet Complete Professional Services for a fee. No documented public WebSocket API exists on either surface (see `review.yml`).

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
