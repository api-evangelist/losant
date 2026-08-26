---
name: losant-data-tables-and-export
description: Model relational data in a Losant Data Table, read and write rows, and get data out of an application safely before any destructive change.
api: openapi/losant-data-and-data-tables-api-openapi.yml
operations:
  - dataTables.get
  - dataTables.post
  - dataTable.get
  - dataTable.patch
  - dataTable.addColumn
  - dataTableRows.get
  - dataTableRow.get
  - dataTableRow.patch
  - dataTableRow.delete
  - dataTableRows.truncate
  - data.export
  - events.export
generated: '2026-08-26'
method: generated
source: openapi/losant-data-and-data-tables-api-openapi.yml + https://docs.losant.com/data-tables/overview/
---

# Work with Losant Data Tables, and export before you destroy

Data Tables are the relational store beside the time-series device data. Time-series telemetry is
queried separately; Data Tables hold the reference and application data workflows join against.

## Steps

1. **Create the table and its shape.** `dataTables.post` creates the table; `dataTable.addColumn`
   adds a typed column; `dataTable.patch` renames it. `dataTables.get` and `dataTable.get` read the
   schema back.
2. **Read rows.** `dataTableRows.get` pages with `page`/`perPage` (default 100), sorts with
   `sortField`/`sortDirection`, and filters with `filterField`/`filter`. For anything more complex,
   pass a `query` object - a MongoDB-style filter that overrides the simple parameters. Responses
   carry both `count` (this page) and `totalCount` (the whole result).
3. **Write rows.** `dataTableRow.patch` updates one row partially; `dataTableRow.delete` removes one.
4. **Export before destroying.** `data.export` and `events.export` are the only rollback Losant
   offers for application data - there is no undo for a truncate. Each export is limited to one
   concurrent call per application and is delivered asynchronously.
5. **Truncate only after the export lands.** `dataTableRows.truncate` empties the table permanently.

## Rules the API will enforce

- **Response size caps.** Data Table Rows: Get and Query return at most 20MB per request, and a
  time-series query at most 30MB. Page rather than widening the range.
- **PATCH is partial**, and there is no idempotency key - a retried write after a timeout is a second
  write (`conventions/losant-conventions.yml`).
- **Reversibility.** Device deletion is restorable for 93 days; data-table truncation and
  `device.removeData` are not restorable at all. Export first
  (`conventions/losant-conventions.yml` -> reversibility).
- **Errors** are `{"type": "...", "message": "..."}` with `400` for malformed requests, and no
  declared `429` or `5xx` even though both occur - handle them anyway.
