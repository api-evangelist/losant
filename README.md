# Losant (losant)

Losant is an Enterprise IoT Platform that lets product teams build connected experiences, manage fleets of
devices, orchestrate edge and embedded compute, and visualize and act on IoT data. The platform exposes a
comprehensive REST API (the Platform API) covering applications, devices, data tables, time-series data,
events, workflows (visual workflow engine), edge and embedded deployments, end-user experiences,
notebooks, files, integrations, webhooks, dashboards, organizations, audit logs, and self-hosted
enterprise instance administration. Devices may also connect via MQTT. Customers include industrial,
smart-building, agriculture, and connected-product companies; Losant emphasizes white-labeled end-user
experiences ("Experiences") and edge compute on Linux gateways plus microcontrollers via the Embedded
Edge Agent (EEA).

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/losant/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/losant/refs/heads/main/apis.yml)

## Scope

- **Access:** 3rd-Party

## Tags

- IoT
- Internet Of Things
- Devices
- Edge Compute
- Embedded
- MQTT
- Industrial IoT
- Telemetry
- Workflow Automation
- Visual Workflow Engine
- Dashboards
- Time Series
- Connected Products
- Enterprise

## APIs

### Losant Authentication And Account API

Authenticate users, devices, and SSO sessions; manage the currently signed-in user, personal access
tokens, organizations, and organization invites. Returns JWTs used as Bearer tokens for the rest of the
Losant Platform API.

