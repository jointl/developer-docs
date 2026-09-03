---
title: MCP tools and skills
description: "A fully authorized connection can expose 50 tools: 26 reads, 23 prepare tools, and jointl_confirm_action."
---

A fully authorized connection can expose 50 tools: 26 reads, 23 prepare tools, and `jointl_confirm_action`. Each client sees only the tools allowed by its scopes and active Jointl permissions.

The protocol uses JSON Schema 2020-12. Tool results include JSON in `structuredContent.result` and the equivalent serialized text block for clients that require it.

## Tools

| Tool | Logical operation | Annotations |
| --- | --- | --- |
| [`jointl_workspace_get`](#jointl-workspace-get) | `workspace.get` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_workspace_search`](#jointl-workspace-search) | `workspace.search` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_companies_list`](#jointl-companies-list) | `companies.list` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_flows_list`](#jointl-flows-list) | `flows.list` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_flows_get`](#jointl-flows-get) | `flows.get` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_flows_capabilities_get`](#jointl-flows-capabilities-get) | `flows.capabilities.get` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_flows_templates_list`](#jointl-flows-templates-list) | `flows.templates.list` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_flows_questions_search`](#jointl-flows-questions-search) | `flows.questions.search` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_flows_reference_templates_list`](#jointl-flows-reference-templates-list) | `flows.referenceTemplates.list` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_flows_blueprint_get`](#jointl-flows-blueprint-get) | `flows.blueprint.get` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_performance_operations_get`](#jointl-performance-operations-get) | `performance.operations.get` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_glow_moments_send_prepare`](#jointl-glow-moments-send-prepare) | `glowMoments.send` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_glow_moments_cycle_status_set_prepare`](#jointl-glow-moments-cycle-status-set-prepare) | `glowMoments.cycle.status.set` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_team_pulse_send_prepare`](#jointl-team-pulse-send-prepare) | `teamPulse.send` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_team_pulse_cycle_status_set_prepare`](#jointl-team-pulse-cycle-status-set-prepare) | `teamPulse.cycle.status.set` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_checks_list`](#jointl-checks-list) | `checks.list` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_checks_analytics`](#jointl-checks-analytics) | `checks.analytics` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_checks_get`](#jointl-checks-get) | `checks.get` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_checks_report`](#jointl-checks-report) | `checks.report` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_references_list`](#jointl-references-list) | `references.list` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_references_get`](#jointl-references-get) | `references.get` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_employees_list`](#jointl-employees-list) | `employees.list` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_employees_analytics`](#jointl-employees-analytics) | `employees.analytics` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_employees_get`](#jointl-employees-get) | `employees.get` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_talents_list`](#jointl-talents-list) | `talents.list` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_talents_get`](#jointl-talents-get) | `talents.get` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_talents_references_list`](#jointl-talents-references-list) | `talents.references.list` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_autopilots_list`](#jointl-autopilots-list) | `autopilots.list` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_autopilots_get`](#jointl-autopilots-get) | `autopilots.get` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_insights_get`](#jointl-insights-get) | `insights.get` | readOnly=true; destructive=false; idempotent=true; openWorld=false |
| [`jointl_flows_draft_create_prepare`](#jointl-flows-draft-create-prepare) | `flows.draft.create` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_flows_draft_revise_prepare`](#jointl-flows-draft-revise-prepare) | `flows.draft.revise` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_flows_status_set_prepare`](#jointl-flows-status-set-prepare) | `flows.status.set` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_flows_delete_prepare`](#jointl-flows-delete-prepare) | `flows.delete` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_checks_status_set_prepare`](#jointl-checks-status-set-prepare) | `checks.status.set` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_checks_delete_prepare`](#jointl-checks-delete-prepare) | `checks.delete` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_employees_status_set_prepare`](#jointl-employees-status-set-prepare) | `employees.status.set` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_employees_delete_prepare`](#jointl-employees-delete-prepare) | `employees.delete` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_talents_status_set_prepare`](#jointl-talents-status-set-prepare) | `talents.status.set` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_autopilots_create_prepare`](#jointl-autopilots-create-prepare) | `autopilots.create` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_autopilots_links_generate_prepare`](#jointl-autopilots-links-generate-prepare) | `autopilots.links.generate` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_autopilots_status_set_prepare`](#jointl-autopilots-status-set-prepare) | `autopilots.status.set` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_autopilots_delete_prepare`](#jointl-autopilots-delete-prepare) | `autopilots.delete` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_references_request_prepare`](#jointl-references-request-prepare) | `references.request` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_checks_bulk_create_prepare`](#jointl-checks-bulk-create-prepare) | `checks.bulkCreate` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_employees_bulk_import_prepare`](#jointl-employees-bulk-import-prepare) | `employees.bulkImport` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_checks_add_note_prepare`](#jointl-checks-add-note-prepare) | `checks.addNote` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_employees_add_note_prepare`](#jointl-employees-add-note-prepare) | `employees.addNote` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_talents_add_note_prepare`](#jointl-talents-add-note-prepare) | `talents.addNote` | readOnly=false; destructive=false; idempotent=true; openWorld=false |
| [`jointl_confirm_action`](#jointl-confirm-action) | prepared write confirmation | readOnly=false; destructive=true; idempotent=true; openWorld=true |

## jointl_workspace_get

Get workspace access. Return the current Jointl workspace and the access granted to the member.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{}
```

Full JSON-RPC example: [jointl_workspace_get](/artifacts/mcp/tool-calls/jointl_workspace_get.json).

## jointl_workspace_search

Search Jointl. Quickly search the connected workspace across authorized people, emails, attributes, companies, tags, job titles, and Flows using the same permissions and relevance ranking as the Jointl UI. An optional source-type filter is applied before ranking. Returns at most 30 top matches and is not an exhaustive list.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{
  "query": "Ada Example"
}
```

Full JSON-RPC example: [jointl_workspace_search](/artifacts/mcp/tool-calls/jointl_workspace_search.json).

## jointl_companies_list

List companies. List Jointl companies visible through the member’s current company scope.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{}
```

Full JSON-RPC example: [jointl_companies_list](/artifacts/mcp/tool-calls/jointl_companies_list.json).

## jointl_flows_list

List Flows. List Flows available through the member’s role, sharing, ownership, and company access.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{}
```

Full JSON-RPC example: [jointl_flows_list](/artifacts/mcp/tool-calls/jointl_flows_list.json).

## jointl_flows_get

Get Flow. Get one visible Flow. Sensitive automation tokens are never returned.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{
  "flowId": "flowid_example_01"
}
```

Full JSON-RPC example: [jointl_flows_get](/artifacts/mcp/tool-calls/jointl_flows_get.json).

## jointl_flows_capabilities_get

Get Flow authoring capabilities. Read supported Flow types, sections, question types, valid section ordering, current authoring permissions, and protected actions before proposing a Flow.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{}
```

Full JSON-RPC example: [jointl_flows_capabilities_get](/artifacts/mcp/tool-calls/jointl_flows_capabilities_get.json).

## jointl_flows_templates_list

List Flow templates. List visible Private and Public Jointl Library templates in one category, including their questions, so an assistant can reuse workspace content and valid IDs.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{
  "kind": "preScreening"
}
```

Full JSON-RPC example: [jointl_flows_templates_list](/artifacts/mcp/tool-calls/jointl_flows_templates_list.json).

## jointl_flows_questions_search

Search Flow questions. Search relevant questions across visible pre-screening, assessment, test, reference, exit, and Team Pulse templates without loading entire catalogs into the assistant context.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{
  "query": "Ada Example"
}
```

Full JSON-RPC example: [jointl_flows_questions_search](/artifacts/mcp/tool-calls/jointl_flows_questions_search.json).

## jointl_flows_reference_templates_list

List manual reference templates for a Flow. List the exact reference forms configured for manual collection on one visible Flow.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{
  "flowId": "flowid_example_01"
}
```

Full JSON-RPC example: [jointl_flows_reference_templates_list](/artifacts/mcp/tool-calls/jointl_flows_reference_templates_list.json).

## jointl_flows_blueprint_get

Get complete Flow blueprint. Read one visible Flow’s latest editable configuration and expanded question/template design. Sensitive automation tokens and protected automation settings are excluded.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{
  "flowId": "flowid_example_01"
}
```

Full JSON-RPC example: [jointl_flows_blueprint_get](/artifacts/mcp/tool-calls/jointl_flows_blueprint_get.json).

## jointl_performance_operations_get

Get Glow Moments and Team Pulse operations. Read one visible Performance Flow’s participants, cadence, recent Glow Moments and Team Pulse cycles, and completion state. Shareable participant and scoreboard links are returned only when explicitly requested.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{
  "flowId": "flowid_example_01"
}
```

Full JSON-RPC example: [jointl_performance_operations_get](/artifacts/mcp/tool-calls/jointl_performance_operations_get.json).

## jointl_glow_moments_send_prepare

Prepare Glow Moments send. Prepare a manual Glow Moments cycle for every configured participant in one active Performance Flow. This queues private requests and messages, so explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "flowId": "flowid_example_01"
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_glow_moments_send_prepare](/artifacts/mcp/tool-calls/jointl_glow_moments_send_prepare.json).

## jointl_glow_moments_cycle_status_set_prepare

Prepare Glow Moments cycle status change. Prepare cancellation or restoration of one exact Glow Moments cycle using its current status for concurrency safety. Explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "cycleId": "cycleid_example_01",
    "enabled": true,
    "expectedStatus": "CANCELLED"
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_glow_moments_cycle_status_set_prepare](/artifacts/mcp/tool-calls/jointl_glow_moments_cycle_status_set_prepare.json).

## jointl_team_pulse_send_prepare

Prepare Team Pulse send. Prepare a manual Team Pulse cycle using the configured form for every participant in one active Performance Flow. This queues private requests and messages, so explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "flowId": "flowid_example_01"
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_team_pulse_send_prepare](/artifacts/mcp/tool-calls/jointl_team_pulse_send_prepare.json).

## jointl_team_pulse_cycle_status_set_prepare

Prepare Team Pulse cycle status change. Prepare cancellation or restoration of one exact Team Pulse cycle using its current status for concurrency safety. Explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "cycleId": "cycleid_example_01",
    "enabled": true,
    "expectedStatus": "CANCELLED"
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_team_pulse_cycle_status_set_prepare](/artifacts/mcp/tool-calls/jointl_team_pulse_cycle_status_set_prepare.json).

## jointl_checks_list

List Checks. List Checks visible through the member’s role, sharing, creator, manager, and company permissions.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{}
```

Full JSON-RPC example: [jointl_checks_list](/artifacts/mcp/tool-calls/jointl_checks_list.json).

## jointl_checks_analytics

Analyze Check evidence. Return a paginated, evidence-based ranking within each visible Flow, including matching scores, measured high and low evidence, evidence coverage, and verification state. It never recommends an employment decision.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{}
```

Full JSON-RPC example: [jointl_checks_analytics](/artifacts/mcp/tool-calls/jointl_checks_analytics.json).

## jointl_checks_get

Get one Check. Return the profile, Flow context, recent visible activity, and optional condensed evidence for one authorized Check. Sensitive access tokens are never returned.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{
  "applicantId": "applicantid_example_01"
}
```

Full JSON-RPC example: [jointl_checks_get](/artifacts/mcp/tool-calls/jointl_checks_get.json).

## jointl_checks_report

Get Check report. Return the authorized full factual Check report, including open-text answers, answered AI follow-ups, Tests, reference narratives and integrity context, employment confirmations, attributes, and scores—but no hiring recommendation.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{
  "applicantId": "applicantid_example_01"
}
```

Full JSON-RPC example: [jointl_checks_report](/artifacts/mcp/tool-calls/jointl_checks_report.json).

## jointl_references_list

List reference responses for a Check. List authorized reference request and completion summaries for one visible Check with stable cursor pagination.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{
  "applicantId": "applicantid_example_01"
}
```

Full JSON-RPC example: [jointl_references_list](/artifacts/mcp/tool-calls/jointl_references_list.json).

## jointl_references_get

Get one reference response. Return one authorized, normalized reference response and its Check-level average metrics.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{
  "referenceId": "referenceid_example_01"
}
```

Full JSON-RPC example: [jointl_references_get](/artifacts/mcp/tool-calls/jointl_references_get.json).

## jointl_employees_list

List Employees. List Employees visible through the member’s role, sharing, manager, creator, and company permissions.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{}
```

Full JSON-RPC example: [jointl_employees_list](/artifacts/mcp/tool-calls/jointl_employees_list.json).

## jointl_employees_analytics

Analyze Employee performance evidence. Return a pageable factual ranking and review signals from Team Pulse and Glow Moments for only the Employees visible to the member. It never recommends an employment decision.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{}
```

Full JSON-RPC example: [jointl_employees_analytics](/artifacts/mcp/tool-calls/jointl_employees_analytics.json).

## jointl_employees_get

Get one Employee. Return the profile, current work context, recent visible activity, and optional performance evidence for one authorized Employee.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{
  "employeeId": "employeeid_example_01"
}
```

Full JSON-RPC example: [jointl_employees_get](/artifacts/mcp/tool-calls/jointl_employees_get.json).

## jointl_talents_list

List Talent Pool profiles. List company-scoped Talent Pool profiles. Profiles without an authorized company match are not returned.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{}
```

Full JSON-RPC example: [jointl_talents_list](/artifacts/mcp/tool-calls/jointl_talents_list.json).

## jointl_talents_get

Get one Talent Pool profile. Return the profile and optional evidence overview for one company-scoped Talent Pool person.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{
  "talentId": "talentid_example_01"
}
```

Full JSON-RPC example: [jointl_talents_get](/artifacts/mcp/tool-calls/jointl_talents_get.json).

## jointl_talents_references_list

List Talent Pool reference responses. Return reference responses only when both Talent Pool and response permissions allow it.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{
  "talentId": "talentid_example_01"
}
```

Full JSON-RPC example: [jointl_talents_references_list](/artifacts/mcp/tool-calls/jointl_talents_references_list.json).

## jointl_autopilots_list

List Autopilots. List Autopilot groups available through the member’s current permissions and Flow or company access. Shareable access links are omitted from list results.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{}
```

Full JSON-RPC example: [jointl_autopilots_list](/artifacts/mcp/tool-calls/jointl_autopilots_list.json).

## jointl_autopilots_get

Get Autopilot and public links. Return one visible Autopilot and its reusable public access links. Anyone holding an active link can start the attached Flow.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{
  "autopilotGroupId": "autopilotgroupid_example_01"
}
```

Full JSON-RPC example: [jointl_autopilots_get](/artifacts/mcp/tool-calls/jointl_autopilots_get.json).

## jointl_insights_get

Get Jointl Insights. Return the General, Performance, or Exit Intelligence view available to the member for an inclusive UTC date range, using the same calculations shown in Jointl.

Requires `workspace.read`. This is a read-only tool.

Request input:

```json
{}
```

Full JSON-RPC example: [jointl_insights_get](/artifacts/mcp/tool-calls/jointl_insights_get.json).

## jointl_flows_draft_create_prepare

Prepare a new Flow draft. Prepare a complete, unpublished Flow draft using visible library templates and optional original question blocks. Hiring drafts enable Public Profiles and, when available for the workspace, Talent Pool by default. No invitations, publishing, team sharing, third-party automation, or automatic candidate decisions occur. Explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "design": {
      "companyId": "company_example_01",
      "jobTitle": "Software Engineer",
      "title": "Example Hiring Flow",
      "type": "HIRING_REVIEW"
    }
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_flows_draft_create_prepare](/artifacts/mcp/tool-calls/jointl_flows_draft_create_prepare.json).

## jointl_flows_draft_revise_prepare

Prepare a Flow draft revision. Prepare a replacement of supported sections in one unpublished Flow. The latest blueprint revision is required so concurrent edits are not overwritten. Publishing, team sharing, Public Profiles, Talent Pool, third-party automation, automatic candidate decisions, and messaging remain unchanged. Explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
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
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_flows_draft_revise_prepare](/artifacts/mcp/tool-calls/jointl_flows_draft_revise_prepare.json).

## jointl_flows_status_set_prepare

Prepare Flow status change. Prepare a Flow publish, archive, or restore action using the current Flow status to prevent conflicting changes. Publishing validates that the Flow is ready; archiving cancels pending requests and scheduled activity for the Flow. Explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "expectedStatus": "ACTIVE",
    "flowId": "flowid_example_01",
    "status": "ARCHIVED"
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_flows_status_set_prepare](/artifacts/mcp/tool-calls/jointl_flows_status_set_prepare.json).

## jointl_flows_delete_prepare

Prepare Flow deletion. Prepare irreversible deletion of one visible Flow and its related Checks, Autopilots, pending activity, and Performance cycle data. Explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "expectedStatus": "ACTIVE",
    "flowId": "flowid_example_01"
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_flows_delete_prepare](/artifacts/mcp/tool-calls/jointl_flows_delete_prepare.json).

## jointl_checks_status_set_prepare

Prepare Check status change. Prepare a status change for one authorized Check using its current status to prevent conflicting changes. The `selected` status is not available because candidate selection uses the separate Employee conversion workflow. Explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "applicantId": "applicantid_example_01",
    "expectedStatus": "new",
    "status": "archived"
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_checks_status_set_prepare](/artifacts/mcp/tool-calls/jointl_checks_status_set_prepare.json).

## jointl_checks_delete_prepare

Prepare Check deletion. Prepare irreversible deletion of one visible Check and its pre-screening, assessment, reference, feedback, verification, and pending lifecycle data. Explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "applicantId": "applicantid_example_01",
    "expectedStatus": "new"
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_checks_delete_prepare](/artifacts/mcp/tool-calls/jointl_checks_delete_prepare.json).

## jointl_employees_status_set_prepare

Prepare Employee status change. Prepare an active or left status change for one authorized Employee using the current status to prevent conflicting changes. Marking left requires an end date for every active position and can optionally launch an Exit Intelligence Flow; an Employee already marked left may use the same operation solely to send Exit Intelligence. Explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "employeeId": "employeeid_example_01",
    "expectedStatus": "left",
    "status": "active"
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_employees_status_set_prepare](/artifacts/mcp/tool-calls/jointl_employees_status_set_prepare.json).

## jointl_employees_delete_prepare

Prepare Employee deletion. Prepare irreversible deletion of one visible Employee, removal from manager and Glow Moment assignments, and cancellation of incomplete requests and scheduled activity for the Employee. Explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "employeeId": "employeeid_example_01",
    "expectedStatus": "active"
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_employees_delete_prepare](/artifacts/mcp/tool-calls/jointl_employees_delete_prepare.json).

## jointl_talents_status_set_prepare

Prepare Talent Pool status change. Prepare a new, shortlisted, or archived status change for one company-scoped Talent Pool profile using its current status to prevent conflicting changes. Explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "expectedStatus": "new",
    "status": "archived",
    "talentId": "talentid_example_01"
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_talents_status_set_prepare](/artifacts/mcp/tool-calls/jointl_talents_status_set_prepare.json).

## jointl_autopilots_create_prepare

Prepare Autopilot run and public links. Prepare a new Autopilot for one active visible Hiring Review Flow and generate reusable public access links. Anyone with a link can start the Flow. Explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "flowId": "flowid_example_01"
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_autopilots_create_prepare](/artifacts/mcp/tool-calls/jointl_autopilots_create_prepare.json).

## jointl_autopilots_links_generate_prepare

Prepare additional Autopilot links. Prepare additional reusable public access links for one active Autopilot. Explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "autopilotGroupId": "autopilotgroupid_example_01"
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_autopilots_links_generate_prepare](/artifacts/mcp/tool-calls/jointl_autopilots_links_generate_prepare.json).

## jointl_autopilots_status_set_prepare

Prepare Autopilot status change. Prepare an Autopilot archive or restore action. Archiving disables every public link in the group while preserving its Checks. Explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "autopilotGroupId": "autopilotgroupid_example_01",
    "expectedStatus": "ACTIVE",
    "status": "ARCHIVED"
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_autopilots_status_set_prepare](/artifacts/mcp/tool-calls/jointl_autopilots_status_set_prepare.json).

## jointl_autopilots_delete_prepare

Prepare Autopilot deletion. Prepare irreversible deletion of an Autopilot, every public link in its group, and every Check created through those links. Explicit confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "autopilotGroupId": "autopilotgroupid_example_01",
    "expectedStatus": "ACTIVE"
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_autopilots_delete_prepare](/artifacts/mcp/tool-calls/jointl_autopilots_delete_prepare.json).

## jointl_references_request_prepare

Prepare a reference request. Prepare one reference request using an exact manual reference form configured on the Check’s Flow.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "applicantId": "applicantid_example_01",
    "referee": {
      "email": "ada@example.test",
      "name": "Ada Example"
    },
    "templateId": "templateid_example_01"
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_references_request_prepare](/artifacts/mcp/tool-calls/jointl_references_request_prepare.json).

## jointl_checks_bulk_create_prepare

Prepare bulk Checks. Prepare up to 250 Checks from validated structured rows, such as rows parsed from an uploaded spreadsheet. Confirmation creates the Checks as one retry-safe action and queues any candidate invitations configured by the Flow.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
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
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_checks_bulk_create_prepare](/artifacts/mcp/tool-calls/jointl_checks_bulk_create_prepare.json).

## jointl_employees_bulk_import_prepare

Prepare bulk Employee import. Prepare an idempotent Employee import from up to 500 validated structured rows. Upsert mode applies Jointl Employee matching, create mode rejects existing matches, and update mode changes only exact Employee and work-record IDs. Company scope and compensation permissions are rechecked at confirmation.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
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
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_employees_bulk_import_prepare](/artifacts/mcp/tool-calls/jointl_employees_bulk_import_prepare.json).

## jointl_checks_add_note_prepare

Prepare Check note. Prepare a note for a visible Check. `visibleToTeam` controls whether other authorized workspace members can see it. A separate human confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "applicantId": "applicantid_example_01",
    "text": "Follow up during the next scheduled review."
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_checks_add_note_prepare](/artifacts/mcp/tool-calls/jointl_checks_add_note_prepare.json).

## jointl_employees_add_note_prepare

Prepare Employee note. Prepare a note for a visible Employee. `visibleToTeam` controls whether other authorized workspace members can see it. A separate human confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "employeeId": "employeeid_example_01",
    "text": "Follow up during the next scheduled review."
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_employees_add_note_prepare](/artifacts/mcp/tool-calls/jointl_employees_add_note_prepare.json).

## jointl_talents_add_note_prepare

Prepare Talent Pool note. Prepare a note for a company-scoped Talent Pool profile. `visibleToTeam` controls whether other authorized workspace members can see it. A separate human confirmation is required.

Requires `workspace.write`. This tool only prepares; show the exact preview and obtain explicit approval before calling `jointl_confirm_action`.

Request input:

```json
{
  "input": {
    "talentId": "talentid_example_01",
    "text": "Follow up during the next scheduled review."
  },
  "idempotencyKey": "intent.example.0001"
}
```

Full JSON-RPC example: [jointl_talents_add_note_prepare](/artifacts/mcp/tool-calls/jointl_talents_add_note_prepare.json).

## jointl_confirm_action

Confirms one unexpired prepared action after explicit approval of its exact preview. The tool may complete an idempotent replay; an at-most-once unknown outcome must be reconciled and never blindly retried.

Full JSON-RPC example: [jointl_confirm_action](/artifacts/mcp/tool-calls/jointl_confirm_action.json).

## Skills extension

Jointl advertises the custom `io.modelcontextprotocol/skills` extension. `skills/list` returns manifests, `skills/get` returns one manifest, and standard MCP resources expose the declared `skill://jointl/...` content. Clients may ignore the extension safely.

| Skill | Description | Resources |
| --- | --- | --- |
| `analyze-jointl-checks` | Analyze authorized Jointl Checks and candidate evidence. Use for top-candidate, ranking, score, strengths, weaknesses, verification, reference, assessment, pre-screening, or individual Check-report requests. Do not use to make or automate hiring decisions. | 1 |
| `analyze-jointl-employees` | Analyze authorized Jointl Employee, workforce, and Insights evidence. Use for workspace activity, completion or satisfaction metrics, performance ranking, strengths, needs-attention, Team Pulse, Glow Moments, workload, manager support, Exit Intelligence, date-range dashboards, or individual Employee detail. Do not use to make disciplinary or termination decisions. | 1 |
| `design-jointl-flow` | Design, create, revise, publish, archive, or operate a complete Jointl Flow for Hiring Review, Exit Intelligence, or Performance (Glow Moments and Team Pulse). Use for role assessments, pre-screening, Tests, references, exit feedback, Employee participants, cadence, cycle sends, Autopilot links, or improving an existing Flow. Do not use merely to find or summarize a Flow. | 2 |
| `find-jointl-records` | Search and retrieve authorized Jointl companies, Flows, Checks, Employees, Talent Pool profiles, and Autopilots. Use to find a person, Flow, or Autopilot, look up an email, attribute, company, tag, or job title, browse a domain, or get factual detail for a known record. Do not use for cohort ranking or bulk imports. | 1 |
| `import-jointl-people` | Validate an uploaded spreadsheet or structured rows and prepare bulk Jointl Checks or Employee imports. Use when the user wants to run Checks for many candidates or create or update many Employees. Do not use for a single record or for files the user has not supplied. | 1 |

Review the [`initialize`](/artifacts/mcp/initialize.json), [`tools/list`](/artifacts/mcp/tools-list.json), and [`skills/list`](/artifacts/mcp/skills-list.json) examples.
