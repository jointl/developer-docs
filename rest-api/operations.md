---
title: Jointl operation reference
description: The Jointl API provides 31 read operations and 25 protected write operations.
---

The Jointl API provides 31 read operations and 25 protected write operations. Use the bundled OpenAPI and JSON Schema files for exact field constraints and nested data models.

Read operations use `POST /api/v1/operations/{operationId}`. Writes use `POST /api/v1/actions/prepare`, an explicit human approval checkpoint, and `POST /api/v1/actions/confirm`. The Zapier-only execute route is identified where applicable.

## Index

| Operation | Kind | Scope | MCP | Zapier action |
| --- | --- | --- | --- | --- |
| [`workspace.get`](#workspace-get) | read | `workspace.read` | yes | no |
| [`workspace.search`](#workspace-search) | read | `workspace.read` | yes | no |
| [`companies.list`](#companies-list) | read | `workspace.read` | yes | no |
| [`flows.list`](#flows-list) | read | `workspace.read` | yes | no |
| [`flows.get`](#flows-get) | read | `workspace.read` | yes | no |
| [`flows.capabilities.get`](#flows-capabilities-get) | read | `workspace.read` | yes | no |
| [`flows.templates.list`](#flows-templates-list) | read | `workspace.read` | yes | no |
| [`flows.questions.search`](#flows-questions-search) | read | `workspace.read` | yes | no |
| [`flows.referenceTemplates.list`](#flows-referencetemplates-list) | read | `workspace.read` | yes | no |
| [`flows.blueprint.get`](#flows-blueprint-get) | read | `workspace.read` | yes | no |
| [`performance.operations.get`](#performance-operations-get) | read | `workspace.read` | yes | no |
| [`glowMoments.send`](#glowmoments-send) | write | `workspace.write` | yes | no |
| [`glowMoments.cycle.status.set`](#glowmoments-cycle-status-set) | write | `workspace.write` | yes | no |
| [`teamPulse.send`](#teampulse-send) | write | `workspace.write` | yes | no |
| [`teamPulse.cycle.status.set`](#teampulse-cycle-status-set) | write | `workspace.write` | yes | no |
| [`checks.list`](#checks-list) | read | `workspace.read` | yes | no |
| [`checks.analytics`](#checks-analytics) | read | `workspace.read` | yes | no |
| [`checks.get`](#checks-get) | read | `workspace.read` | yes | no |
| [`checks.report`](#checks-report) | read | `workspace.read` | yes | no |
| [`checks.verifications.get`](#checks-verifications-get) | read | `workspace.read` | no | no |
| [`checks.verifications.runAll`](#checks-verifications-runall) | write | `workspace.write` | no | yes |
| [`checks.publicProfiles.get`](#checks-publicprofiles-get) | read | `workspace.read` | no | no |
| [`checks.publicProfiles.find`](#checks-publicprofiles-find) | write | `workspace.write` | no | yes |
| [`references.list`](#references-list) | read | `workspace.read` | yes | no |
| [`references.get`](#references-get) | read | `workspace.read` | yes | no |
| [`employees.list`](#employees-list) | read | `workspace.read` | yes | no |
| [`employees.analytics`](#employees-analytics) | read | `workspace.read` | yes | no |
| [`employees.get`](#employees-get) | read | `workspace.read` | yes | no |
| [`employees.exitIntelligence.get`](#employees-exitintelligence-get) | read | `workspace.read` | no | no |
| [`talents.list`](#talents-list) | read | `workspace.read` | yes | no |
| [`talents.get`](#talents-get) | read | `workspace.read` | yes | no |
| [`talents.references.list`](#talents-references-list) | read | `workspace.read` | yes | no |
| [`autopilots.list`](#autopilots-list) | read | `workspace.read` | yes | no |
| [`autopilots.get`](#autopilots-get) | read | `workspace.read` | yes | no |
| [`insights.get`](#insights-get) | read | `workspace.read` | yes | no |
| [`events.list`](#events-list) | read | `workspace.read` | no | no |
| [`events.get`](#events-get) | read | `workspace.read` | no | no |
| [`flows.draft.create`](#flows-draft-create) | write | `workspace.write` | yes | no |
| [`flows.draft.revise`](#flows-draft-revise) | write | `workspace.write` | yes | no |
| [`flows.status.set`](#flows-status-set) | write | `workspace.write` | yes | no |
| [`flows.delete`](#flows-delete) | write | `workspace.write` | yes | no |
| [`checks.status.set`](#checks-status-set) | write | `workspace.write` | yes | yes |
| [`checks.delete`](#checks-delete) | write | `workspace.write` | yes | no |
| [`employees.status.set`](#employees-status-set) | write | `workspace.write` | yes | yes |
| [`employees.delete`](#employees-delete) | write | `workspace.write` | yes | no |
| [`talents.status.set`](#talents-status-set) | write | `workspace.write` | yes | yes |
| [`autopilots.create`](#autopilots-create) | write | `workspace.write` | yes | no |
| [`autopilots.links.generate`](#autopilots-links-generate) | write | `workspace.write` | yes | no |
| [`autopilots.status.set`](#autopilots-status-set) | write | `workspace.write` | yes | no |
| [`autopilots.delete`](#autopilots-delete) | write | `workspace.write` | yes | no |
| [`references.request`](#references-request) | write | `workspace.write` | yes | yes |
| [`checks.bulkCreate`](#checks-bulkcreate) | write | `workspace.write` | yes | yes |
| [`employees.bulkImport`](#employees-bulkimport) | write | `workspace.write` | yes | yes |
| [`checks.addNote`](#checks-addnote) | write | `workspace.write` | yes | yes |
| [`employees.addNote`](#employees-addnote) | write | `workspace.write` | yes | yes |
| [`talents.addNote`](#talents-addnote) | write | `workspace.write` | yes | yes |

## workspace.get

Return the current Jointl workspace and the access granted to the member.

Use when: Call once at the start of a task that depends on workspace identity, company scope, or permissions; do not use it to discover domain records.

Returns: workspace ID, workspace name, member identity, accessible companies, and granted permission keys.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/workspace.get`
- MCP: `jointl_workspace_get`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

This operation takes an empty object.

### Request example

```json
{
  "input": {}
}
```

### Success example

```json
{
  "data": {
    "companyScope": {
      "mode": "all"
    },
    "grantedPermissions": [
      "flows.view"
    ],
    "member": {
      "id": "member_example_01",
      "name": "Ada Example",
      "roleId": "owner"
    },
    "name": "Example Workspace",
    "workspaceId": "workspace_example_01"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/workspace.get.json).

## workspace.search

Quickly search the connected workspace across authorized people, emails, attributes, companies, tags, job titles, and Flows using the same permissions and relevance ranking as the Jointl UI. An optional source-type filter is applied before ranking. Returns at most 30 top matches and is not an exhaustive list.

Use when: Use for quick entity lookup from a name, email, attribute, company, tag, job title, or Flow phrase; optionally restrict source types before ranking, and use a domain list or analytics operation for complete cohorts.

Returns: ranked matches in `sourceRecords`, suggested next operations in `followUpOperations`, result counts, the applied limit, and `exhaustive: false`.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/workspace.search`
- MCP: `jointl_workspace_search`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `entityTypes` | array | No | Optional source-type filter applied before ranking. Omit it to search every global-search type. |
| `limit` | integer | No | See the JSON Schema definition. |
| `query` | string | Yes | Search people, emails, attributes, companies, tags, job titles, and Flows. |

### Request example

```json
{
  "input": {
    "query": "Ada Example"
  }
}
```

### Success example

```json
{
  "data": {
    "exhaustive": false,
    "items": [
      {
        "entityId": "applicant_example_01",
        "entityType": "applicant",
        "followUpOperations": [
          {
            "input": {
              "applicantId": "applicant_example_01",
              "includeEvidence": true
            },
            "operationId": "checks.get"
          }
        ],
        "label": "Ada Example",
        "sourceRecords": [
          {
            "applicantId": "applicant_example_01",
            "companyName": "Example Company",
            "entityId": "applicant_example_01",
            "entityType": "applicant",
            "label": "Applicant",
            "primary": "Software Engineer",
            "route": "/checks/applicant_example_01",
            "statusLabels": [
              {
                "className": "new",
                "label": "New",
                "value": "new"
              }
            ]
          }
        ]
      }
    ],
    "query": "Ada Example",
    "resultLimit": 30,
    "returnedCount": 1
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/workspace.search.json).

## companies.list

List Jointl companies visible through the member’s current company scope.

Use when: Use before a scoped Flow, Employee import, or other action needs an exact Jointl company ID.

Returns: a cursor-paginated list of company IDs, names, statuses, and creation timestamps.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/companies.list`
- MCP: `jointl_companies_list`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `cursor` | object | No | See the JSON Schema definition. |
| `includeArchived` | boolean | No | Include archived companies; active companies are returned by default. |
| `limit` | integer | No | See the JSON Schema definition. |

### Request example

```json
{
  "input": {}
}
```

### Success example

```json
{
  "data": {
    "hasMore": false,
    "items": [
      {
        "_id": "_id_example_01",
        "name": "Ada Example",
        "status": "active"
      }
    ],
    "nextCursor": null
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/companies.list.json).

## flows.list

List Flows available through the member’s role, sharing, ownership, and company access.

Use when: Use to browse or filter a Flow cohort; use flows.get for one Flow or flows.blueprint.get only for authoring a revision.

Returns: a cursor-paginated list of Flow summaries with activity, company, tags, type, status, and IDs.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/flows.list`
- MCP: `jointl_flows_list`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `activeOnly` | boolean | No | Return only active Flows when true. |
| `cursor` | object | No | See the JSON Schema definition. |
| `includeActivity` | boolean | No | Include aggregate activity counts. Disable for lightweight selectors and dropdowns. |
| `includeUnscopedCompanies` | boolean | No | When company filters are supplied, also include authorized Flows with no company. |
| `limit` | integer | No | See the JSON Schema definition. |
| `selectedCompanies` | array | No | Exact Jointl company IDs from companies.list; empty means every authorized company. |
| `selectedFlowStatus` | array | No | Exact Flow statuses; empty means every authorized status. |
| `selectedTags` | array | No | Exact Jointl tag IDs; empty means every tag. |
| `type` | `HIRING_REVIEW` | `PERFORMANCE` | `EXIT_INTELLIGENCE` | No | Optionally return one exact enabled Flow type. |

### Request example

```json
{
  "input": {}
}
```

### Success example

```json
{
  "data": {
    "hasMore": false,
    "items": [
      {
        "_id": "_id_example_01",
        "status": "active",
        "title": "Example title",
        "type": "HIRING_REVIEW"
      }
    ],
    "nextCursor": null
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/flows.list.json).

## flows.get

Get one visible Flow. Sensitive automation tokens are never returned.

Use when: Use for the operational details of one Flow; use flows.blueprint.get instead when preparing a draft revision.

Returns: the authorized Flow details, related company, job role, tags, sharing members, and automation status summaries.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/flows.get`
- MCP: `jointl_flows_get`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `flowId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "input": {
    "flowId": "flowid_example_01"
  }
}
```

### Success example

```json
{
  "data": {
    "_id": "_id_example_01",
    "status": "active",
    "title": "Example title",
    "type": "HIRING_REVIEW"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/flows.get.json).

## flows.capabilities.get

Read supported Flow types, sections, question types, valid section ordering, current authoring permissions, and protected actions before proposing a Flow.

Use when: Call before creating or substantially redesigning a Flow so the proposed design uses only supported sections and question types.

Returns: supported types and sections, authoring limits, current write access, the authoring protocol, and protected actions.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/flows.capabilities.get`
- MCP: `jointl_flows_capabilities_get`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

This operation takes an empty object.

### Request example

```json
{
  "input": {}
}
```

### Success example

```json
{
  "data": {
    "authoringProtocol": [
      "example"
    ],
    "decisionSupport": {},
    "draftWriteSupport": {},
    "flowTypes": [
      {}
    ],
    "liveAccess": {},
    "protectedActions": [
      "example"
    ],
    "sections": [
      {}
    ],
    "structuredReferenceQuestionTypes": [
      {}
    ],
    "supportedAuthoredQuestionTypes": {}
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/flows.capabilities.get.json).

## flows.templates.list

List visible Private and Public Jointl Library templates in one category, including their questions, so an assistant can reuse workspace content and valid IDs.

Use when: Use to browse one exact template category or inspect all questions in matching templates; use flows.questions.search for cross-category relevance search.

Returns: template IDs and titles with complete question blocks for the returned templates, plus indicators telling the assistant to increase the limit or narrow the query when results were truncated.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/flows.templates.list`
- MCP: `jointl_flows_templates_list`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `kind` | `preScreening` | `assessmentQuestions` | `assessmentTests` | `references` | `exitIntelligence` | `teamPulse` | Yes | One exact template category to browse. |
| `limit` | integer | No | See the JSON Schema definition. |
| `query` | string | No | See the JSON Schema definition. |

### Request example

```json
{
  "input": {
    "kind": "preScreening"
  }
}
```

### Success example

```json
{
  "data": {
    "catalogScanTruncated": false,
    "hasMore": false,
    "items": [
      {}
    ],
    "kind": "private",
    "totalMatchedInScan": 1
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/flows.templates.list.json).

## flows.questions.search

Search relevant questions across visible pre-screening, assessment, test, reference, exit, and Team Pulse templates without loading entire catalogs into the assistant context.

Use when: Use first when finding reusable questions for a use case across one or more categories; do not load entire template catalogs just to search.

Returns: relevance-ranked question and template IDs, prompts, types, options, matched terms, and search coverage details.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/flows.questions.search`
- MCP: `jointl_flows_questions_search`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `kinds` | array | No | Categories to search. Restrict this list when the requested Flow uses only specific sections. |
| `limit` | integer | No | See the JSON Schema definition. |
| `query` | string | Yes | The job-related capability or use case to find in question prompts, attributes, template titles, types, and options. |

### Request example

```json
{
  "input": {
    "query": "Ada Example"
  }
}
```

### Success example

```json
{
  "data": {
    "catalogScanTruncated": false,
    "hasMore": false,
    "items": [
      {}
    ],
    "searchedQuestionCount": 1,
    "searchedTemplateCount": 1,
    "totalMatchedInScan": 1,
    "truncatedKinds": [
      "example"
    ]
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/flows.questions.search.json).

## flows.referenceTemplates.list

List the exact reference forms configured for manual collection on one visible Flow.

Use when: Use before requesting a reference so the action receives a valid template ID configured on the selected Check’s Flow.

Returns: ordered reference template IDs, titles, icons, and types configured on the Flow.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/flows.referenceTemplates.list`
- MCP: `jointl_flows_reference_templates_list`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `flowId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "input": {
    "flowId": "flowid_example_01"
  }
}
```

### Success example

```json
{
  "data": {
    "items": [
      {}
    ]
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/flows.referenceTemplates.list.json).

## flows.blueprint.get

Read one visible Flow’s latest editable configuration and expanded question/template design. Sensitive automation tokens and protected automation settings are excluded.

Use when: Use only before flows.draft.revise so the latest revision token and complete supported design can be preserved.

Returns: the editable Flow metadata, expanded design, revision token, and indicators for settings that must be managed separately.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/flows.blueprint.get`
- MCP: `jointl_flows_blueprint_get`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `flowId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "input": {
    "flowId": "flowid_example_01"
  }
}
```

### Success example

```json
{
  "data": {
    "design": {},
    "editableDesign": {},
    "flow": {},
    "revision": "2026-01-15T10:30:00.000Z",
    "safety": {}
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/flows.blueprint.get.json).

## performance.operations.get

Read one visible Performance Flow’s participants, cadence, recent Glow Moments and Team Pulse cycles, and completion state. Shareable participant and scoreboard links are returned only when explicitly requested.

Use when: Use after flows.get for a Performance Flow when the user needs cycle progress, a cycle ID, or an explicitly requested participant/scoreboard link.

Returns: the Performance configuration and recent cycles visible to the member; optional participant and scoreboard links include an explicit sharing warning.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/performance.operations.get`
- MCP: `jointl_performance_operations_get`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `cycleLimit` | integer | No | Number of recent Glow Moments and Team Pulse cycles to return per feature. |
| `flowId` | string | Yes | See the JSON Schema definition. |
| `includeLinks` | boolean | No | Include participant access links and the Glow scoreboard link only when the user explicitly needs them. |

### Request example

```json
{
  "input": {
    "flowId": "flowid_example_01"
  }
}
```

### Success example

```json
{
  "data": {
    "capabilityWarning": "Treat returned URLs as private bearer capabilities and share them only with the intended recipient.",
    "flow": {},
    "glowMoments": {},
    "teamPulse": {}
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/performance.operations.get.json).

## glowMoments.send

Prepare a manual Glow Moments cycle for every configured participant in one active Performance Flow. This queues private requests and messages, so explicit confirmation is required.

Use when: Use only when the user explicitly asks to send Glow Moments now; publishing alone follows the configured cadence and is not a manual-send request.

Returns: after confirmation, whether the Glow Moments send was queued and its scheduled time.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_glow_moments_send_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `at-most-once`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `expectedFlowStatus` | constant `"ACTIVE"` | No | The Flow must still be ACTIVE when the confirmed send executes. |
| `flowId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "flowId": "flowid_example_01"
    },
    "operationId": "glowMoments.send"
  }
}
```

### Success example

```json
{
  "data": {
    "flowId": "flowid_example_01",
    "queued": true,
    "scheduledFor": "2026-01-15T10:30:00.000Z"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `outcomeUnknown`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/glowMoments.send.json).

## glowMoments.cycle.status.set

Prepare cancellation or restoration of one exact Glow Moments cycle using its current status for concurrency safety. Explicit confirmation is required.

Use when: Use only after performance.operations.get when the user explicitly asks to cancel or restore that exact Glow Moments cycle.

Returns: after confirmation, the cycle ID, Flow ID, previous status, resulting status, enabled state, and change flag.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_glow_moments_cycle_status_set_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `cycleId` | string | Yes | See the JSON Schema definition. |
| `enabled` | boolean | Yes | False cancels pending delivery and incomplete requests; true restores the cycle where possible. |
| `expectedStatus` | `SCHEDULED` | `SENT` | `CANCELLED` | Yes | Current Glow Moments cycle status read from performance.operations.get. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "cycleId": "cycleid_example_01",
      "enabled": true,
      "expectedStatus": "CANCELLED"
    },
    "operationId": "glowMoments.cycle.status.set"
  }
}
```

### Success example

```json
{
  "data": {
    "changed": true,
    "cycleId": "cycleid_example_01",
    "enabled": true,
    "flowId": "flowid_example_01",
    "previousStatus": "active",
    "status": "active"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/glowMoments.cycle.status.set.json).

## teamPulse.send

Prepare a manual Team Pulse cycle using the configured form for every participant in one active Performance Flow. This queues private requests and messages, so explicit confirmation is required.

Use when: Use only when the user explicitly asks to send Team Pulse now; publishing alone follows the configured cadence and is not a manual-send request.

Returns: after confirmation, whether the Team Pulse send was queued and its scheduled time.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_team_pulse_send_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `at-most-once`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `expectedFlowStatus` | constant `"ACTIVE"` | No | The Flow must still be ACTIVE when the confirmed send executes. |
| `flowId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "flowId": "flowid_example_01"
    },
    "operationId": "teamPulse.send"
  }
}
```

### Success example

```json
{
  "data": {
    "flowId": "flowid_example_01",
    "queued": true,
    "scheduledFor": "2026-01-15T10:30:00.000Z"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `outcomeUnknown`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/teamPulse.send.json).

## teamPulse.cycle.status.set

Prepare cancellation or restoration of one exact Team Pulse cycle using its current status for concurrency safety. Explicit confirmation is required.

Use when: Use only after performance.operations.get when the user explicitly asks to cancel or restore that exact Team Pulse cycle.

Returns: after confirmation, the cycle ID, Flow ID, previous status, resulting status, enabled state, and change flag.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_team_pulse_cycle_status_set_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `cycleId` | string | Yes | See the JSON Schema definition. |
| `enabled` | boolean | Yes | False cancels pending delivery and incomplete requests; true restores the cycle where possible. |
| `expectedStatus` | `SCHEDULED` | `PROCESSING` | `SENT` | `CANCELLED` | `FAILED` | Yes | Current Team Pulse cycle status read from performance.operations.get. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "cycleId": "cycleid_example_01",
      "enabled": true,
      "expectedStatus": "CANCELLED"
    },
    "operationId": "teamPulse.cycle.status.set"
  }
}
```

### Success example

```json
{
  "data": {
    "changed": true,
    "cycleId": "cycleid_example_01",
    "enabled": true,
    "flowId": "flowid_example_01",
    "previousStatus": "active",
    "status": "active"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/teamPulse.cycle.status.set.json).

## checks.list

List Checks visible through the member’s role, sharing, creator, manager, and company permissions.

Use when: Use to browse or filter Checks and obtain applicant IDs; use checks.analytics for comparisons and checks.get for one person.

Returns: a cursor-paginated list of authorized Check summaries, Flow context, statuses, progress, and IDs.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/checks.list`
- MCP: `jointl_checks_list`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `cursor` | object | No | See the JSON Schema definition. |
| `limit` | integer | No | See the JSON Schema definition. |
| `selectedApplicantStatus` | array | No | Defaults to current Checks. Pass an empty array to include every authorized Check status. |
| `selectedFlows` | array | No | Exact Flow IDs. A non-empty list automatically enables the Flow filter. |

### Request example

```json
{
  "input": {}
}
```

### Success example

```json
{
  "data": {
    "hasMore": false,
    "items": [
      {
        "_id": "_id_example_01",
        "firstName": "Ada",
        "flowId": "flowid_example_01",
        "lastName": "Example",
        "status": "active"
      }
    ],
    "nextCursor": null
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/checks.list.json).

## checks.analytics

Return a paginated, evidence-based ranking within each visible Flow, including matching scores, measured high and low evidence, evidence coverage, and verification state. It never recommends an employment decision.

Use when: Use first for top-candidate, ranking, strengths, weaknesses, or cohort-comparison requests; follow nextOffset until null when the complete filtered cohort is required.

Returns: per-Flow factual ranks, scores, evidence summaries, coverage and verification signals, cohort counts, pagination, and guidance for human review.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/checks.analytics`
- MCP: `jointl_checks_analytics`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `limit` | integer | No | See the JSON Schema definition. |
| `offset` | integer | No | See the JSON Schema definition. |
| `selectedApplicantStatus` | array | No | Defaults to current Checks. Pass an empty array to include every authorized Check status. |
| `selectedFlows` | array | No | Exact Flow IDs. Empty means every otherwise-authorized Flow, subject to the cohort bound. |

### Request example

```json
{
  "input": {}
}
```

### Success example

```json
{
  "data": {
    "evaluatedCandidateCount": 1,
    "exactCohort": false,
    "flowCohorts": [
      {}
    ],
    "hasMore": false,
    "items": [
      {
        "applicantId": "applicantid_example_01",
        "detailOperation": "checks.get",
        "evidenceSummary": "evidencesummary_example_01",
        "matchingScore": 75,
        "matchingScorePercent": 75,
        "name": "Ada Example",
        "rankWithinFlow": 1,
        "scoredCandidateCount": 75
      }
    ],
    "nextOffset": 1,
    "offset": 1,
    "returnedCandidateCount": 1,
    "safety": {}
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/checks.analytics.json).

## checks.get

Return the profile, Flow context, recent visible activity, and optional condensed evidence for one authorized Check. Sensitive access tokens are never returned.

Use when: Use after search, list, or analytics when one Check needs contextual detail; use checks.report only for the full itemized assessment and reference report.

Returns: profile metadata and recent activity, evidenceIncluded, and either condensed pre-screening, matching, work and reference evidence or null.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/checks.get`
- MCP: `jointl_checks_get`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `applicantId` | string | Yes | See the JSON Schema definition. |
| `includeEvidence` | boolean | No | Include the authorized evidence view. Set false only when profile metadata is sufficient. |

### Request example

```json
{
  "input": {
    "applicantId": "applicantid_example_01"
  }
}
```

### Success example

```json
{
  "data": {
    "evidence": {},
    "evidenceIncluded": false,
    "profile": {}
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/checks.get.json).

## checks.report

Return the authorized full factual Check report, including open-text answers, answered AI follow-ups, Tests, reference narratives and integrity context, employment confirmations, attributes, and scores—but no hiring recommendation.

Use when: Use after checks.analytics for every candidate relevant to a comparative conclusion, or after checks.get when complete itemized evidence is needed; do not rely on rating and score summaries alone.

Returns: the itemized authorized Check report with factual narrative and measured evidence; it never returns a recommendation or reference responses the member cannot access.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/checks.report`
- MCP: `jointl_checks_report`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `applicantId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "input": {
    "applicantId": "applicantid_example_01"
  }
}
```

### Success example

```json
{
  "data": {
    "assessment": {},
    "company": {},
    "crossVerifiedAttributeScores": [
      {}
    ],
    "flow": {},
    "flowRequest": {},
    "keyAchievements": [
      {}
    ],
    "matchingScore": 75,
    "preScreening": {},
    "references": [
      {}
    ],
    "referencesAvgMetrics": [
      {}
    ]
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/checks.report.json).

## checks.verifications.get

Return the verification types available to the member and their latest results for one authorized Check. Image content is not returned.

Use when: Use after a verification.completed or verification.failed Zapier event, or to inspect which verification types are available, active, complete, locked, or missing required details.

Returns: verification types available through the member’s permissions and workspace plan, the latest run status and findings for each type, and Check eligibility state.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/checks.verifications.get`
- MCP: not available
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `applicantId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "input": {
    "applicantId": "applicantid_example_01"
  }
}
```

### Success example

```json
{
  "data": {
    "applicantId": "applicantid_example_01",
    "canRunAny": false,
    "serviceUnavailable": false,
    "verificationEligibility": {},
    "verifications": [
      {}
    ]
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/checks.verifications.get.json).

## checks.verifications.runAll

Prepare every verification available and eligible for one authorized Check. Active runs and completed results that cannot be repeated are reused.

Use when: Use when an external event should start the Run All Checks workflow; verification types that require unavailable applicant details are skipped.

Returns: one run group ID and the queued, reused, locked, or immediately completed result for each available verification type.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: not available
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: supported

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `applicantId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "applicantId": "applicantid_example_01"
    },
    "operationId": "checks.verifications.runAll"
  }
}
```

### Success example

```json
{
  "data": {
    "applicantId": "applicantid_example_01",
    "runGroupId": "rungroupid_example_01",
    "runs": [
      {}
    ]
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `idempotencyConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/checks.verifications.runAll.json).

## checks.publicProfiles.get

Return the latest public-profile discovery results visible for one authorized Check. Image content is not returned.

Use when: Use after a public_profiles.completed or public_profiles.failed Zapier event, or to inspect a previously completed public-profile discovery run.

Returns: the latest and previous completed discovery states, public profile matches available to the member, graph summary, and availability state.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/checks.publicProfiles.get`
- MCP: not available
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `applicantId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "input": {
    "applicantId": "applicantid_example_01"
  }
}
```

### Success example

```json
{
  "data": {
    "entitled": false,
    "latestRun": {},
    "previousCompletedRun": {},
    "serviceUnavailable": false,
    "subjectRef": {}
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/checks.publicProfiles.get.json).

## checks.publicProfiles.find

Prepare public-profile discovery for one authorized Check using existing Check identity data and optional corroborating hints.

Use when: Use when an external event should start the Find Profiles workflow; provide only known identity, location, or profile-URL hints and never speculative personal data.

Returns: the queued or reused run ID and status, or a rescore of an existing completed result with its match count.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: not available
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: supported

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `applicantId` | string | Yes | See the JSON Schema definition. |
| `profileMatchingDetails` | object | No | Optional corroborating identity and location hints. Jointl also reuses the Check name, email, stored verification location, and confirmed profile links. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "applicantId": "applicantid_example_01"
    },
    "operationId": "checks.publicProfiles.find"
  }
}
```

### Success example

```json
{
  "data": {
    "alreadyRunning": false,
    "applicantId": "applicantid_example_01",
    "matchCount": 1,
    "rescored": false,
    "runId": "runid_example_01",
    "status": "active"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `idempotencyConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/checks.publicProfiles.find.json).

## references.list

List authorized reference request and completion summaries for one visible Check with stable cursor pagination.

Use when: Use to retrieve every reference for a Check or find a reference ID before retrieving one complete response.

Returns: a cursor-paginated list of reference IDs, referee identity, type, status, and lifecycle times.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/references.list`
- MCP: `jointl_references_list`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `applicantId` | string | Yes | See the JSON Schema definition. |
| `cursor` | object | No | See the JSON Schema definition. |
| `limit` | integer | No | See the JSON Schema definition. |

### Request example

```json
{
  "input": {
    "applicantId": "applicantid_example_01"
  }
}
```

### Success example

```json
{
  "data": {
    "hasMore": false,
    "items": [
      {
        "applicantId": "applicantid_example_01",
        "createdAt": "2026-01-15",
        "id": "id_example_01",
        "status": "active"
      }
    ],
    "nextCursor": null
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/references.list.json).

## references.get

Return one authorized, normalized reference response and its Check-level average metrics.

Use when: Use after references.list or a reference.completed event when the complete submitted response is needed.

Returns: the complete reference response available to the member and average reference metrics.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/references.get`
- MCP: `jointl_references_get`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `referenceId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "input": {
    "referenceId": "referenceid_example_01"
  }
}
```

### Success example

```json
{
  "data": {},
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/references.get.json).

## employees.list

List Employees visible through the member’s role, sharing, manager, creator, and company permissions.

Use when: Use to browse or filter Employees and obtain Employee IDs; use employees.analytics for performance comparisons and employees.get for one person.

Returns: a cursor-paginated list of authorized Employee summaries with company, position, manager, tags, status, and IDs.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/employees.list`
- MCP: `jointl_employees_list`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `cursor` | object | No | See the JSON Schema definition. |
| `limit` | integer | No | See the JSON Schema definition. |
| `selectedCompanies` | array | No | Exact Jointl company IDs; empty means every authorized company. |
| `selectedEmployeeStatus` | array | No | Defaults to active Employees. Pass an empty array to include every authorized Employee status. |
| `selectedTags` | array | No | Exact Jointl tag IDs; empty means every tag. |

### Request example

```json
{
  "input": {}
}
```

### Success example

```json
{
  "data": {
    "hasMore": false,
    "items": [
      {
        "_id": "_id_example_01",
        "companyId": "companyid_example_01",
        "fullName": "Ada Example",
        "positionTitle": "Example title",
        "status": "active"
      }
    ],
    "nextCursor": null
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/employees.list.json).

## employees.analytics

Return a pageable factual ranking and review signals from Team Pulse and Glow Moments for only the Employees visible to the member. It never recommends an employment decision.

Use when: Use first for best-performer, needs-attention, strengths, weaknesses, or workforce-comparison requests; follow nextOffset until null for the complete filtered cohort.

Returns: factual visible-cohort ranks, performance scores, measured evidence, attention signals, counts, pagination, and guidance for human review.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/employees.analytics`
- MCP: `jointl_employees_analytics`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `endDate` | string | No | Inclusive UTC evidence end date in YYYY-MM-DD. Omit both dates for the trailing six-month default. |
| `limit` | integer | No | See the JSON Schema definition. |
| `offset` | integer | No | See the JSON Schema definition. |
| `selectedCompanies` | array | No | Exact Jointl company IDs; empty means every authorized company, subject to the cohort bound. |
| `selectedEmployeeStatus` | array | No | Defaults to active Employees. Pass an empty array to include every authorized Employee status. |
| `selectedTags` | array | No | Exact Jointl tag IDs; empty means every tag. |
| `startDate` | string | No | Inclusive UTC evidence start date in YYYY-MM-DD. Omit both dates for the trailing six-month default. |

### Request example

```json
{
  "input": {}
}
```

### Success example

```json
{
  "data": {
    "evaluatedEmployeeCount": 1,
    "evidenceWindow": {
      "endDate": "2026-01-15",
      "inclusive": true,
      "startDate": "2026-01-15",
      "timeZone": "UTC"
    },
    "exactCohort": false,
    "hasMore": false,
    "items": [
      {}
    ],
    "nextOffset": 1,
    "offset": 1,
    "returnedEmployeeCount": 1,
    "safety": {},
    "scoredEmployeeCount": 75
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/employees.analytics.json).

## employees.get

Return the profile, current work context, recent visible activity, and optional performance evidence for one authorized Employee.

Use when: Use after search, list, or analytics when one Employee needs contextual or performance detail; set includeEvidence=false only for lightweight profile metadata.

Returns: profile, position, company, manager, tags and compensation-access metadata, plus optional Team Pulse, Glow Moments, exit, and work evidence.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/employees.get`
- MCP: `jointl_employees_get`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `employeeId` | string | Yes | See the JSON Schema definition. |
| `includeEvidence` | boolean | No | Include the authorized evidence view. Set false only when profile metadata is sufficient. |

### Request example

```json
{
  "input": {
    "employeeId": "employeeid_example_01"
  }
}
```

### Success example

```json
{
  "data": {
    "evidence": {},
    "evidenceIncluded": false,
    "profile": {}
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/employees.get.json).

## employees.exitIntelligence.get

Return the latest or one exact authorized Exit Intelligence request for a visible Employee, including completed answers and calculated metrics. Public access tokens are never returned.

Use when: Use after an exit_intelligence.completed Zapier event, passing its request ID when available so a later request cannot replace the intended result.

Returns: the visible Employee summary and zero or one non-cancelled Exit Intelligence request with its Flow, form, metrics, and answered questions.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/employees.exitIntelligence.get`
- MCP: not available
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `employeeId` | string | Yes | See the JSON Schema definition. |
| `requestId` | string | No | Optional exact Exit Intelligence request ID from a trigger; omitted means the latest visible request. |

### Request example

```json
{
  "input": {
    "employeeId": "employeeid_example_01"
  }
}
```

### Success example

```json
{
  "data": {
    "employee": {},
    "requests": [
      {}
    ]
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/employees.exitIntelligence.get.json).

## talents.list

List company-scoped Talent Pool profiles. Profiles without an authorized company match are not returned.

Use when: Use to browse and filter the authorized Talent Pool and obtain profile IDs; use talents.get for one profile.

Returns: a cursor-paginated list of scoped Talent Pool summaries, statuses, experience and evidence metrics allowed by the role.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/talents.list`
- MCP: `jointl_talents_list`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `cursor` | object | No | See the JSON Schema definition. |
| `limit` | integer | No | See the JSON Schema definition. |
| `selectedAttributes` | array | No | Exact extracted attribute values. |
| `selectedCompanies` | array | No | Exact extracted company-name values; these are labels, not Jointl company IDs. |
| `selectedExperience` | array | No | Experience-range IDs: 0-2, 3-5, 6-9, or 10-plus. |
| `selectedIndustries` | array | No | Exact extracted industry values. |
| `selectedRoles` | array | No | Exact extracted current or prior job-title values. |
| `selectedTalentStatus` | array | No | See the JSON Schema definition. |

### Request example

```json
{
  "input": {}
}
```

### Success example

```json
{
  "data": {
    "hasMore": false,
    "items": [
      {
        "_id": "_id_example_01",
        "firstName": "Ada",
        "lastName": "Example",
        "status": "active"
      }
    ],
    "nextCursor": null
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/talents.list.json).

## talents.get

Return the profile and optional evidence overview for one company-scoped Talent Pool person.

Use when: Use after search or talents.list for one profile; use talents.references.list only when itemized reference responses are specifically needed and permitted.

Returns: profile, contact and extracted experience data, plus optional achievements, work, notes, answer signals and cross-verified attributes.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/talents.get`
- MCP: `jointl_talents_get`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `includeEvidence` | boolean | No | Include the authorized evidence view. Set false only when profile metadata is sufficient. |
| `talentId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "input": {
    "talentId": "talentid_example_01"
  }
}
```

### Success example

```json
{
  "data": {
    "evidence": {},
    "evidenceIncluded": false,
    "profile": {}
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/talents.get.json).

## talents.references.list

Return reference responses only when both Talent Pool and response permissions allow it.

Use when: Use only for itemized authorized reference responses on one Talent Pool profile; talents.get is the normal profile and evidence path.

Returns: normalized reference responses and average reference metrics, with third-party identities masked when required.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/talents.references.list`
- MCP: `jointl_talents_references_list`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `talentId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "input": {
    "talentId": "talentid_example_01"
  }
}
```

### Success example

```json
{
  "data": {
    "avgMetrics": [
      {}
    ],
    "references": [
      {}
    ]
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/talents.references.list.json).

## autopilots.list

List Autopilot groups available through the member’s current permissions and Flow or company access. Shareable access links are omitted from list results.

Use when: Use to find an Autopilot group, inspect status and Check counts, or obtain a group ID; use autopilots.get only when its public links are needed.

Returns: a cursor-paginated list of visible Autopilot summaries without shareable access links.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/autopilots.list`
- MCP: `jointl_autopilots_list`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `cursor` | object | No | See the JSON Schema definition. |
| `includeArchived` | boolean | No | Include archived Autopilots as well as active Autopilots. |
| `limit` | integer | No | See the JSON Schema definition. |

### Request example

```json
{
  "input": {}
}
```

### Success example

```json
{
  "data": {
    "hasMore": false,
    "items": [
      {
        "_id": "_id_example_01",
        "checksTotal": 1,
        "flowId": "flowid_example_01",
        "status": "active",
        "title": "Example title"
      }
    ],
    "nextCursor": null
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/autopilots.list.json).

## autopilots.get

Return one visible Autopilot and its reusable public access links. Anyone holding an active link can start the attached Flow.

Use when: Use only when the user needs to inspect one known Autopilot or retrieve its links for an intended audience; do not expose links from a broad list.

Returns: Autopilot status, Flow context, Check count, enabled sections, public links, and a sharing warning.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/autopilots.get`
- MCP: `jointl_autopilots_get`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `autopilotGroupId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "input": {
    "autopilotGroupId": "autopilotgroupid_example_01"
  }
}
```

### Success example

```json
{
  "data": {
    "autopilotGroupId": "autopilotgroupid_example_01",
    "capabilityWarning": "Treat returned URLs as private bearer capabilities and share them only with the intended recipient.",
    "checksTotal": 1,
    "createdAt": "2026-01-15",
    "flowId": "flowid_example_01",
    "publicLinks": [
      "example"
    ],
    "status": "active",
    "title": "Example title"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/autopilots.get.json).

## insights.get

Return the General, Performance, or Exit Intelligence view available to the member for an inclusive UTC date range, using the same calculations shown in Jointl.

Use when: Use for workspace activity and completion metrics, team performance evidence, or Exit Intelligence themes; select one view and supply both dates when the user specifies a period.

Returns: the selected Insights dataset plus the applied view, inclusive UTC dates, and company, Flow, and role filters.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/insights.get`
- MCP: `jointl_insights_get`
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `endDate` | string | No | Inclusive UTC end date in YYYY-MM-DD. Omit both dates for the trailing six-month default. |
| `selectedCompanies` | array | No | Exact authorized Jointl company IDs; empty means every authorized company. |
| `selectedFlows` | array | No | Exact authorized Flow IDs; empty means every authorized Flow for this view. |
| `selectedRoles` | array | No | Exact Employee role-title labels; empty means every authorized role. |
| `startDate` | string | No | Inclusive UTC start date in YYYY-MM-DD. Omit both dates for the trailing six-month default. |
| `view` | `general` | `performance` | `exitIntelligence` | No | general maps to /insights, performance to /insights?view=performance, and exitIntelligence to /insights?view=exit-intelligence. |

### Request example

```json
{
  "input": {}
}
```

### Success example

```json
{
  "data": {
    "data": {
      "summary": {
        "activeChecks": 12,
        "activeEmployees": 34
      }
    },
    "dateRange": {
      "endDate": "2026-01-15",
      "inclusive": true,
      "startDate": "2025-07-15",
      "timeZone": "UTC"
    },
    "filters": {
      "companyIds": [],
      "flowIds": [],
      "roleTitles": []
    },
    "view": "general"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/insights.get.json).

## events.list

Return up to three recent events that the connected member can access, matching one Zapier trigger and its filters.

Use when: Use when Zapier tests or configures a trigger before new events are available.

Returns: newest-first trigger payloads with the same shape returned after a Zapier webhook notification.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/events.list`
- MCP: not available
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `eventType` | `check.created` | `check.status_changed` | `check.completed` | `verification.completed` | `verification.failed` | `public_profiles.completed` | `public_profiles.failed` | `reference.completed` | `employee.created` | `employee.updated` | `employee.status_changed` | `exit_intelligence.requested` | `exit_intelligence.completed` | `talent.created` | `talent.updated` | `talent.status_changed` | Yes | See the JSON Schema definition. |
| `filters` | object | No | See the JSON Schema definition. |
| `limit` | integer | No | See the JSON Schema definition. |

### Request example

```json
{
  "input": {
    "eventType": "check.created"
  }
}
```

### Success example

```json
{
  "data": {
    "items": [
      {
        "check_id": "check_example_01",
        "company_ids": [
          "company_example_01"
        ],
        "data": {
          "id": "check_example_01",
          "status": "new"
        },
        "entity_id": "check_example_01",
        "entity_type": "check",
        "event_type": "check.created",
        "id": "event_example_01",
        "jointl_url": "https://join.tl/checks/check_example_01",
        "occurred_at": "2026-01-15T10:30:00.000Z",
        "record_name": "Ada Example"
      }
    ]
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/events.list.json).

## events.get

Retrieve the full payload for one opaque event notification through the member’s current Jointl permissions.

Use when: Use only after an instant Zapier hook receives an event ID.

Returns: one authorized trigger payload; revoked or inaccessible records are not returned.

- Scope: `workspace.read`
- REST: `POST /api/v1/operations/events.get`
- MCP: not available
- Confirmation: not required
- Destructive: no
- Retry safety: `safe-read`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `eventId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "input": {
    "eventId": "eventid_example_01"
  }
}
```

### Success example

```json
{
  "data": {
    "check_id": "check_example_01",
    "company_ids": [
      "company_example_01"
    ],
    "data": {
      "id": "check_example_01",
      "status": "new"
    },
    "entity_id": "check_example_01",
    "entity_type": "check",
    "event_type": "check.created",
    "id": "event_example_01",
    "jointl_url": "https://join.tl/checks/check_example_01",
    "occurred_at": "2026-01-15T10:30:00.000Z",
    "record_name": "Ada Example"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/events.get.json).

## flows.draft.create

Prepare a complete, unpublished Flow draft using visible library templates and optional original question blocks. Hiring drafts enable Public Profiles and, when available for the workspace, Talent Pool by default. No invitations, publishing, team sharing, third-party automation, or automatic candidate decisions occur. Explicit confirmation is required.

Use when: Use after capabilities, companies, and relevant question/template discovery have produced a complete supported design and the user wants it saved as a new draft.

Returns: after confirmation, the created draft Flow ID, revision, and saved design summary.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_flows_draft_create_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `design` | object | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "design": {
        "companyId": "company_example_01",
        "jobTitle": "Software Engineer",
        "title": "Example Hiring Flow",
        "type": "HIRING_REVIEW"
      }
    },
    "operationId": "flows.draft.create"
  }
}
```

### Success example

```json
{
  "data": {
    "configuration": {},
    "createdTemplateIds": {},
    "flowId": "flow_example_01",
    "publicProfilesEnabled": true,
    "revision": "2026-01-15T10:30:00.000Z",
    "status": "DRAFT",
    "talentPoolEnabled": true,
    "title": "Example Hiring Flow",
    "type": "HIRING_REVIEW"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/flows.draft.create.json).

## flows.draft.revise

Prepare a replacement of supported sections in one unpublished Flow. The latest blueprint revision is required so concurrent edits are not overwritten. Publishing, team sharing, Public Profiles, Talent Pool, third-party automation, automatic candidate decisions, and messaging remain unchanged. Explicit confirmation is required.

Use when: Use only after flows.blueprint.get when the user wants to replace supported sections of that still-unpublished draft.

Returns: after confirmation, the revised draft Flow ID, new revision, and saved design summary.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_flows_draft_revise_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `design` | object | Yes | See the JSON Schema definition. |
| `expectedRevision` | union | Yes | See the JSON Schema definition. |
| `flowId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "design": {
        "companyId": "company_example_01",
        "jobTitle": "Software Engineer",
        "title": "Example Hiring Flow",
        "type": "HIRING_REVIEW"
      },
      "expectedRevision": "2026-01-15T10:30:00.000Z",
      "flowId": "flow_example_01"
    },
    "operationId": "flows.draft.revise"
  }
}
```

### Success example

```json
{
  "data": {
    "configuration": {},
    "createdTemplateIds": {},
    "flowId": "flow_example_01",
    "publicProfilesEnabled": true,
    "revision": "2026-01-15T10:30:00.000Z",
    "status": "DRAFT",
    "talentPoolEnabled": true,
    "title": "Example Hiring Flow",
    "type": "HIRING_REVIEW"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/flows.draft.revise.json).

## flows.status.set

Prepare a Flow publish, archive, or restore action using the current Flow status to prevent conflicting changes. Publishing validates that the Flow is ready; archiving cancels pending requests and scheduled activity for the Flow. Explicit confirmation is required.

Use when: Use only when the user explicitly asks to publish, activate, archive, or restore one known Flow; never infer a status change from scores or recommendations.

Returns: after confirmation, the Flow ID, previous status, resulting status, and whether the status change was applied.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_flows_status_set_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `expectedStatus` | `ACTIVE` | `DRAFT` | `ARCHIVED` | Yes | Current status read from flows.get or flows.blueprint.get; used for concurrency safety. |
| `flowId` | string | Yes | See the JSON Schema definition. |
| `status` | `ACTIVE` | `ARCHIVED` | Yes | Publish/restore as ACTIVE or archive as ARCHIVED. Returning a Flow to DRAFT is unsupported. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "expectedStatus": "ACTIVE",
      "flowId": "flowid_example_01",
      "status": "ARCHIVED"
    },
    "operationId": "flows.status.set"
  }
}
```

### Success example

```json
{
  "data": {
    "changed": true,
    "previousStatus": "active",
    "recordId": "recordid_example_01",
    "status": "active"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/flows.status.set.json).

## flows.delete

Prepare irreversible deletion of one visible Flow and its related Checks, Autopilots, pending activity, and Performance cycle data. Explicit confirmation is required.

Use when: Use only when the user explicitly asks to permanently delete one known Flow; offer flows.status.set with ARCHIVED when preserving history is acceptable.

Returns: after confirmation, the deleted Flow ID, prior status, and deletion outcome.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_flows_delete_prepare`
- Confirmation: required
- Destructive: yes
- Retry safety: `at-most-once`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `expectedStatus` | `ACTIVE` | `DRAFT` | `ARCHIVED` | Yes | Current status read from flows.get or flows.blueprint.get; used to prevent a stale destructive action. |
| `flowId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "expectedStatus": "ACTIVE",
      "flowId": "flowid_example_01"
    },
    "operationId": "flows.delete"
  }
}
```

### Success example

```json
{
  "data": {
    "deleted": true,
    "previousStatus": "active",
    "recordId": "recordid_example_01"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `outcomeUnknown`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/flows.delete.json).

## checks.status.set

Prepare a status change for one authorized Check using its current status to prevent conflicting changes. The `selected` status is not available because candidate selection uses the separate Employee conversion workflow. Explicit confirmation is required.

Use when: Use only when the user explicitly asks to change one Check status; never shortlist or reject someone solely because an analysis, score, or ranking suggests it.

Returns: after confirmation, the Check ID, previous status, resulting status, and whether the change was applied.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_checks_status_set_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: supported

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `applicantId` | string | Yes | See the JSON Schema definition. |
| `expectedStatus` | `new` | `archived` | `inProgress` | `shortlisted` | `rejected` | `selected` | Yes | Current status read from checks.get or checks.list; used for concurrency safety. |
| `status` | `new` | `archived` | `inProgress` | `shortlisted` | `rejected` | Yes | New Check status. selected is intentionally excluded because selection creates an Employee. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "applicantId": "applicantid_example_01",
      "expectedStatus": "new",
      "status": "archived"
    },
    "operationId": "checks.status.set"
  }
}
```

### Success example

```json
{
  "data": {
    "changed": true,
    "previousStatus": "active",
    "recordId": "recordid_example_01",
    "status": "active"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `idempotencyConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/checks.status.set.json).

## checks.delete

Prepare irreversible deletion of one visible Check and its pre-screening, assessment, reference, feedback, verification, and pending lifecycle data. Explicit confirmation is required.

Use when: Use only when the user explicitly asks to permanently delete one known Check; do not derive deletion from a score, rank, recommendation, or status.

Returns: after confirmation, the deleted Check ID, prior status, and deletion outcome.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_checks_delete_prepare`
- Confirmation: required
- Destructive: yes
- Retry safety: `at-most-once`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `applicantId` | string | Yes | See the JSON Schema definition. |
| `expectedStatus` | `new` | `archived` | `inProgress` | `shortlisted` | `rejected` | `selected` | Yes | Current status read from checks.get or checks.list; used to prevent a stale destructive action. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "applicantId": "applicantid_example_01",
      "expectedStatus": "new"
    },
    "operationId": "checks.delete"
  }
}
```

### Success example

```json
{
  "data": {
    "deleted": true,
    "previousStatus": "active",
    "recordId": "recordid_example_01"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `outcomeUnknown`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/checks.delete.json).

## employees.status.set

Prepare an active or left status change for one authorized Employee using the current status to prevent conflicting changes. Marking left requires an end date for every active position and can optionally launch an Exit Intelligence Flow; an Employee already marked left may use the same operation solely to send Exit Intelligence. Explicit confirmation is required.

Use when: Use only when the user explicitly asks to mark a known Employee active or left and has supplied any required position end dates, or explicitly asks to send Exit Intelligence to an Employee already marked left; never infer this action from performance analytics.

Returns: after confirmation, the Employee ID, previous status, resulting status, and whether the change was applied.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_employees_status_set_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: supported

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `employeeId` | string | Yes | See the JSON Schema definition. |
| `exitIntelligenceFlowId` | string | No | Optional active Exit Intelligence Flow to launch after marking the Employee left. |
| `expectedStatus` | `active` | `left` | Yes | Current status read from employees.get or employees.list; used for concurrency safety. |
| `positionEndAt` | string | No | One leaving date to apply to every active position. Do not combine with positionEndDates. |
| `positionEndDates` | array | No | When marking left, provide an end date for every active position returned by employees.get. |
| `status` | `active` | `left` | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "employeeId": "employeeid_example_01",
      "expectedStatus": "left",
      "status": "active"
    },
    "operationId": "employees.status.set"
  }
}
```

### Success example

```json
{
  "data": {
    "changed": true,
    "previousStatus": "active",
    "recordId": "recordid_example_01",
    "status": "active"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `idempotencyConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/employees.status.set.json).

## employees.delete

Prepare irreversible deletion of one visible Employee, removal from manager and Glow Moment assignments, and cancellation of incomplete requests and scheduled activity for the Employee. Explicit confirmation is required.

Use when: Use only when the user explicitly asks to permanently delete one known Employee; do not derive deletion from performance evidence, rankings, or attention signals.

Returns: after confirmation, the deleted Employee ID, prior status, and deletion outcome.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_employees_delete_prepare`
- Confirmation: required
- Destructive: yes
- Retry safety: `at-most-once`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `employeeId` | string | Yes | See the JSON Schema definition. |
| `expectedStatus` | `active` | `left` | Yes | Current status read from employees.get or employees.list; used to prevent a stale destructive action. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "employeeId": "employeeid_example_01",
      "expectedStatus": "active"
    },
    "operationId": "employees.delete"
  }
}
```

### Success example

```json
{
  "data": {
    "deleted": true,
    "previousStatus": "active",
    "recordId": "recordid_example_01"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `outcomeUnknown`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/employees.delete.json).

## talents.status.set

Prepare a new, shortlisted, or archived status change for one company-scoped Talent Pool profile using its current status to prevent conflicting changes. Explicit confirmation is required.

Use when: Use only when the user explicitly asks to change one Talent Pool status; never infer shortlisting from an analysis or ranking.

Returns: after confirmation, the Talent Pool profile ID, previous status, resulting status, and whether the change was applied.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_talents_status_set_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: supported

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `expectedStatus` | `new` | `archived` | `shortlisted` | Yes | Current status read from talents.get or talents.list; used for concurrency safety. |
| `status` | `new` | `archived` | `shortlisted` | Yes | See the JSON Schema definition. |
| `talentId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "expectedStatus": "new",
      "status": "archived",
      "talentId": "talentid_example_01"
    },
    "operationId": "talents.status.set"
  }
}
```

### Success example

```json
{
  "data": {
    "changed": true,
    "previousStatus": "active",
    "recordId": "recordid_example_01",
    "status": "active"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `idempotencyConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/talents.status.set.json).

## autopilots.create

Prepare a new Autopilot for one active visible Hiring Review Flow and generate reusable public access links. Anyone with a link can start the Flow. Explicit confirmation is required.

Use when: Use when the user explicitly asks to run a new Autopilot or generate a new Autopilot link group for one exact active Flow.

Returns: after confirmation, the Autopilot group ID, Flow context, newly generated public links, and a sharing warning.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_autopilots_create_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `flowId` | string | Yes | Exact active Hiring Review Flow ID. |
| `linkCount` | integer | No | Number of independent reusable public access links to generate. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "flowId": "flowid_example_01"
    },
    "operationId": "autopilots.create"
  }
}
```

### Success example

```json
{
  "data": {
    "autopilotGroupId": "autopilotgroupid_example_01",
    "capabilityWarning": "Treat returned URLs as private bearer capabilities and share them only with the intended recipient.",
    "flowId": "flowid_example_01",
    "flowTitle": "Example title",
    "publicLinks": [
      "example"
    ]
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/autopilots.create.json).

## autopilots.links.generate

Prepare additional reusable public access links for one active Autopilot. Explicit confirmation is required.

Use when: Use when the user explicitly asks for more links on an existing known Autopilot; do not create a second Autopilot group for the same intent.

Returns: after confirmation, the existing group ID and only the newly generated public links with a sharing warning.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_autopilots_links_generate_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `autopilotGroupId` | string | Yes | See the JSON Schema definition. |
| `expectedStatus` | constant `"ACTIVE"` | No | Links can be added only while the Autopilot is ACTIVE. |
| `linkCount` | integer | No | Number of independent reusable public access links to generate. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "autopilotGroupId": "autopilotgroupid_example_01"
    },
    "operationId": "autopilots.links.generate"
  }
}
```

### Success example

```json
{
  "data": {
    "autopilotGroupId": "autopilotgroupid_example_01",
    "capabilityWarning": "Treat returned URLs as private bearer capabilities and share them only with the intended recipient.",
    "flowId": "flowid_example_01",
    "flowTitle": "Example title",
    "publicLinks": [
      "example"
    ]
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/autopilots.links.generate.json).

## autopilots.status.set

Prepare an Autopilot archive or restore action. Archiving disables every public link in the group while preserving its Checks. Explicit confirmation is required.

Use when: Use only when the user explicitly asks to archive, disable, restore, or reactivate one known Autopilot.

Returns: after confirmation, the Autopilot group ID, previous status, resulting status, and whether the action was applied.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_autopilots_status_set_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `autopilotGroupId` | string | Yes | See the JSON Schema definition. |
| `expectedStatus` | `ACTIVE` | `ARCHIVED` | Yes | See the JSON Schema definition. |
| `status` | `ACTIVE` | `ARCHIVED` | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "autopilotGroupId": "autopilotgroupid_example_01",
      "expectedStatus": "ACTIVE",
      "status": "ARCHIVED"
    },
    "operationId": "autopilots.status.set"
  }
}
```

### Success example

```json
{
  "data": {
    "changed": true,
    "previousStatus": "active",
    "recordId": "recordid_example_01",
    "status": "active"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/autopilots.status.set.json).

## autopilots.delete

Prepare irreversible deletion of an Autopilot, every public link in its group, and every Check created through those links. Explicit confirmation is required.

Use when: Use only when the user explicitly asks to permanently delete one known Autopilot; offer autopilots.status.set with ARCHIVED when disabling links while preserving Checks is acceptable.

Returns: after confirmation, deleted group ID, prior status, link and Check counts, and deletion outcome.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_autopilots_delete_prepare`
- Confirmation: required
- Destructive: yes
- Retry safety: `at-most-once`
- Zapier automation: not available

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `autopilotGroupId` | string | Yes | See the JSON Schema definition. |
| `expectedStatus` | `ACTIVE` | `ARCHIVED` | Yes | Current status read from autopilots.get or autopilots.list; used to prevent a stale destructive action. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "autopilotGroupId": "autopilotgroupid_example_01",
      "expectedStatus": "ACTIVE"
    },
    "operationId": "autopilots.delete"
  }
}
```

### Success example

```json
{
  "data": {
    "deleted": true,
    "deletedCheckCount": 1,
    "deletedLinkCount": 1,
    "previousStatus": "active",
    "recordId": "recordid_example_01"
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `outcomeUnknown`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/autopilots.delete.json).

## references.request

Prepare one reference request using an exact manual reference form configured on the Check’s Flow.

Use when: Use after resolving the Check and selecting a template from flows.referenceTemplates.list.

Returns: after confirmation, the created reference ID and invitation delivery status.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_references_request_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: supported

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `applicantId` | string | Yes | See the JSON Schema definition. |
| `referee` | object | Yes | See the JSON Schema definition. |
| `templateId` | string | Yes | See the JSON Schema definition. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "applicantId": "applicantid_example_01",
      "referee": {
        "email": "ada@example.test",
        "name": "Ada Example"
      },
      "templateId": "templateid_example_01"
    },
    "operationId": "references.request"
  }
}
```

### Success example

```json
{
  "data": {
    "emailDispatch": {},
    "meta": {},
    "reference": {}
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `idempotencyConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/references.request.json).

## checks.bulkCreate

Prepare up to 250 Checks from validated structured rows, such as rows parsed from an uploaded spreadsheet. Confirmation creates the Checks as one retry-safe action and queues any candidate invitations configured by the Flow.

Use when: Use after the client has parsed a file into validated fullName and email rows and resolved one authorized Flow ID; never pass a file or URL.

Returns: after confirmation, the created count and each applicant ID with its invitation delivery status.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_checks_bulk_create_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: supported

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `applicants` | array | Yes | See the JSON Schema definition. |
| `flowId` | string | Yes | Exact authorized Hiring Review Flow ID. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "applicants": [
        {
          "email": "ada@example.test",
          "fullName": "Ada Example",
          "sourceRowNumber": 1
        }
      ],
      "flowId": "flow_example_01"
    },
    "operationId": "checks.bulkCreate"
  }
}
```

### Success example

```json
{
  "data": {
    "checks": [
      {
        "applicantId": "applicant_example_01",
        "invitationStatus": "queued",
        "sourceRowNumber": 1
      }
    ],
    "createdCount": 1,
    "errorCount": 0
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `idempotencyConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/checks.bulkCreate.json).

## employees.bulkImport

Prepare an idempotent Employee import from up to 500 validated structured rows. Upsert mode applies Jointl Employee matching, create mode rejects existing matches, and update mode changes only exact Employee and work-record IDs. Company scope and compensation permissions are rechecked at confirmation.

Use when: Use after the client has parsed and validated Employee rows and resolved exact authorized company IDs; use create for Search-or-Create, update for one exact existing work record, and upsert for bulk imports; never pass a file or URL.

Returns: after confirmation, an import summary with created, updated, unchanged, and row-level outcomes.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_employees_bulk_import_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: supported

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `employees` | array | Yes | See the JSON Schema definition. |
| `mode` | `upsert` | `create` | `update` | No | upsert applies Jointl Employee matching; create rejects existing matches; update requires exact employeeId and positionId values. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "employees": [
        {
          "companyId": "company_example_01",
          "email": "ada@example.test",
          "fullName": "Ada Example",
          "positionTitle": "Software Engineer",
          "sourceRowNumber": 1,
          "startAt": "2026-01-15"
        }
      ]
    },
    "operationId": "employees.bulkImport"
  }
}
```

### Success example

```json
{
  "data": {
    "createdCount": 1,
    "employees": [
      {
        "email": "ada@example.test",
        "employeeId": "employee_example_01",
        "fullName": "Ada Example",
        "outcome": "created",
        "positionIds": [
          "position_example_01"
        ],
        "rows": [
          1
        ],
        "status": "active",
        "workRecords": [
          {
            "companyId": "company_example_01",
            "companyName": "Example Company",
            "positionId": "position_example_01",
            "positionTitle": "Software Engineer",
            "startAt": "2026-01-15"
          }
        ]
      }
    ],
    "errorCount": 0,
    "errors": [],
    "unchangedCount": 0,
    "updatedCount": 0
  },
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `idempotencyConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/employees.bulkImport.json).

## checks.addNote

Prepare a note for a visible Check. `visibleToTeam` controls whether other authorized workspace members can see it. A separate human confirmation is required.

Use when: Use only when the user explicitly asks to add text to one authorized Check, after resolving its applicant ID.

Returns: after confirmation, whether the note was added.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_checks_add_note_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: supported

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `applicantId` | string | Yes | See the JSON Schema definition. |
| `text` | string | Yes | Exact note text the user asked to save. |
| `visibleToTeam` | boolean | No | False keeps the note private to its author; true shares it with authorized workspace members. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "applicantId": "applicantid_example_01",
      "text": "Follow up during the next scheduled review."
    },
    "operationId": "checks.addNote"
  }
}
```

### Success example

```json
{
  "data": true,
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `idempotencyConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/checks.addNote.json).

## employees.addNote

Prepare a note for a visible Employee. `visibleToTeam` controls whether other authorized workspace members can see it. A separate human confirmation is required.

Use when: Use only when the user explicitly asks to add text to one authorized Employee, after resolving its Employee ID.

Returns: after confirmation, whether the note was added.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_employees_add_note_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: supported

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `employeeId` | string | Yes | See the JSON Schema definition. |
| `text` | string | Yes | Exact note text the user asked to save. |
| `visibleToTeam` | boolean | No | False keeps the note private to its author; true shares it with authorized workspace members. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "employeeId": "employeeid_example_01",
      "text": "Follow up during the next scheduled review."
    },
    "operationId": "employees.addNote"
  }
}
```

### Success example

```json
{
  "data": true,
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `idempotencyConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/employees.addNote.json).

## talents.addNote

Prepare a note for a company-scoped Talent Pool profile. `visibleToTeam` controls whether other authorized workspace members can see it. A separate human confirmation is required.

Use when: Use only when the user explicitly asks to add text to one authorized Talent Pool profile, after resolving its profile ID.

Returns: after confirmation, whether the note was added.

- Scope: `workspace.write`
- REST: `/api/v1/actions/prepare` → approval → `/api/v1/actions/confirm`
- MCP: `jointl_talents_add_note_prepare`
- Confirmation: required
- Destructive: no
- Retry safety: `idempotent`
- Zapier automation: supported

### Input

| Field | Type | Required | Meaning |
| --- | --- | --- | --- |
| `talentId` | string | Yes | See the JSON Schema definition. |
| `text` | string | Yes | Exact note text the user asked to save. |
| `visibleToTeam` | boolean | No | False keeps the note private to its author; true shares it with authorized workspace members. |

### Request example

```json
{
  "confirm": {
    "confirmationToken": "jtl_confirm_23456789ABCDEFGHJ.example_confirmation_token_000000000000"
  },
  "prepare": {
    "idempotencyKey": "intent.example.0001",
    "input": {
      "talentId": "talentid_example_01",
      "text": "Follow up during the next scheduled review."
    },
    "operationId": "talents.addNote"
  }
}
```

### Success example

```json
{
  "data": true,
  "requestId": "request_example_01"
}
```

Applicable shared errors: `invalidInput`, `notAuthorized`, `rateLimited`, `confirmationExpired`, `stateConflict`, `idempotencyConflict`. See [shared errors](/examples/shared/errors.json) and the complete [operation example](/examples/operations/talents.addNote.json).
