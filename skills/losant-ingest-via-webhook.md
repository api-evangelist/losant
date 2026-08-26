---
name: losant-ingest-via-webhook
description: Take data into a Losant application from a third-party service through an application webhook and a workflow, then debug what the workflow did.
api: openapi/losant-application-api-openapi.yml
operations:
  - webhooks.get
  - webhooks.post
  - webhook.get
  - webhook.patch
  - webhook.delete
  - flowVersions.get
  - flowVersion.patch
  - flows.import
  - flows.palette
  - flow.pressVirtualButton
  - flow.errors
  - flowVersion.errors
  - flow.setStorageEntry
  - flow.clearStorageEntries
  - applicationJobLogs.get
generated: '2026-08-26'
method: generated
source: openapi/losant-application-api-openapi.yml + https://docs.losant.com/applications/webhooks/
---

# Ingest third-party data through a Losant webhook

A webhook is an application-scoped HTTP or WebSocket endpoint whose only job is to fire a Webhook
Trigger inside the Visual Workflow Engine. The workflow does the work.

## Steps

1. **Create the webhook.** `webhooks.post` creates it; the response carries the permanent trigger
   URL (on `https://triggers.losant.com`) that will never change. `webhooks.get` lists existing ones
   first so you do not create a duplicate - there is no idempotency key.
2. **Configure request handling.** `webhook.patch` sets authentication and request verification,
   binary-body casting (integer array by default, or binary string / UTF-8 / base64 / hex), multipart
   file-upload annotation, and whether the webhook replies with the default
   `200 {"success": true}` or with a custom reply from a Webhook Reply Node.
3. **Bind a workflow.** Build the application workflow with a Webhook Trigger. `flows.palette`
   reports which nodes are available in this application, and `flows.import` imports a workflow
   definition wholesale. `flowVersion.patch` and `flowVersions.get` manage the version you deploy.
4. **Test without the third party.** Use a Virtual Button trigger and `flow.pressVirtualButton` to
   run the workflow with a payload you control - 100 presses in a 10-second window per button.
5. **Debug.** `flow.errors` and `flowVersion.errors` return recent execution errors;
   `applicationJobLogs.get` covers long-running work. `flow.setStorageEntry` and
   `flow.clearStorageEntries` read and reset workflow storage between test runs.

## Rules the API will enforce

- **A disabled webhook is invisible, not an error.** HTTP requests to it still return
  `200 {"success": true}` and no trigger fires; WebSocket connections get `404`. Check the `enabled`
  flag before concluding the sender is broken (`asyncapi/losant-event-surface.yml`).
- **Event creation from a workflow is throttled** to 15 in a 15-second window per application, and
  MQTT publishes to 30 in 15 seconds per topic.
- **Deleting a webhook is permanent** and the URL is not reissued.
- **No request-id header.** Correlate through Application Audit Logs (`auditLogs.get`) and workflow
  error logs instead (`conventions/losant-conventions.yml`).
