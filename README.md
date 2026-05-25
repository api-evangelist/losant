# Losant

[Losant](https://www.losant.com/) is an Enterprise IoT Platform that lets product teams build connected experiences, manage fleets of devices, orchestrate edge and embedded compute, and visualize and act on IoT data. This repository is an API Evangelist catalog entry for Losant: it captures the platform's API surface, SDKs, and developer assets, and republishes a machine-readable view of the Losant Platform API in standards-aligned formats.

- Provider: Losant IoT, Inc.
- Type: `company`
- Tier: 1 (real machine-readable API spec)
- Base URL: `https://api.losant.com`
- MQTT broker: `broker.losant.com`
- Source spec: served at `https://api.losant.com/` (Bravado / Swagger 2 dialect, version 1.29.4, 97 resources, 316 definitions)

## APIs

This repo splits the Losant Platform API into nine OpenAPI 3.0 documents aligned to Losant's product surfaces:

| API | OpenAPI Spec | Description |
|---|---|---|
| Authentication and Account | [`openapi/losant-auth-api-openapi.yml`](openapi/losant-auth-api-openapi.yml) | Authenticate users, devices, and SSO; manage signed-in user, personal access tokens, organizations. |
| Application | [`openapi/losant-application-api-openapi.yml`](openapi/losant-application-api-openapi.yml) | Manage Losant Applications and all app-scoped resources: dashboards, events, webhooks, integrations, files, certificates, audit logs, credentials, application keys, API tokens. |
| Device | [`openapi/losant-device-api-openapi.yml`](openapi/losant-device-api-openapi.yml) | Provision and manage IoT devices and device recipes; read state, send commands. |
| Data and Data Tables | [`openapi/losant-data-api-openapi.yml`](openapi/losant-data-api-openapi.yml) | Time-series device data queries and Data Table row CRUD. |
| Workflow Engine | [`openapi/losant-workflow-api-openapi.yml`](openapi/losant-workflow-api-openapi.yml) | Create, version, deploy, debug, and execute Visual Workflow Engine flows. |
| Edge and Embedded Compute | [`openapi/losant-edge-api-openapi.yml`](openapi/losant-edge-api-openapi.yml) | Edge Compute (Linux gateway) and Embedded Edge Agent (EEA, microcontroller) deployments. |
| Experience | [`openapi/losant-experience-api-openapi.yml`](openapi/losant-experience-api-openapi.yml) | White-labeled end-user web Experiences: users, groups, endpoints, views, slugs, domains, versions. |
| Notebooks | [`openapi/losant-notebook-api-openapi.yml`](openapi/losant-notebook-api-openapi.yml) | Trigger Jupyter-style batch executions over historical IoT data. |
| Enterprise Instance | [`openapi/losant-instance-api-openapi.yml`](openapi/losant-instance-api-openapi.yml) | Administer dedicated and self-hosted Losant Enterprise Instances. |

## Authentication

The Losant Platform API uses JSON Web Tokens (JWTs) as Bearer tokens. Obtain one of:

- A user token via `POST /auth/user`
- A device token via `POST /auth/device`
- A personal access token via `POST /me/tokens`
- An application API token via `POST /applications/{applicationId}/tokens`

Pass the JWT as `Authorization: Bearer <token>` on every request.

## Artifacts

| Type | Location |
|---|---|
| OpenAPI 3.0 specs (9) | [`openapi/`](openapi/) |
| JSON Schemas (8 key resources) | [`json-schema/`](json-schema/) |
| JSON Structures (4 narratives) | [`json-structure/`](json-structure/) |
| JSON-LD context | [`json-ld/losant-context.jsonld`](json-ld/losant-context.jsonld) |
| Operation examples (12) | [`examples/`](examples/) |
| Naftiko capabilities (22 per-API + 3 shared) | [`capabilities/`](capabilities/) |
| Spectral rules | [`rules/losant-rules.yml`](rules/losant-rules.yml) |
| Vocabulary | [`vocabulary/losant-vocabulary.yml`](vocabulary/losant-vocabulary.yml) |
| Plans (API Commons Plans 0.1) | [`plans/losant-plans-pricing.yml`](plans/losant-plans-pricing.yml) |
| Rate limits (API Commons 0.1) | [`rate-limits/losant-rate-limits.yml`](rate-limits/losant-rate-limits.yml) |
| FinOps mapping (FOCUS-aligned) | [`finops/losant-finops.yml`](finops/losant-finops.yml) |
| API provider review | [`review.yml`](review.yml) |
| APIs.json catalog | [`apis.yml`](apis.yml) |

## SDKs and Tooling

First-party clients maintained by Losant in [github.com/Losant](https://github.com/Losant):

- REST: [`losant-rest-js`](https://github.com/Losant/losant-rest-js), [`losant-rest-python`](https://github.com/Losant/losant-rest-python), [`losant-rest-ruby`](https://github.com/Losant/losant-rest-ruby)
- MQTT: [`losant-mqtt-js`](https://github.com/Losant/losant-mqtt-js), [`losant-mqtt-python`](https://github.com/Losant/losant-mqtt-python), [`losant-mqtt-ruby`](https://github.com/Losant/losant-mqtt-ruby), [`losant-mqtt-arduino`](https://github.com/Losant/losant-mqtt-arduino), [`losant-esp-idf-esp32`](https://github.com/Losant/losant-esp-idf-esp32)
- CLI: [`losant-cli`](https://github.com/Losant/losant-cli)
- Embedded Edge Agent examples: [`eea-examples`](https://github.com/Losant/eea-examples)
- Application templates: [`application-templates`](https://github.com/Losant/application-templates)
- Community workflow nodes: [`workflow-node-catalog`](https://github.com/Losant/workflow-node-catalog)
- Notebook examples: [`notebook-examples`](https://github.com/Losant/notebook-examples)

## Resources

- Documentation: [docs.losant.com](https://docs.losant.com/)
- Getting Started: [Walkthrough](https://docs.losant.com/getting-started/walkthrough/)
- REST API Overview: [docs.losant.com/rest-api/overview](https://docs.losant.com/rest-api/overview/)
- MQTT Specification: [docs.losant.com/mqtt/overview](https://docs.losant.com/mqtt/overview/)
- Losant University: [docs.losant.com/university/overview](https://docs.losant.com/university/overview/)
- Template Library: [docs.losant.com/template-library/overview](https://docs.losant.com/template-library/overview/)
- Workflow Lab: [docs.losant.com/workflow-lab/overview](https://docs.losant.com/workflow-lab/overview/)
- Solution Guides: [docs.losant.com/guides/overview](https://docs.losant.com/guides/overview/)
- Blog: [losant.com/blog](https://www.losant.com/blog)
- Status: [status.losant.com](https://status.losant.com/)
- Pricing: [losant.com/pricing](https://www.losant.com/pricing) (contact sales)

## Notes on the Conversion

The OpenAPI 3.0 specs in `openapi/` are derived from the Bravado/Swagger-2 document Losant serves at the API root (`GET https://api.losant.com/`). The conversion:

- Splits the 97 resources into nine product-aligned API documents
- Preserves operation summaries, descriptions, parameters, request bodies, and response schemas
- Rewrites `$ref` from `#/definitions/...` to `#/components/schemas/...`
- Computes per-API schema closures so each spec only carries the definitions it actually references
- Applies Title Case to operation summaries
- Documents BearerAuth (JWT) as the single security scheme

Losant's own definitions and schema shapes are unchanged - only the envelope is rewritten to be OpenAPI 3.0 compliant.
