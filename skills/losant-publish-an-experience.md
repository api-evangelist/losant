---
name: losant-publish-an-experience
description: Build, version and publish a white-labeled end-user Experience on a Losant application - views, endpoints, users, groups, slugs and custom domains.
api: openapi/losant-experience-api-openapi.yml
operations:
  - experience.bootstrap
  - experienceViews.get
  - experienceViews.post
  - experienceView.patch
  - experienceView.linkedResources
  - experienceEndpoints.post
  - experienceEndpoint.patch
  - experienceEndpoint.linkedResources
  - experienceEndpoints.stats
  - experienceGroups.post
  - experienceUsers.get
  - experienceUsers.post
  - experienceUser.patch
  - experienceVersions.get
  - experienceVersions.post
  - experienceSlugs.post
  - experienceDomains.post
generated: '2026-08-26'
method: generated
source: openapi/losant-experience-api-openapi.yml + https://docs.losant.com/experiences/overview/
---

# Publish a Losant Experience

An Experience is the white-labeled web application layered on top of a Losant Application:
server-rendered views, HTTP endpoints backed by workflows, and its own end-user directory.

## Steps

1. **Bootstrap.** `experience.bootstrap` generates the standard starter set - layouts, pages,
   components, endpoints and the workflows behind them. Run it once on a new application rather
   than hand-building the scaffold.
2. **Author views.** `experienceViews.get` lists views; `experienceViews.post` creates one;
   `experienceView.patch` edits it. Views come in three types - layouts, pages and components.
   Before deleting or renaming, call `experienceView.linkedResources` to see what depends on it.
   For local editing, the Losant CLI syncs the same views to disk (`cli/losant-cli.yml`).
3. **Wire endpoints.** `experienceEndpoints.post` creates an HTTP endpoint; `experienceEndpoint.patch`
   edits it; `experienceEndpoint.linkedResources` shows the workflow and views bound to it.
   `experienceEndpoints.stats` reports request volume once traffic starts.
4. **Set up the user directory.** `experienceGroups.post` creates a group;
   `experienceUsers.post` creates an end user; `experienceUsers.get` lists and filters them;
   `experienceUser.patch` updates one. Experience users are *not* Losant platform users - they
   belong to the application.
5. **Version and release.** `experienceVersions.post` snapshots the current `develop` state as a
   named version; `experienceVersions.get` lists them. A version is the deployable unit - untagged
   work stays on `develop`.
6. **Route traffic.** `experienceSlugs.post` binds a version to a slug on the Losant-hosted domain;
   `experienceDomains.post` attaches a custom domain with its certificate.

## Rules the API will enforce

- **PATCH is partial.** Send only the fields you are changing; omitted fields are left alone.
- **Creates are not idempotent.** There is no idempotency key. If `experienceVersions.post` times
  out, list versions before retrying or you will create a second one.
- **Deleting a version is permanent** - there is no restore path for experience resources
  (`conventions/losant-conventions.yml`).
- **Errors** come back as `{"type": "...", "message": "..."}` with `400` for malformed requests and
  `404` when the `applicationId` or resource id is wrong.
