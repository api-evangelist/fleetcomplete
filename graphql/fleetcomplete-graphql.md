# Fleet Complete Unity GraphQL API

Fleet Complete's current developer surface is the Unity API - a single GraphQL
endpoint covering vehicles, drivers/people, geofences, devices/cameras, groups
and roles, and reports/work schedules for a connected fleet.

**Endpoint:** https://api.fleetcomplete.com/graphql
**Documentation / landing page:** https://www.fleetcomplete.com/api/
**Interactive docs:** https://api.fleetcomplete.com/
**GraphiQL:** https://api.fleetcomplete.com/graphiql?path=/graphql

This file summarizes what is confirmed from Fleet Complete's own published
documentation. The interactive docs are a JavaScript-rendered single-page app
that requires an authenticated session to run live queries against, so no
full SDL/introspection dump could be captured here - the field lists below are
transcribed from the rendered documentation, not fabricated, but argument and
return-type shapes beyond what is named should be verified in the live docs
before integrating.

## Authentication

1. `POST https://api.fleetcomplete.com/login/token` with username/password
   credentials returns an `access_token` (TTL 300 seconds / 5 minutes) and a
   `refresh_token` (usable up to 12 hours).
2. `GET https://api.fleetcomplete.com/login/userinfo` with the Bearer token
   returns the caller's `userId` and available `fleetId` values.
3. Every GraphQL request must include:
   - `Authorization: Bearer <access_token>`
   - `userId: <uuid>` or `fleetId: <uuid>`

## Rate Limiting

The API enforces **only one active request per user at a time**. Issuing a
second request while one is in flight returns `HTTP 429`.

## Query Fields

**Vehicles**
- `getVehicles(filter: VehicleFilter)`
- `getVehicleById`
- `getVehiclesByVin`
- `getActiveVehicles`
- `getVehicleCustomFields`
- `getVehicleMappedSensors`
- `getVehicleTypes`
- `getLatestSnapshots`
- `getSnapshots(vehicleId, from: DateTime, to: DateTime)`

**Drivers & People**
- `getPeople(filter: PersonFilter)`
- `getPersonById`
- `getPersonCustomFields`
- `getDriverAssignments(input: GetDriverAssignmentsInput)` - by `vehicleId` or `driverId`

**Geofences**
- `getGeofenceById`
- `getGeofences(filter: GeofenceFilter)`

**Devices**
- `getDeviceById`
- `getDeviceBySerial` - documented as deprecated, use `getDevicesBySerial`
- `getDevicesBySerial`
- `getCameraPrivacyMode`

**Groups & Roles**
- `getGroups`
- `getRoles`

**Reports, Scheduling & Other**
- `getLabels`
- `getMetaSensors`
- `getUserInfo`
- `getWorkScheduleById`
- `getWorkSchedules`
- `getRuleById`
- `getRules`
- `getWrappedReport`
- `getWrappedReportInputs`

## Mutation Fields

**Vehicles**
- `updateVehicle`
- `updateVehicleCustomField`
- `changeVehicleGroups`
- `changeVehiclesGroup`

**Drivers & People**
- `createPerson`
- `updatePerson`
- `updatePersonCustomField`
- `setPersonCustomRoles`
- `deletePerson`
- `assignDriver`
- `unassignDriver`
- `createDriverToken`
- `updateDriverToken`
- `deleteDriverToken`

**Geofences**
- `createGeofence`
- `updateGeofence`
- `deleteGeofence`
- `changeGeofenceGroups`

**Groups**
- `createGroup`
- `updateGroup`
- `deleteGroup`

**Camera / Privacy**
- `setCameraPrivacyMode`

## Subscriptions

No GraphQL Subscription type or WebSocket real-time push capability is
documented. The Unity API is request/response only.

## Sources

- https://www.fleetcomplete.com/api/
- https://api.fleetcomplete.com/
- https://www.fleetcomplete.com/partner-ecosystem/