- **Human URL:** [https://docs.losant.com/rest-api/auth/](https://docs.losant.com/rest-api/auth/)
- **Base URL:** `https://api.losant.com`

#### Tags

- Authentication
- Account
- Users
- Organizations
- JWT

#### Properties

- [Documentation](https://docs.losant.com/rest-api/auth/)
- [Documentation](https://docs.losant.com/rest-api/me/)
- [Documentation](https://docs.losant.com/rest-api/org/)
- [OpenAPI](openapi/losant-auth-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/losant-auth-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/losant-auth-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Losant Application API

Manage Losant Applications - the top-level multi-tenant container for IoT solutions - plus all
application-scoped resources: dashboards, events, webhooks, integrations, files, application keys, API
tokens, certificate authorities and certificates for X.509-authenticated devices, application templates,
audit logs, credentials, and long-running resource jobs.

- **Human URL:** [https://docs.losant.com/rest-api/application/](https://docs.losant.com/rest-api/application/)
- **Base URL:** `https://api.losant.com`

#### Tags

- Applications
- Dashboards
- Events
- Webhooks
- Integrations
- Files
- Audit Logs
- Credentials
- Certificates
- API Tokens
- Resource Jobs

#### Properties

- [Documentation](https://docs.losant.com/applications/overview/)
- [Documentation](https://docs.losant.com/rest-api/application/)
- [Documentation](https://docs.losant.com/rest-api/applications/)
- [OpenAPI](openapi/losant-application-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/losant-application-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/losant-application-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/losant-application-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/losant-event-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Structure](json-structure/losant-application-structure.json)

### Losant Device API

Provision and manage IoT devices and device recipes, query device tags and attributes, read connection
state and logs, and publish state or send commands to devices. Devices may also publish state and
receive commands via MQTT (`broker.losant.com`).

- **Human URL:** [https://docs.losant.com/rest-api/device/](https://docs.losant.com/rest-api/device/)
- **Base URL:** `https://api.losant.com`

#### Tags

- Devices
- Device Recipes
- Telemetry
- State
- Commands
- IoT

#### Properties

- [Documentation](https://docs.losant.com/devices/overview/)
- [Documentation](https://docs.losant.com/rest-api/device/)
- [Documentation](https://docs.losant.com/rest-api/devices/)
- [Documentation](https://docs.losant.com/mqtt/overview/)
- [OpenAPI](openapi/losant-device-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/losant-device-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/losant-device-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/losant-device-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Structure](json-structure/losant-device-structure.json)

### Losant Data And Data Tables API

Aggregate, query, and export time-series device data, and read/write rows in Data Tables - Losant's
schemaful relational store for context data that lives alongside IoT telemetry.

- **Human URL:** [https://docs.losant.com/rest-api/data/](https://docs.losant.com/rest-api/data/)
- **Base URL:** `https://api.losant.com`

#### Tags

- Data
- Data Tables
- Time Series
- Telemetry
- Aggregation
- Export

#### Properties

- [Documentation](https://docs.losant.com/data-tables/overview/)
- [Documentation](https://docs.losant.com/rest-api/data/)
- [Documentation](https://docs.losant.com/rest-api/data-table/)
- [Documentation](https://docs.losant.com/rest-api/data-table-rows/)
- [OpenAPI](openapi/losant-data-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/losant-data-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/losant-data-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/losant-data-table-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Structure](json-structure/losant-data-structure.json)

### Losant Workflow Engine API

Create, version, deploy, debug, and execute flows in the Losant Visual Workflow Engine. Supports
Application, Experience, Edge, Embedded, and Custom Node workflow types with full version history and
rollback.

- **Human URL:** [https://docs.losant.com/rest-api/flow/](https://docs.losant.com/rest-api/flow/)
- **Base URL:** `https://api.losant.com`

#### Tags

- Workflows
- Visual Workflow Engine
- Automation
- Orchestration
- Versioning

#### Properties

- [Documentation](https://docs.losant.com/workflows/overview/)
- [Documentation](https://docs.losant.com/rest-api/flow/)
- [Documentation](https://docs.losant.com/rest-api/flows/)
- [Documentation](https://docs.losant.com/rest-api/flow-version/)
- [OpenAPI](openapi/losant-workflow-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/losant-workflow-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/losant-workflow-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Losant Edge And Embedded Compute API

Manage Losant Edge Compute deployments to Linux gateways (Gateway Edge Agent) and Embedded Edge Agent
(EEA) deployments to microcontrollers. Distribute workflow versions to fleets, track deployment state,
and roll back releases.

- **Human URL:** [https://docs.losant.com/rest-api/edge-deployment/](https://docs.losant.com/rest-api/edge-deployment/)
- **Base URL:** `https://api.losant.com`

#### Tags

- Edge Compute
- Embedded
- EEA
- Deployments
- Gateways
- Microcontrollers

#### Properties

- [Documentation](https://docs.losant.com/edge-compute/overview/)
- [Documentation](https://docs.losant.com/rest-api/edge-deployment/)
- [Documentation](https://docs.losant.com/rest-api/embedded-deployment/)
- [OpenAPI](openapi/losant-edge-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/losant-edge-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/losant-edge-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Losant Experience API

Build white-labeled end-user web Experiences on top of a Losant Application: experience users, groups,
HTTP endpoints, server-rendered views, slugs, custom domains, versions, and the Experience publishing
pipeline.

- **Human URL:** [https://docs.losant.com/rest-api/experience/](https://docs.losant.com/rest-api/experience/)
- **Base URL:** `https://api.losant.com`

#### Tags

- Experiences
- End User
- White Label
- Web
- Users
- Groups
- Endpoints
- Views

#### Properties

- [Documentation](https://docs.losant.com/experiences/overview/)
- [Documentation](https://docs.losant.com/rest-api/experience/)
- [Documentation](https://docs.losant.com/rest-api/experience-users/)
- [Documentation](https://docs.losant.com/rest-api/experience-endpoint/)
- [OpenAPI](openapi/losant-experience-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/losant-experience-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/losant-experience-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Losant Notebooks API

Trigger and manage Losant Notebook executions - Jupyter-style batch workloads that operate on historical
device data, data table contents, and other application state for analytics, ML, and reporting.

- **Human URL:** [https://docs.losant.com/rest-api/notebook/](https://docs.losant.com/rest-api/notebook/)
- **Base URL:** `https://api.losant.com`

#### Tags

- Notebooks
- Jupyter
- Batch
- Analytics
- Reporting
- Data Science

#### Properties

- [Documentation](https://docs.losant.com/notebooks/overview/)
- [Documentation](https://docs.losant.com/rest-api/notebook/)
- [OpenAPI](openapi/losant-notebook-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/losant-notebook-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/losant-notebook-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Losant Enterprise Instance API

Administer dedicated or self-hosted Losant Enterprise Instances: instance members, organizations within
the instance, organization members and invites, instance-level custom workflow nodes, sandboxes,
notification rules, instance-level API tokens, and audit logs.

- **Human URL:** [https://docs.losant.com/rest-api/instance/](https://docs.losant.com/rest-api/instance/)
- **Base URL:** `https://api.losant.com`

#### Tags

- Enterprise
- Instance
- Self Hosted
- Administration
- Custom Nodes
- Sandboxes
- Notification Rules

#### Properties

- [Documentation](https://docs.losant.com/rest-api/instance/)
- [Documentation](https://docs.losant.com/rest-api/instance-org/)
- [Documentation](https://docs.losant.com/rest-api/instance-custom-node/)
- [OpenAPI](openapi/losant-instance-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/losant-instance-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/losant-instance-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Portal](https://www.losant.com/)
- [Documentation](https://docs.losant.com/)
- [Getting Started](https://docs.losant.com/getting-started/walkthrough/)
- [Documentation](https://docs.losant.com/rest-api/overview/)
- [Documentation](https://docs.losant.com/mqtt/overview/)
- [Documentation](https://docs.losant.com/cli/overview/)
- [Education](https://docs.losant.com/university/overview/)
- [Templates](https://docs.losant.com/template-library/overview/)
- [Documentation](https://docs.losant.com/workflow-lab/overview/)
- [Guides](https://docs.losant.com/guides/overview/)
- [Source Code](https://github.com/Losant)
- [SDK](https://github.com/Losant/losant-rest-js)
- [SDK](https://github.com/Losant/losant-rest-python)
- [SDK](https://github.com/Losant/losant-rest-ruby)
- [SDK](https://github.com/Losant/losant-mqtt-js)
- [SDK](https://github.com/Losant/losant-mqtt-python)
- [SDK](https://github.com/Losant/losant-mqtt-ruby)
- [SDK](https://github.com/Losant/losant-mqtt-arduino)
- [SDK](https://github.com/Losant/losant-esp-idf-esp32)
- [C L I](https://github.com/Losant/losant-cli)
- [Source Code](https://github.com/Losant/eea-examples)
- [Source Code](https://github.com/Losant/notebook-examples)
- [Source Code](https://github.com/Losant/application-templates)
- [Source Code](https://github.com/Losant/workflow-node-catalog)
- [Blog](https://www.losant.com/blog)
- [Status Page](https://status.losant.com/)
- [Pricing](https://www.losant.com/pricing)
- [Support](https://www.losant.com/contact)
- [LinkedIn](https://www.linkedin.com/company/losant/)
- [Twitter](https://x.com/losantiot)
- [Plans](plans/losant-plans-pricing.yml)
- [Rate Limits](rate-limits/losant-rate-limits.yml)
- [Fin Ops](finops/losant-finops.yml)
- [Vocabulary](vocabulary/losant-vocabulary.yml)
- [Spectral Rules](rules/losant-rules.yml)
- [JSON-LD](json-ld/losant-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

## Maintainers

**FN:** Kin Lane
**Email:** info@apievangelist.com
