---
name: losant-provision-devices
description: Provision and configure devices in a Losant application from a device recipe, define their attributes, and read back connection state and payload usage.
api: openapi/losant-device-api-openapi.yml
operations:
  - deviceRecipes.get
  - deviceRecipes.post
  - deviceRecipe.get
  - deviceRecipe.bulkCreate
  - deviceAttributes.get
  - deviceAttributes.post
  - deviceAttribute.patch
  - device.patch
  - devices.patch
  - devices.getCompositeState
  - device.payloadCountsBreakdown
  - devices.payloadCounts
generated: '2026-08-26'
method: generated
source: openapi/losant-device-api-openapi.yml + https://docs.losant.com/devices/overview/
---

# Provision devices in a Losant application

Losant's tenancy boundary is the **Application**. Every operation below needs an
`applicationId`, and nothing crosses application boundaries.

## Before you start

- Authenticate: `Authorization: Bearer <token>`. Use an Application API Token scoped to this
  application rather than a full-access User token (`authentication/losant-authentication.yml`).
- Every id is a 24-character hex ObjectId (`^[A-Fa-f\d]{24}$`). An id carries no type prefix, so
  read the `_type` field on the response to know what you were handed.
- Base URL: `https://api.losant.com`. There is no version segment and no test mode - a free
  Developer Sandbox account is the rehearsal environment (`sandbox/losant-sandbox.yml`).

## Steps

1. **Find or create the recipe.** `deviceRecipes.get` lists the application's recipes; page with
   `page`/`perPage` and filter with `filterField`/`filter` (glob supported). If none fits, create one
   with `deviceRecipes.post`. A recipe is the template - attributes, tags, device class - that new
   devices inherit.
2. **Bulk-create the fleet.** `deviceRecipe.bulkCreate` creates many devices from one recipe in a
   single call. This is a **create**, not an upsert: Losant publishes no idempotency-key contract
   (`conventions/losant-conventions.yml`), so a retry after a timeout will create duplicates. Before
   retrying, list devices filtered on the name or tag you used and reconcile.
3. **Confirm and adjust attributes.** `deviceAttributes.get` reads a device's attribute list;
   `deviceAttributes.post` adds one; `deviceAttribute.patch` renames or retypes one. Attribute names
   are the keys a device publishes in its MQTT state payload, so they must match what the firmware
   sends (`asyncapi/losant-event-surface.yml`).
4. **Tag and edit devices.** `device.patch` updates a single device; `devices.patch` updates the
   fields of many devices at once and may answer **202** with a `jobEnqueuedResult` rather than
   completing inline - poll `resourceJobs.get` when it does.
5. **Read state.** `devices.getCompositeState` returns the last complete state for the matching
   devices. `device.payloadCountsBreakdown` and `devices.payloadCounts` report payload usage per
   resolution over a time range, which is how you check ingest is actually flowing.

## Rules the API will enforce

- **Throttles are per endpoint, not per account.** State and command writes are limited to 30 calls
  in a 15-second window per device; `devices.payloadCounts` is one concurrent call per application.
  There are no rate-limit response headers - you will only see `429`
  (`rate-limits/losant-rate-limits.yml`).
- **Errors are not RFC 9457.** Every failure is `application/json` shaped
  `{"type": "...", "message": "..."}`. A `404` on a device usually means the wrong `applicationId`,
  not a missing device (`errors/losant-problem-types.yml`).
- **Deleting a device is reversible for 93 days** and is the only destructive action Losant restores.
  Everything else - `device.removeData`, `dataTableRows.truncate` - is permanent
  (`conventions/losant-conventions.yml`).
