---
title: Zapier component reference
description: Jointl for Zapier 1.0.0 supports 16 triggers, 7 searches, and 14 actions.
---

Jointl for Zapier 1.0.0 supports 16 triggers, 7 searches, and 14 actions. It targets Zapier Platform 19.1.0.

All actions require Source Event ID even where it is omitted from the abbreviated tables below. The field provides the retry-safe identity described in the [Zapier guide](/integrations/zapier/index).

## Available components

| Kind | Key | Label | Jointl operation |
| --- | --- | --- | --- |
| trigger | `new_check` | New Check | `events.list` / `events.get` |
| trigger | `check_status_changed` | Check Status Changed | `events.list` / `events.get` |
| trigger | `check_completed` | Check Completed | `events.list` / `events.get` |
| trigger | `verification_check_completed` | Verification Check Completed | `events.list` / `events.get` |
| trigger | `verification_check_failed` | Verification Check Failed | `events.list` / `events.get` |
| trigger | `public_profile_discovery_completed` | Public Profile Discovery Completed | `events.list` / `events.get` |
| trigger | `public_profile_discovery_failed` | Public Profile Discovery Failed | `events.list` / `events.get` |
| trigger | `reference_completed` | Reference Completed | `events.list` / `events.get` |
| trigger | `new_employee` | New Employee | `events.list` / `events.get` |
| trigger | `employee_work_details_changed` | Employee Work Details Changed | `events.list` / `events.get` |
| trigger | `employee_status_changed` | Employee Status Changed | `events.list` / `events.get` |
| trigger | `exit_intelligence_request_created` | Exit Intelligence Request Created | `events.list` / `events.get` |
| trigger | `exit_intelligence_completed` | Exit Intelligence Completed | `events.list` / `events.get` |
| trigger | `new_talent` | New Talent | `events.list` / `events.get` |
| trigger | `talent_profile_submitted` | Talent Profile Submitted From Reference | `events.list` / `events.get` |
| trigger | `talent_status_changed` | Talent Pool Status Changed | `events.list` / `events.get` |
| search | `find_person` | Find Person | `workspace.search` |
| search | `find_check_report` | Find Check Report | `checks.report` |
| search | `find_reference_response` | Find Reference Response | `references.get` |
| search | `find_references_for_check` | Find References for Check | `references.list` |
| search | `find_verification_results` | Find Verification Results | `checks.verifications.get` |
| search | `find_public_profile_results` | Find Public Profile Results | `checks.publicProfiles.get` |
| search | `find_exit_intelligence_result` | Find Exit Intelligence Result | `employees.exitIntelligence.get` |
| action | `create_check_send_invitation` | Create Check & Send Flow Invitation | `checks.bulkCreate` |
| action | `bulk_create_checks` | Create Checks in Bulk & Send Flow Invitations | `checks.bulkCreate` |
| action | `send_reference_request` | Send Reference Request | `references.request` |
| action | `update_employee` | Update Employee | `employees.bulkImport` |
| action | `bulk_import_employees` | Import Employees in Bulk | `employees.bulkImport` |
| action | `run_all_verification_checks` | Run All Available Verification Checks | `checks.verifications.runAll` |
| action | `start_public_profile_discovery` | Start Public Profile Discovery | `checks.publicProfiles.find` |
| action | `change_check_status` | Change Check Status | `checks.status.set` |
| action | `change_employee_status` | Change Employee Status | `employees.status.set` |
| action | `change_talent_status` | Change Talent Pool Status | `talents.status.set` |
| action | `send_exit_intelligence_request` | Send Exit Intelligence Request | `employees.status.set` |
| action | `add_note_to_check` | Add Note to Check | `checks.addNote` |
| action | `add_note_to_employee` | Add Note to Employee | `employees.addNote` |
| action | `add_note_to_talent` | Add Note to Talent | `talents.addNote` |

## New Check

- Zapier key: `new_check`
- Kind: trigger

Triggers when a new Check is created.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `flow_id` | Flow | string | No | Optional. Trigger only for this Flow. Choices: . |
| `company_id` | Company | string | No | Optional. Trigger only for this company. Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Event ID | string | No |  |
| `event_type` | Event Type | string | No |  |
| `occurred_at` | Occurred At | datetime | No |  |
| `entity_id` | Record ID | string | No |  |
| `entity_type` | Record Type | string | No |  |
| `check_id` | Check ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `company_ids` | Company IDs | string | No |  |
| `changed_fields` | Changed Fields | string | No |  |
| `previous_status` | Previous Status | string | No |  |
| `current_status` | Current Status | string | No |  |
| `run_id` | Run ID | string | No |  |
| `run_group_id` | Run Group ID | string | No |  |
| `verification_type` | Verification Type | string | No |  |
| `verification_label` | Verification Label | string | No |  |
| `run_status` | Run Status | string | No |  |
| `run_outcome` | Run Outcome | string | No |  |
| `graph_node_count` | Profile Graph Nodes | integer | No |  |
| `graph_edge_count` | Profile Graph Edges | integer | No |  |
| `graph_cluster_count` | Profile Graph Clusters | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `record_name` | Record Name | string | No |  |
| `record_first_name` | Record First Name | string | No |  |
| `record_last_name` | Record Last Name | string | No |  |
| `record_email` | Record Email | string | No |  |
| `record_status` | Record Status | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `flow_title` | Flow Title | string | No |  |
| `position_title` | Position Title | string | No |  |
| `data` | Jointl Data | value | No |  |

### Sample output

```json
{
  "changed_fields": [],
  "check_id": "check_id",
  "company_id": "company_id",
  "company_ids": [
    "company_id"
  ],
  "company_name": "Example Company",
  "current_status": null,
  "data": {
    "profile": {
      "_id": "check_id",
      "email": "alex@example.com",
      "fullName": "Alex Example"
    }
  },
  "employee_id": null,
  "entity_id": "check_id",
  "entity_type": "check",
  "event_type": "check.created",
  "exit_intelligence_request_id": null,
  "flow_id": "flow_id",
  "flow_title": "Example Hiring Flow",
  "graph_cluster_count": null,
  "graph_edge_count": null,
  "graph_node_count": null,
  "id": "evt_example",
  "jointl_url": "https://join.tl/checks/check_id",
  "occurred_at": "2026-01-01T12:00:00.000Z",
  "position_title": "Software Engineer",
  "previous_status": null,
  "record_email": "alex@example.com",
  "record_first_name": "Alex",
  "record_last_name": "Example",
  "record_name": "Alex Example",
  "record_status": null,
  "reference_id": null,
  "run_group_id": null,
  "run_id": null,
  "run_outcome": null,
  "run_status": null,
  "talent_id": null,
  "verification_label": null,
  "verification_type": null
}
```

## Check Status Changed

- Zapier key: `check_status_changed`
- Kind: trigger

Triggers when a Check moves to another status.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `flow_id` | Flow | string | No | Optional. Trigger only for this Flow. Choices: . |
| `company_id` | Company | string | No | Optional. Trigger only for this company. Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Event ID | string | No |  |
| `event_type` | Event Type | string | No |  |
| `occurred_at` | Occurred At | datetime | No |  |
| `entity_id` | Record ID | string | No |  |
| `entity_type` | Record Type | string | No |  |
| `check_id` | Check ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `company_ids` | Company IDs | string | No |  |
| `changed_fields` | Changed Fields | string | No |  |
| `previous_status` | Previous Status | string | No |  |
| `current_status` | Current Status | string | No |  |
| `run_id` | Run ID | string | No |  |
| `run_group_id` | Run Group ID | string | No |  |
| `verification_type` | Verification Type | string | No |  |
| `verification_label` | Verification Label | string | No |  |
| `run_status` | Run Status | string | No |  |
| `run_outcome` | Run Outcome | string | No |  |
| `graph_node_count` | Profile Graph Nodes | integer | No |  |
| `graph_edge_count` | Profile Graph Edges | integer | No |  |
| `graph_cluster_count` | Profile Graph Clusters | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `record_name` | Record Name | string | No |  |
| `record_first_name` | Record First Name | string | No |  |
| `record_last_name` | Record Last Name | string | No |  |
| `record_email` | Record Email | string | No |  |
| `record_status` | Record Status | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `flow_title` | Flow Title | string | No |  |
| `position_title` | Position Title | string | No |  |
| `data` | Jointl Data | value | No |  |

### Sample output

```json
{
  "changed_fields": [
    "status"
  ],
  "check_id": "check_id",
  "company_id": "company_id",
  "company_ids": [
    "company_id"
  ],
  "company_name": "Example Company",
  "current_status": "IN_PROGRESS",
  "data": {
    "profile": {
      "_id": "check_id",
      "email": "alex@example.com",
      "fullName": "Alex Example"
    }
  },
  "employee_id": null,
  "entity_id": "check_id",
  "entity_type": "check",
  "event_type": "check.status_changed",
  "exit_intelligence_request_id": null,
  "flow_id": "flow_id",
  "flow_title": "Example Hiring Flow",
  "graph_cluster_count": null,
  "graph_edge_count": null,
  "graph_node_count": null,
  "id": "evt_example",
  "jointl_url": "https://join.tl/checks/check_id",
  "occurred_at": "2026-01-01T12:00:00.000Z",
  "position_title": "Software Engineer",
  "previous_status": "NEW",
  "record_email": "alex@example.com",
  "record_first_name": "Alex",
  "record_last_name": "Example",
  "record_name": "Alex Example",
  "record_status": "IN_PROGRESS",
  "reference_id": null,
  "run_group_id": null,
  "run_id": null,
  "run_outcome": null,
  "run_status": null,
  "talent_id": null,
  "verification_label": null,
  "verification_type": null
}
```

## Check Completed

- Zapier key: `check_completed`
- Kind: trigger

Triggers when a candidate completes a Flow.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `flow_id` | Flow | string | No | Optional. Trigger only for this Flow. Choices: . |
| `company_id` | Company | string | No | Optional. Trigger only for this company. Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Event ID | string | No |  |
| `event_type` | Event Type | string | No |  |
| `occurred_at` | Occurred At | datetime | No |  |
| `entity_id` | Record ID | string | No |  |
| `entity_type` | Record Type | string | No |  |
| `check_id` | Check ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `company_ids` | Company IDs | string | No |  |
| `changed_fields` | Changed Fields | string | No |  |
| `previous_status` | Previous Status | string | No |  |
| `current_status` | Current Status | string | No |  |
| `run_id` | Run ID | string | No |  |
| `run_group_id` | Run Group ID | string | No |  |
| `verification_type` | Verification Type | string | No |  |
| `verification_label` | Verification Label | string | No |  |
| `run_status` | Run Status | string | No |  |
| `run_outcome` | Run Outcome | string | No |  |
| `graph_node_count` | Profile Graph Nodes | integer | No |  |
| `graph_edge_count` | Profile Graph Edges | integer | No |  |
| `graph_cluster_count` | Profile Graph Clusters | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `record_name` | Record Name | string | No |  |
| `record_first_name` | Record First Name | string | No |  |
| `record_last_name` | Record Last Name | string | No |  |
| `record_email` | Record Email | string | No |  |
| `record_status` | Record Status | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `flow_title` | Flow Title | string | No |  |
| `position_title` | Position Title | string | No |  |
| `data` | Jointl Data | value | No |  |

### Sample output

```json
{
  "changed_fields": [],
  "check_id": "check_id",
  "company_id": "company_id",
  "company_ids": [
    "company_id"
  ],
  "company_name": "Example Company",
  "current_status": null,
  "data": {
    "profile": {
      "_id": "check_id",
      "email": "alex@example.com",
      "fullName": "Alex Example"
    }
  },
  "employee_id": null,
  "entity_id": "check_id",
  "entity_type": "check",
  "event_type": "check.completed",
  "exit_intelligence_request_id": null,
  "flow_id": "flow_id",
  "flow_title": "Example Hiring Flow",
  "graph_cluster_count": null,
  "graph_edge_count": null,
  "graph_node_count": null,
  "id": "evt_example",
  "jointl_url": "https://join.tl/checks/check_id",
  "occurred_at": "2026-01-01T12:00:00.000Z",
  "position_title": "Software Engineer",
  "previous_status": null,
  "record_email": "alex@example.com",
  "record_first_name": "Alex",
  "record_last_name": "Example",
  "record_name": "Alex Example",
  "record_status": null,
  "reference_id": null,
  "run_group_id": null,
  "run_id": null,
  "run_outcome": null,
  "run_status": null,
  "talent_id": null,
  "verification_label": null,
  "verification_type": null
}
```

## Verification Check Completed

- Zapier key: `verification_check_completed`
- Kind: trigger

Triggers when one verification check finishes. Use Find Verification Results when a later step needs detailed findings.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `flow_id` | Flow | string | No | Optional. Trigger only for this Flow. Choices: . |
| `company_id` | Company | string | No | Optional. Trigger only for this company. Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Event ID | string | No |  |
| `event_type` | Event Type | string | No |  |
| `occurred_at` | Occurred At | datetime | No |  |
| `entity_id` | Record ID | string | No |  |
| `entity_type` | Record Type | string | No |  |
| `check_id` | Check ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `company_ids` | Company IDs | string | No |  |
| `changed_fields` | Changed Fields | string | No |  |
| `previous_status` | Previous Status | string | No |  |
| `current_status` | Current Status | string | No |  |
| `run_id` | Run ID | string | No |  |
| `run_group_id` | Run Group ID | string | No |  |
| `verification_type` | Verification Type | string | No |  |
| `verification_label` | Verification Label | string | No |  |
| `run_status` | Run Status | string | No |  |
| `run_outcome` | Run Outcome | string | No |  |
| `graph_node_count` | Profile Graph Nodes | integer | No |  |
| `graph_edge_count` | Profile Graph Edges | integer | No |  |
| `graph_cluster_count` | Profile Graph Clusters | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `record_name` | Record Name | string | No |  |
| `record_first_name` | Record First Name | string | No |  |
| `record_last_name` | Record Last Name | string | No |  |
| `record_email` | Record Email | string | No |  |
| `record_status` | Record Status | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `flow_title` | Flow Title | string | No |  |
| `position_title` | Position Title | string | No |  |
| `data` | Jointl Data | value | No |  |

### Sample output

```json
{
  "changed_fields": [],
  "check_id": "check_id",
  "company_id": "company_id",
  "company_ids": [
    "company_id"
  ],
  "company_name": "Example Company",
  "current_status": null,
  "data": {
    "profile": {
      "_id": "check_id",
      "email": "alex@example.com",
      "fullName": "Alex Example"
    }
  },
  "employee_id": null,
  "entity_id": "check_id",
  "entity_type": "check",
  "event_type": "verification.completed",
  "exit_intelligence_request_id": null,
  "flow_id": "flow_id",
  "flow_title": "Example Hiring Flow",
  "graph_cluster_count": null,
  "graph_edge_count": null,
  "graph_node_count": null,
  "id": "evt_example",
  "jointl_url": "https://join.tl/checks/check_id",
  "occurred_at": "2026-01-01T12:00:00.000Z",
  "position_title": "Software Engineer",
  "previous_status": null,
  "record_email": "alex@example.com",
  "record_first_name": "Alex",
  "record_last_name": "Example",
  "record_name": "Alex Example",
  "record_status": null,
  "reference_id": null,
  "run_group_id": "run_group_id",
  "run_id": "run_id",
  "run_outcome": "clear",
  "run_status": "completed",
  "talent_id": null,
  "verification_label": "Sanctions",
  "verification_type": "sanctions"
}
```

## Verification Check Failed

- Zapier key: `verification_check_failed`
- Kind: trigger

Triggers when one verification check cannot be completed.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `flow_id` | Flow | string | No | Optional. Trigger only for this Flow. Choices: . |
| `company_id` | Company | string | No | Optional. Trigger only for this company. Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Event ID | string | No |  |
| `event_type` | Event Type | string | No |  |
| `occurred_at` | Occurred At | datetime | No |  |
| `entity_id` | Record ID | string | No |  |
| `entity_type` | Record Type | string | No |  |
| `check_id` | Check ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `company_ids` | Company IDs | string | No |  |
| `changed_fields` | Changed Fields | string | No |  |
| `previous_status` | Previous Status | string | No |  |
| `current_status` | Current Status | string | No |  |
| `run_id` | Run ID | string | No |  |
| `run_group_id` | Run Group ID | string | No |  |
| `verification_type` | Verification Type | string | No |  |
| `verification_label` | Verification Label | string | No |  |
| `run_status` | Run Status | string | No |  |
| `run_outcome` | Run Outcome | string | No |  |
| `graph_node_count` | Profile Graph Nodes | integer | No |  |
| `graph_edge_count` | Profile Graph Edges | integer | No |  |
| `graph_cluster_count` | Profile Graph Clusters | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `record_name` | Record Name | string | No |  |
| `record_first_name` | Record First Name | string | No |  |
| `record_last_name` | Record Last Name | string | No |  |
| `record_email` | Record Email | string | No |  |
| `record_status` | Record Status | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `flow_title` | Flow Title | string | No |  |
| `position_title` | Position Title | string | No |  |
| `data` | Jointl Data | value | No |  |

### Sample output

```json
{
  "changed_fields": [],
  "check_id": "check_id",
  "company_id": "company_id",
  "company_ids": [
    "company_id"
  ],
  "company_name": "Example Company",
  "current_status": null,
  "data": {
    "profile": {
      "_id": "check_id",
      "email": "alex@example.com",
      "fullName": "Alex Example"
    }
  },
  "employee_id": null,
  "entity_id": "check_id",
  "entity_type": "check",
  "event_type": "verification.failed",
  "exit_intelligence_request_id": null,
  "flow_id": "flow_id",
  "flow_title": "Example Hiring Flow",
  "graph_cluster_count": null,
  "graph_edge_count": null,
  "graph_node_count": null,
  "id": "evt_example",
  "jointl_url": "https://join.tl/checks/check_id",
  "occurred_at": "2026-01-01T12:00:00.000Z",
  "position_title": "Software Engineer",
  "previous_status": null,
  "record_email": "alex@example.com",
  "record_first_name": "Alex",
  "record_last_name": "Example",
  "record_name": "Alex Example",
  "record_status": null,
  "reference_id": null,
  "run_group_id": "run_group_id",
  "run_id": "run_id",
  "run_outcome": "error",
  "run_status": "failed",
  "talent_id": null,
  "verification_label": "Sanctions",
  "verification_type": "sanctions"
}
```

## Public Profile Discovery Completed

- Zapier key: `public_profile_discovery_completed`
- Kind: trigger

Triggers when a new public-profile discovery run finishes. Use Find Public Profile Results to retrieve authorized matches.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `flow_id` | Flow | string | No | Optional. Trigger only for this Flow. Choices: . |
| `company_id` | Company | string | No | Optional. Trigger only for this company. Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Event ID | string | No |  |
| `event_type` | Event Type | string | No |  |
| `occurred_at` | Occurred At | datetime | No |  |
| `entity_id` | Record ID | string | No |  |
| `entity_type` | Record Type | string | No |  |
| `check_id` | Check ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `company_ids` | Company IDs | string | No |  |
| `changed_fields` | Changed Fields | string | No |  |
| `previous_status` | Previous Status | string | No |  |
| `current_status` | Current Status | string | No |  |
| `run_id` | Run ID | string | No |  |
| `run_group_id` | Run Group ID | string | No |  |
| `verification_type` | Verification Type | string | No |  |
| `verification_label` | Verification Label | string | No |  |
| `run_status` | Run Status | string | No |  |
| `run_outcome` | Run Outcome | string | No |  |
| `graph_node_count` | Profile Graph Nodes | integer | No |  |
| `graph_edge_count` | Profile Graph Edges | integer | No |  |
| `graph_cluster_count` | Profile Graph Clusters | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `record_name` | Record Name | string | No |  |
| `record_first_name` | Record First Name | string | No |  |
| `record_last_name` | Record Last Name | string | No |  |
| `record_email` | Record Email | string | No |  |
| `record_status` | Record Status | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `flow_title` | Flow Title | string | No |  |
| `position_title` | Position Title | string | No |  |
| `data` | Jointl Data | value | No |  |

### Sample output

```json
{
  "changed_fields": [],
  "check_id": "check_id",
  "company_id": "company_id",
  "company_ids": [
    "company_id"
  ],
  "company_name": "Example Company",
  "current_status": null,
  "data": {
    "profile": {
      "_id": "check_id",
      "email": "alex@example.com",
      "fullName": "Alex Example"
    }
  },
  "employee_id": null,
  "entity_id": "check_id",
  "entity_type": "check",
  "event_type": "public_profiles.completed",
  "exit_intelligence_request_id": null,
  "flow_id": "flow_id",
  "flow_title": "Example Hiring Flow",
  "graph_cluster_count": 3,
  "graph_edge_count": 18,
  "graph_node_count": 12,
  "id": "evt_example",
  "jointl_url": "https://join.tl/checks/check_id",
  "occurred_at": "2026-01-01T12:00:00.000Z",
  "position_title": "Software Engineer",
  "previous_status": null,
  "record_email": "alex@example.com",
  "record_first_name": "Alex",
  "record_last_name": "Example",
  "record_name": "Alex Example",
  "record_status": null,
  "reference_id": null,
  "run_group_id": null,
  "run_id": "run_id",
  "run_outcome": "profilesFound",
  "run_status": "completed",
  "talent_id": null,
  "verification_label": null,
  "verification_type": null
}
```

## Public Profile Discovery Failed

- Zapier key: `public_profile_discovery_failed`
- Kind: trigger

Triggers when a public-profile discovery run cannot be completed.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `flow_id` | Flow | string | No | Optional. Trigger only for this Flow. Choices: . |
| `company_id` | Company | string | No | Optional. Trigger only for this company. Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Event ID | string | No |  |
| `event_type` | Event Type | string | No |  |
| `occurred_at` | Occurred At | datetime | No |  |
| `entity_id` | Record ID | string | No |  |
| `entity_type` | Record Type | string | No |  |
| `check_id` | Check ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `company_ids` | Company IDs | string | No |  |
| `changed_fields` | Changed Fields | string | No |  |
| `previous_status` | Previous Status | string | No |  |
| `current_status` | Current Status | string | No |  |
| `run_id` | Run ID | string | No |  |
| `run_group_id` | Run Group ID | string | No |  |
| `verification_type` | Verification Type | string | No |  |
| `verification_label` | Verification Label | string | No |  |
| `run_status` | Run Status | string | No |  |
| `run_outcome` | Run Outcome | string | No |  |
| `graph_node_count` | Profile Graph Nodes | integer | No |  |
| `graph_edge_count` | Profile Graph Edges | integer | No |  |
| `graph_cluster_count` | Profile Graph Clusters | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `record_name` | Record Name | string | No |  |
| `record_first_name` | Record First Name | string | No |  |
| `record_last_name` | Record Last Name | string | No |  |
| `record_email` | Record Email | string | No |  |
| `record_status` | Record Status | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `flow_title` | Flow Title | string | No |  |
| `position_title` | Position Title | string | No |  |
| `data` | Jointl Data | value | No |  |

### Sample output

```json
{
  "changed_fields": [],
  "check_id": "check_id",
  "company_id": "company_id",
  "company_ids": [
    "company_id"
  ],
  "company_name": "Example Company",
  "current_status": null,
  "data": {
    "profile": {
      "_id": "check_id",
      "email": "alex@example.com",
      "fullName": "Alex Example"
    }
  },
  "employee_id": null,
  "entity_id": "check_id",
  "entity_type": "check",
  "event_type": "public_profiles.failed",
  "exit_intelligence_request_id": null,
  "flow_id": "flow_id",
  "flow_title": "Example Hiring Flow",
  "graph_cluster_count": 3,
  "graph_edge_count": 18,
  "graph_node_count": 12,
  "id": "evt_example",
  "jointl_url": "https://join.tl/checks/check_id",
  "occurred_at": "2026-01-01T12:00:00.000Z",
  "position_title": "Software Engineer",
  "previous_status": null,
  "record_email": "alex@example.com",
  "record_first_name": "Alex",
  "record_last_name": "Example",
  "record_name": "Alex Example",
  "record_status": null,
  "reference_id": null,
  "run_group_id": null,
  "run_id": "run_id",
  "run_outcome": "error",
  "run_status": "failed",
  "talent_id": null,
  "verification_label": null,
  "verification_type": null
}
```

## Reference Completed

- Zapier key: `reference_completed`
- Kind: trigger

Triggers when a referee submits a reference response.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `flow_id` | Flow | string | No | Optional. Trigger only for this Flow. Choices: . |
| `company_id` | Company | string | No | Optional. Trigger only for this company. Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Event ID | string | No |  |
| `event_type` | Event Type | string | No |  |
| `occurred_at` | Occurred At | datetime | No |  |
| `entity_id` | Record ID | string | No |  |
| `entity_type` | Record Type | string | No |  |
| `check_id` | Check ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `company_ids` | Company IDs | string | No |  |
| `changed_fields` | Changed Fields | string | No |  |
| `previous_status` | Previous Status | string | No |  |
| `current_status` | Current Status | string | No |  |
| `run_id` | Run ID | string | No |  |
| `run_group_id` | Run Group ID | string | No |  |
| `verification_type` | Verification Type | string | No |  |
| `verification_label` | Verification Label | string | No |  |
| `run_status` | Run Status | string | No |  |
| `run_outcome` | Run Outcome | string | No |  |
| `graph_node_count` | Profile Graph Nodes | integer | No |  |
| `graph_edge_count` | Profile Graph Edges | integer | No |  |
| `graph_cluster_count` | Profile Graph Clusters | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `record_name` | Record Name | string | No |  |
| `record_first_name` | Record First Name | string | No |  |
| `record_last_name` | Record Last Name | string | No |  |
| `record_email` | Record Email | string | No |  |
| `record_status` | Record Status | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `flow_title` | Flow Title | string | No |  |
| `position_title` | Position Title | string | No |  |
| `data` | Jointl Data | value | No |  |

### Sample output

```json
{
  "changed_fields": [],
  "check_id": "check_id",
  "company_id": "company_id",
  "company_ids": [
    "company_id"
  ],
  "company_name": "Example Company",
  "current_status": null,
  "data": {
    "detailedResponseIncluded": false,
    "flow": {
      "companyId": "company_id",
      "id": "flow_id",
      "title": "Example Hiring Flow"
    },
    "response": {
      "applicantId": "check_id",
      "completedAt": "2026-01-01T12:00:00.000Z",
      "id": "reference_id",
      "referee": {
        "email": "morgan@example.com",
        "name": "Morgan Example"
      }
    }
  },
  "employee_id": null,
  "entity_id": "reference_id",
  "entity_type": "reference",
  "event_type": "reference.completed",
  "exit_intelligence_request_id": null,
  "flow_id": "flow_id",
  "flow_title": "Example Hiring Flow",
  "graph_cluster_count": null,
  "graph_edge_count": null,
  "graph_node_count": null,
  "id": "evt_example",
  "jointl_url": "https://join.tl/checks/check_id",
  "occurred_at": "2026-01-01T12:00:00.000Z",
  "position_title": null,
  "previous_status": null,
  "record_email": "morgan@example.com",
  "record_first_name": "Morgan",
  "record_last_name": "Example",
  "record_name": "Morgan Example",
  "record_status": null,
  "reference_id": "reference_id",
  "run_group_id": null,
  "run_id": null,
  "run_outcome": null,
  "run_status": null,
  "talent_id": null,
  "verification_label": null,
  "verification_type": null
}
```

## New Employee

- Zapier key: `new_employee`
- Kind: trigger

Triggers when a new Employee is created.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `company_id` | Company | string | No | Optional. Trigger only for this company. Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Event ID | string | No |  |
| `event_type` | Event Type | string | No |  |
| `occurred_at` | Occurred At | datetime | No |  |
| `entity_id` | Record ID | string | No |  |
| `entity_type` | Record Type | string | No |  |
| `check_id` | Check ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `company_ids` | Company IDs | string | No |  |
| `changed_fields` | Changed Fields | string | No |  |
| `previous_status` | Previous Status | string | No |  |
| `current_status` | Current Status | string | No |  |
| `run_id` | Run ID | string | No |  |
| `run_group_id` | Run Group ID | string | No |  |
| `verification_type` | Verification Type | string | No |  |
| `verification_label` | Verification Label | string | No |  |
| `run_status` | Run Status | string | No |  |
| `run_outcome` | Run Outcome | string | No |  |
| `graph_node_count` | Profile Graph Nodes | integer | No |  |
| `graph_edge_count` | Profile Graph Edges | integer | No |  |
| `graph_cluster_count` | Profile Graph Clusters | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `record_name` | Record Name | string | No |  |
| `record_first_name` | Record First Name | string | No |  |
| `record_last_name` | Record Last Name | string | No |  |
| `record_email` | Record Email | string | No |  |
| `record_status` | Record Status | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `flow_title` | Flow Title | string | No |  |
| `position_title` | Position Title | string | No |  |
| `data` | Jointl Data | value | No |  |

### Sample output

```json
{
  "changed_fields": [],
  "check_id": null,
  "company_id": "company_id",
  "company_ids": [
    "company_id"
  ],
  "company_name": "Example Company",
  "current_status": null,
  "data": {
    "profile": {
      "_id": "employee_id",
      "email": "alex@example.com",
      "fullName": "Alex Example"
    }
  },
  "employee_id": "employee_id",
  "entity_id": "employee_id",
  "entity_type": "employee",
  "event_type": "employee.created",
  "exit_intelligence_request_id": null,
  "flow_id": null,
  "flow_title": null,
  "graph_cluster_count": null,
  "graph_edge_count": null,
  "graph_node_count": null,
  "id": "evt_example",
  "jointl_url": "https://join.tl/employees/employee_id",
  "occurred_at": "2026-01-01T12:00:00.000Z",
  "position_title": "Software Engineer",
  "previous_status": null,
  "record_email": "alex@example.com",
  "record_first_name": "Alex",
  "record_last_name": "Example",
  "record_name": "Alex Example",
  "record_status": null,
  "reference_id": null,
  "run_group_id": null,
  "run_id": null,
  "run_outcome": null,
  "run_status": null,
  "talent_id": null,
  "verification_label": null,
  "verification_type": null
}
```

## Employee Work Details Changed

- Zapier key: `employee_work_details_changed`
- Kind: trigger

Triggers when the selected Employee profile or work-detail field changes.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `company_id` | Company | string | No | Optional. Trigger only for this company. Choices: . |
| `changed_field` | Changed Field | string | Yes | Choose the exact category of employee change that should trigger this Zap. Choices: company, compensation, email, end_date, full_name, manager, position_title, start_date, tags, work_record. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Event ID | string | No |  |
| `event_type` | Event Type | string | No |  |
| `occurred_at` | Occurred At | datetime | No |  |
| `entity_id` | Record ID | string | No |  |
| `entity_type` | Record Type | string | No |  |
| `check_id` | Check ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `company_ids` | Company IDs | string | No |  |
| `changed_fields` | Changed Fields | string | No |  |
| `previous_status` | Previous Status | string | No |  |
| `current_status` | Current Status | string | No |  |
| `run_id` | Run ID | string | No |  |
| `run_group_id` | Run Group ID | string | No |  |
| `verification_type` | Verification Type | string | No |  |
| `verification_label` | Verification Label | string | No |  |
| `run_status` | Run Status | string | No |  |
| `run_outcome` | Run Outcome | string | No |  |
| `graph_node_count` | Profile Graph Nodes | integer | No |  |
| `graph_edge_count` | Profile Graph Edges | integer | No |  |
| `graph_cluster_count` | Profile Graph Clusters | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `record_name` | Record Name | string | No |  |
| `record_first_name` | Record First Name | string | No |  |
| `record_last_name` | Record Last Name | string | No |  |
| `record_email` | Record Email | string | No |  |
| `record_status` | Record Status | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `flow_title` | Flow Title | string | No |  |
| `position_title` | Position Title | string | No |  |
| `data` | Jointl Data | value | No |  |

### Sample output

```json
{
  "changed_fields": [
    "position_title"
  ],
  "check_id": null,
  "company_id": "company_id",
  "company_ids": [
    "company_id"
  ],
  "company_name": "Example Company",
  "current_status": null,
  "data": {
    "profile": {
      "_id": "employee_id",
      "email": "alex@example.com",
      "fullName": "Alex Example"
    }
  },
  "employee_id": "employee_id",
  "entity_id": "employee_id",
  "entity_type": "employee",
  "event_type": "employee.updated",
  "exit_intelligence_request_id": null,
  "flow_id": null,
  "flow_title": null,
  "graph_cluster_count": null,
  "graph_edge_count": null,
  "graph_node_count": null,
  "id": "evt_example",
  "jointl_url": "https://join.tl/employees/employee_id",
  "occurred_at": "2026-01-01T12:00:00.000Z",
  "position_title": "Software Engineer",
  "previous_status": null,
  "record_email": "alex@example.com",
  "record_first_name": "Alex",
  "record_last_name": "Example",
  "record_name": "Alex Example",
  "record_status": null,
  "reference_id": null,
  "run_group_id": null,
  "run_id": null,
  "run_outcome": null,
  "run_status": null,
  "talent_id": null,
  "verification_label": null,
  "verification_type": null
}
```

## Employee Status Changed

- Zapier key: `employee_status_changed`
- Kind: trigger

Triggers when an Employee moves to another status.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `company_id` | Company | string | No | Optional. Trigger only for this company. Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Event ID | string | No |  |
| `event_type` | Event Type | string | No |  |
| `occurred_at` | Occurred At | datetime | No |  |
| `entity_id` | Record ID | string | No |  |
| `entity_type` | Record Type | string | No |  |
| `check_id` | Check ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `company_ids` | Company IDs | string | No |  |
| `changed_fields` | Changed Fields | string | No |  |
| `previous_status` | Previous Status | string | No |  |
| `current_status` | Current Status | string | No |  |
| `run_id` | Run ID | string | No |  |
| `run_group_id` | Run Group ID | string | No |  |
| `verification_type` | Verification Type | string | No |  |
| `verification_label` | Verification Label | string | No |  |
| `run_status` | Run Status | string | No |  |
| `run_outcome` | Run Outcome | string | No |  |
| `graph_node_count` | Profile Graph Nodes | integer | No |  |
| `graph_edge_count` | Profile Graph Edges | integer | No |  |
| `graph_cluster_count` | Profile Graph Clusters | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `record_name` | Record Name | string | No |  |
| `record_first_name` | Record First Name | string | No |  |
| `record_last_name` | Record Last Name | string | No |  |
| `record_email` | Record Email | string | No |  |
| `record_status` | Record Status | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `flow_title` | Flow Title | string | No |  |
| `position_title` | Position Title | string | No |  |
| `data` | Jointl Data | value | No |  |

### Sample output

```json
{
  "changed_fields": [
    "status"
  ],
  "check_id": null,
  "company_id": "company_id",
  "company_ids": [
    "company_id"
  ],
  "company_name": "Example Company",
  "current_status": "IN_PROGRESS",
  "data": {
    "profile": {
      "_id": "employee_id",
      "email": "alex@example.com",
      "fullName": "Alex Example"
    }
  },
  "employee_id": "employee_id",
  "entity_id": "employee_id",
  "entity_type": "employee",
  "event_type": "employee.status_changed",
  "exit_intelligence_request_id": null,
  "flow_id": null,
  "flow_title": null,
  "graph_cluster_count": null,
  "graph_edge_count": null,
  "graph_node_count": null,
  "id": "evt_example",
  "jointl_url": "https://join.tl/employees/employee_id",
  "occurred_at": "2026-01-01T12:00:00.000Z",
  "position_title": "Software Engineer",
  "previous_status": "NEW",
  "record_email": "alex@example.com",
  "record_first_name": "Alex",
  "record_last_name": "Example",
  "record_name": "Alex Example",
  "record_status": "IN_PROGRESS",
  "reference_id": null,
  "run_group_id": null,
  "run_id": null,
  "run_outcome": null,
  "run_status": null,
  "talent_id": null,
  "verification_label": null,
  "verification_type": null
}
```

## Exit Intelligence Request Created

- Zapier key: `exit_intelligence_request_created`
- Kind: trigger

Triggers when an Exit Intelligence request is created and its invitation is queued.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `flow_id` | Flow | string | No | Optional. Trigger only for this Flow. Choices: . |
| `company_id` | Company | string | No | Optional. Trigger only for this company. Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Event ID | string | No |  |
| `event_type` | Event Type | string | No |  |
| `occurred_at` | Occurred At | datetime | No |  |
| `entity_id` | Record ID | string | No |  |
| `entity_type` | Record Type | string | No |  |
| `check_id` | Check ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `company_ids` | Company IDs | string | No |  |
| `changed_fields` | Changed Fields | string | No |  |
| `previous_status` | Previous Status | string | No |  |
| `current_status` | Current Status | string | No |  |
| `run_id` | Run ID | string | No |  |
| `run_group_id` | Run Group ID | string | No |  |
| `verification_type` | Verification Type | string | No |  |
| `verification_label` | Verification Label | string | No |  |
| `run_status` | Run Status | string | No |  |
| `run_outcome` | Run Outcome | string | No |  |
| `graph_node_count` | Profile Graph Nodes | integer | No |  |
| `graph_edge_count` | Profile Graph Edges | integer | No |  |
| `graph_cluster_count` | Profile Graph Clusters | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `record_name` | Record Name | string | No |  |
| `record_first_name` | Record First Name | string | No |  |
| `record_last_name` | Record Last Name | string | No |  |
| `record_email` | Record Email | string | No |  |
| `record_status` | Record Status | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `flow_title` | Flow Title | string | No |  |
| `position_title` | Position Title | string | No |  |
| `data` | Jointl Data | value | No |  |

### Sample output

```json
{
  "changed_fields": [],
  "check_id": null,
  "company_id": "company_id",
  "company_ids": [
    "company_id"
  ],
  "company_name": "Example Company",
  "current_status": null,
  "data": {
    "profile": {
      "_id": "employee_id",
      "email": "alex@example.com",
      "fullName": "Alex Example"
    }
  },
  "employee_id": "employee_id",
  "entity_id": "employee_id",
  "entity_type": "employee",
  "event_type": "exit_intelligence.requested",
  "exit_intelligence_request_id": "exit_intelligence_request_id",
  "flow_id": "flow_id",
  "flow_title": "Example Hiring Flow",
  "graph_cluster_count": null,
  "graph_edge_count": null,
  "graph_node_count": null,
  "id": "evt_example",
  "jointl_url": "https://join.tl/employees/employee_id",
  "occurred_at": "2026-01-01T12:00:00.000Z",
  "position_title": "Software Engineer",
  "previous_status": null,
  "record_email": "alex@example.com",
  "record_first_name": "Alex",
  "record_last_name": "Example",
  "record_name": "Alex Example",
  "record_status": null,
  "reference_id": null,
  "run_group_id": null,
  "run_id": null,
  "run_outcome": null,
  "run_status": null,
  "talent_id": null,
  "verification_label": null,
  "verification_type": null
}
```

## Exit Intelligence Completed

- Zapier key: `exit_intelligence_completed`
- Kind: trigger

Triggers when an Employee completes an Exit Intelligence request. Use Find Exit Intelligence Result to retrieve authorized answers.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `flow_id` | Flow | string | No | Optional. Trigger only for this Flow. Choices: . |
| `company_id` | Company | string | No | Optional. Trigger only for this company. Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Event ID | string | No |  |
| `event_type` | Event Type | string | No |  |
| `occurred_at` | Occurred At | datetime | No |  |
| `entity_id` | Record ID | string | No |  |
| `entity_type` | Record Type | string | No |  |
| `check_id` | Check ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `company_ids` | Company IDs | string | No |  |
| `changed_fields` | Changed Fields | string | No |  |
| `previous_status` | Previous Status | string | No |  |
| `current_status` | Current Status | string | No |  |
| `run_id` | Run ID | string | No |  |
| `run_group_id` | Run Group ID | string | No |  |
| `verification_type` | Verification Type | string | No |  |
| `verification_label` | Verification Label | string | No |  |
| `run_status` | Run Status | string | No |  |
| `run_outcome` | Run Outcome | string | No |  |
| `graph_node_count` | Profile Graph Nodes | integer | No |  |
| `graph_edge_count` | Profile Graph Edges | integer | No |  |
| `graph_cluster_count` | Profile Graph Clusters | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `record_name` | Record Name | string | No |  |
| `record_first_name` | Record First Name | string | No |  |
| `record_last_name` | Record Last Name | string | No |  |
| `record_email` | Record Email | string | No |  |
| `record_status` | Record Status | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `flow_title` | Flow Title | string | No |  |
| `position_title` | Position Title | string | No |  |
| `data` | Jointl Data | value | No |  |

### Sample output

```json
{
  "changed_fields": [],
  "check_id": null,
  "company_id": "company_id",
  "company_ids": [
    "company_id"
  ],
  "company_name": "Example Company",
  "current_status": null,
  "data": {
    "profile": {
      "_id": "employee_id",
      "email": "alex@example.com",
      "fullName": "Alex Example"
    }
  },
  "employee_id": "employee_id",
  "entity_id": "employee_id",
  "entity_type": "employee",
  "event_type": "exit_intelligence.completed",
  "exit_intelligence_request_id": "exit_intelligence_request_id",
  "flow_id": "flow_id",
  "flow_title": "Example Hiring Flow",
  "graph_cluster_count": null,
  "graph_edge_count": null,
  "graph_node_count": null,
  "id": "evt_example",
  "jointl_url": "https://join.tl/employees/employee_id",
  "occurred_at": "2026-01-01T12:00:00.000Z",
  "position_title": "Software Engineer",
  "previous_status": null,
  "record_email": "alex@example.com",
  "record_first_name": "Alex",
  "record_last_name": "Example",
  "record_name": "Alex Example",
  "record_status": null,
  "reference_id": null,
  "run_group_id": null,
  "run_id": null,
  "run_outcome": null,
  "run_status": null,
  "talent_id": null,
  "verification_label": null,
  "verification_type": null
}
```

## New Talent

- Zapier key: `new_talent`
- Kind: trigger

Triggers when a new profile enters the Talent Pool.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `company_id` | Company | string | No | Optional. Trigger only for this company. Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Event ID | string | No |  |
| `event_type` | Event Type | string | No |  |
| `occurred_at` | Occurred At | datetime | No |  |
| `entity_id` | Record ID | string | No |  |
| `entity_type` | Record Type | string | No |  |
| `check_id` | Check ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `company_ids` | Company IDs | string | No |  |
| `changed_fields` | Changed Fields | string | No |  |
| `previous_status` | Previous Status | string | No |  |
| `current_status` | Current Status | string | No |  |
| `run_id` | Run ID | string | No |  |
| `run_group_id` | Run Group ID | string | No |  |
| `verification_type` | Verification Type | string | No |  |
| `verification_label` | Verification Label | string | No |  |
| `run_status` | Run Status | string | No |  |
| `run_outcome` | Run Outcome | string | No |  |
| `graph_node_count` | Profile Graph Nodes | integer | No |  |
| `graph_edge_count` | Profile Graph Edges | integer | No |  |
| `graph_cluster_count` | Profile Graph Clusters | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `record_name` | Record Name | string | No |  |
| `record_first_name` | Record First Name | string | No |  |
| `record_last_name` | Record Last Name | string | No |  |
| `record_email` | Record Email | string | No |  |
| `record_status` | Record Status | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `flow_title` | Flow Title | string | No |  |
| `position_title` | Position Title | string | No |  |
| `data` | Jointl Data | value | No |  |

### Sample output

```json
{
  "changed_fields": [],
  "check_id": null,
  "company_id": "company_id",
  "company_ids": [
    "company_id"
  ],
  "company_name": "Example Company",
  "current_status": null,
  "data": {
    "profile": {
      "_id": "talent_id",
      "email": "alex@example.com",
      "fullName": "Alex Example"
    }
  },
  "employee_id": null,
  "entity_id": "talent_id",
  "entity_type": "talent",
  "event_type": "talent.created",
  "exit_intelligence_request_id": null,
  "flow_id": null,
  "flow_title": null,
  "graph_cluster_count": null,
  "graph_edge_count": null,
  "graph_node_count": null,
  "id": "evt_example",
  "jointl_url": "https://join.tl/talents/talent_id",
  "occurred_at": "2026-01-01T12:00:00.000Z",
  "position_title": "Software Engineer",
  "previous_status": null,
  "record_email": "alex@example.com",
  "record_first_name": "Alex",
  "record_last_name": "Example",
  "record_name": "Alex Example",
  "record_status": null,
  "reference_id": null,
  "run_group_id": null,
  "run_id": null,
  "run_outcome": null,
  "run_status": null,
  "talent_id": "talent_id",
  "verification_label": null,
  "verification_type": null
}
```

## Talent Profile Submitted From Reference

- Zapier key: `talent_profile_submitted`
- Kind: trigger

Triggers when a referee submits updated Talent Pool profile details.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `company_id` | Company | string | No | Optional. Trigger only for this company. Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Event ID | string | No |  |
| `event_type` | Event Type | string | No |  |
| `occurred_at` | Occurred At | datetime | No |  |
| `entity_id` | Record ID | string | No |  |
| `entity_type` | Record Type | string | No |  |
| `check_id` | Check ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `company_ids` | Company IDs | string | No |  |
| `changed_fields` | Changed Fields | string | No |  |
| `previous_status` | Previous Status | string | No |  |
| `current_status` | Current Status | string | No |  |
| `run_id` | Run ID | string | No |  |
| `run_group_id` | Run Group ID | string | No |  |
| `verification_type` | Verification Type | string | No |  |
| `verification_label` | Verification Label | string | No |  |
| `run_status` | Run Status | string | No |  |
| `run_outcome` | Run Outcome | string | No |  |
| `graph_node_count` | Profile Graph Nodes | integer | No |  |
| `graph_edge_count` | Profile Graph Edges | integer | No |  |
| `graph_cluster_count` | Profile Graph Clusters | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `record_name` | Record Name | string | No |  |
| `record_first_name` | Record First Name | string | No |  |
| `record_last_name` | Record Last Name | string | No |  |
| `record_email` | Record Email | string | No |  |
| `record_status` | Record Status | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `flow_title` | Flow Title | string | No |  |
| `position_title` | Position Title | string | No |  |
| `data` | Jointl Data | value | No |  |

### Sample output

```json
{
  "changed_fields": [
    "profile"
  ],
  "check_id": null,
  "company_id": "company_id",
  "company_ids": [
    "company_id"
  ],
  "company_name": "Example Company",
  "current_status": null,
  "data": {
    "profile": {
      "_id": "talent_id",
      "email": "alex@example.com",
      "fullName": "Alex Example"
    }
  },
  "employee_id": null,
  "entity_id": "talent_id",
  "entity_type": "talent",
  "event_type": "talent.updated",
  "exit_intelligence_request_id": null,
  "flow_id": null,
  "flow_title": null,
  "graph_cluster_count": null,
  "graph_edge_count": null,
  "graph_node_count": null,
  "id": "evt_example",
  "jointl_url": "https://join.tl/talents/talent_id",
  "occurred_at": "2026-01-01T12:00:00.000Z",
  "position_title": "Software Engineer",
  "previous_status": null,
  "record_email": "alex@example.com",
  "record_first_name": "Alex",
  "record_last_name": "Example",
  "record_name": "Alex Example",
  "record_status": null,
  "reference_id": null,
  "run_group_id": null,
  "run_id": null,
  "run_outcome": null,
  "run_status": null,
  "talent_id": "talent_id",
  "verification_label": null,
  "verification_type": null
}
```

## Talent Pool Status Changed

- Zapier key: `talent_status_changed`
- Kind: trigger

Triggers when a Talent Pool profile moves to another status.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `company_id` | Company | string | No | Optional. Trigger only for this company. Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Event ID | string | No |  |
| `event_type` | Event Type | string | No |  |
| `occurred_at` | Occurred At | datetime | No |  |
| `entity_id` | Record ID | string | No |  |
| `entity_type` | Record Type | string | No |  |
| `check_id` | Check ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `company_ids` | Company IDs | string | No |  |
| `changed_fields` | Changed Fields | string | No |  |
| `previous_status` | Previous Status | string | No |  |
| `current_status` | Current Status | string | No |  |
| `run_id` | Run ID | string | No |  |
| `run_group_id` | Run Group ID | string | No |  |
| `verification_type` | Verification Type | string | No |  |
| `verification_label` | Verification Label | string | No |  |
| `run_status` | Run Status | string | No |  |
| `run_outcome` | Run Outcome | string | No |  |
| `graph_node_count` | Profile Graph Nodes | integer | No |  |
| `graph_edge_count` | Profile Graph Edges | integer | No |  |
| `graph_cluster_count` | Profile Graph Clusters | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `record_name` | Record Name | string | No |  |
| `record_first_name` | Record First Name | string | No |  |
| `record_last_name` | Record Last Name | string | No |  |
| `record_email` | Record Email | string | No |  |
| `record_status` | Record Status | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `flow_title` | Flow Title | string | No |  |
| `position_title` | Position Title | string | No |  |
| `data` | Jointl Data | value | No |  |

### Sample output

```json
{
  "changed_fields": [
    "status"
  ],
  "check_id": null,
  "company_id": "company_id",
  "company_ids": [
    "company_id"
  ],
  "company_name": "Example Company",
  "current_status": "IN_PROGRESS",
  "data": {
    "profile": {
      "_id": "talent_id",
      "email": "alex@example.com",
      "fullName": "Alex Example"
    }
  },
  "employee_id": null,
  "entity_id": "talent_id",
  "entity_type": "talent",
  "event_type": "talent.status_changed",
  "exit_intelligence_request_id": null,
  "flow_id": null,
  "flow_title": null,
  "graph_cluster_count": null,
  "graph_edge_count": null,
  "graph_node_count": null,
  "id": "evt_example",
  "jointl_url": "https://join.tl/talents/talent_id",
  "occurred_at": "2026-01-01T12:00:00.000Z",
  "position_title": "Software Engineer",
  "previous_status": "NEW",
  "record_email": "alex@example.com",
  "record_first_name": "Alex",
  "record_last_name": "Example",
  "record_name": "Alex Example",
  "record_status": "IN_PROGRESS",
  "reference_id": null,
  "run_group_id": null,
  "run_id": null,
  "run_outcome": null,
  "run_status": null,
  "talent_id": "talent_id",
  "verification_label": null,
  "verification_type": null
}
```

## Find Person

- Zapier key: `find_person`
- Kind: search
- Jointl operation: `workspace.search`

Finds up to 30 authorized people across Checks, Employees, Talent Pool profiles, References, and Team Members.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `query` | Search Text | string | Yes | Enter a name, email, company, job title, tag, attribute, or other identifying text. |
| `person_source` | Person Source | string | No | Optionally search only one Jointl record type. Reference people require reference-response access, and Team Members follow Jointl’s owner-only global-search visibility. Default: "all". Choices: all, applicant, employee, member, reference, talent. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Person Search ID | string | No |  |
| `full_name` | Full Name | string | No |  |
| `job_title` | Job Title | string | No |  |
| `company_name` | Company Name | string | No |  |
| `primary_source_type` | Primary Source Type | string | No |  |
| `source_types` | Source Types | string | No |  |
| `status_labels` | Status Labels | string | No |  |
| `check_id` | Check ID (When Unique) | string | No |  |
| `check_status` | Check Status (When Unique) | string | No |  |
| `employee_id` | Employee ID (When Unique) | string | No |  |
| `employee_status` | Employee Status (When Unique) | string | No |  |
| `talent_id` | Talent ID (When Unique) | string | No |  |
| `talent_status` | Talent Status (When Unique) | string | No |  |
| `reference_id` | Reference ID (When Unique) | string | No |  |
| `reference_parent_check_id` | Reference Parent Check ID (When Unique) | string | No |  |
| `team_member_id` | Team Member ID (When Unique) | string | No |  |
| `check_ids` | Check IDs | string | No |  |
| `employee_ids` | Employee IDs | string | No |  |
| `talent_ids` | Talent IDs | string | No |  |
| `reference_ids` | Reference IDs | string | No |  |
| `team_member_ids` | Team Member IDs | string | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `source_records` | Source Records | line items | No |  |
| `↳ source_type` | Source Type | string | No |  |
| `↳ source_entity_type` | Source Entity Type | string | No |  |
| `↳ record_id` | Record ID | string | No |  |
| `↳ parent_check_id` | Parent Check ID | string | No |  |
| `↳ source_label` | Source Label | string | No |  |
| `↳ context` | Context | string | No |  |
| `↳ company_name` | Company Name | string | No |  |
| `↳ status` | Status | string | No |  |
| `↳ status_label` | Status Label | string | No |  |
| `↳ jointl_url` | Jointl URL | string | No |  |

### Sample output

```json
{
  "check_id": "check_id",
  "check_ids": [
    "check_id"
  ],
  "check_status": "inProgress",
  "company_name": "Example Co",
  "employee_id": "employee_id",
  "employee_ids": [
    "employee_id"
  ],
  "employee_status": "active",
  "full_name": "Alex Example",
  "id": "person:email:alex@example.com",
  "job_title": "Engineering Manager",
  "jointl_url": "https://join.tl/employees/employee_id/overview",
  "primary_source_type": "employee",
  "reference_id": "reference_id",
  "reference_ids": [
    "reference_id"
  ],
  "reference_parent_check_id": "parent_check_id",
  "source_records": [
    {
      "company_name": "Example Co",
      "context": "Engineering Manager",
      "jointl_url": "https://join.tl/employees/employee_id/overview",
      "parent_check_id": null,
      "record_id": "employee_id",
      "source_entity_type": "employee",
      "source_label": "Employee",
      "source_type": "employee",
      "status": "active",
      "status_label": "Active"
    },
    {
      "company_name": "Example Co",
      "context": "Engineering Manager",
      "jointl_url": "https://join.tl/checks/check_id/overview",
      "parent_check_id": null,
      "record_id": "check_id",
      "source_entity_type": "applicant",
      "source_label": "Applicant",
      "source_type": "check",
      "status": "inProgress",
      "status_label": "In Progress"
    },
    {
      "company_name": null,
      "context": "Candidate Example",
      "jointl_url": "https://join.tl/checks/parent_check_id/references/reference_id",
      "parent_check_id": "parent_check_id",
      "record_id": "reference_id",
      "source_entity_type": "reference",
      "source_label": "Reference",
      "source_type": "reference",
      "status": null,
      "status_label": null
    }
  ],
  "source_types": [
    "employee",
    "check",
    "reference"
  ],
  "status_labels": [
    "Active",
    "In Progress"
  ],
  "talent_id": null,
  "talent_ids": [],
  "talent_status": null,
  "team_member_id": null,
  "team_member_ids": []
}
```

## Find Check Report

- Zapier key: `find_check_report`
- Kind: search
- Jointl operation: `checks.report`

Finds the full authorized factual report for one Check.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `applicant_id` | Check | string | Yes | Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Check ID | string | No |  |
| `data` | Check Report | value | No |  |

### Sample output

```json
{
  "data": {},
  "id": "check_id"
}
```

## Find Reference Response

- Zapier key: `find_reference_response`
- Kind: search
- Jointl operation: `references.get`

Finds one complete authorized reference response.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `applicant_id` | Check | string | No | Optional when you map a Reference ID from an earlier Zap step. Choices: . |
| `reference_id` | Reference | string | Yes | Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Reference ID | string | No |  |
| `data` | Reference Response | value | No |  |

### Sample output

```json
{
  "data": {},
  "id": "reference_id"
}
```

## Find References for Check

- Zapier key: `find_references_for_check`
- Kind: search
- Jointl operation: `references.list`

Finds every authorized reference request and completed response for one Check as separate Zapier search results.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `check_id` | Check | string | Yes | Zapier uses the first result by default. Choose the option to return all search results as line items when a later step needs every reference. Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `reference_id` | Reference ID | string | No |  |
| `check_id` | Check ID | string | No |  |
| `status` | Reference Status | string | No |  |
| `referee_name` | Referee Name | string | No |  |
| `referee_email` | Referee Email | string | No |  |
| `referee_job_title` | Referee Job Title | string | No |  |
| `referee_company_name` | Referee Company | string | No |  |
| `reference_type` | Reference Type | string | No |  |
| `created_at` | Created At | datetime | No |  |
| `sent_at` | Sent At | datetime | No |  |
| `completed_at` | Completed At | datetime | No |  |
| `jointl_url` | Jointl URL | string | No |  |

### Sample output

```json
{
  "check_id": "check_id",
  "completed_at": "2026-09-01T12:00:00.000Z",
  "created_at": "2026-08-30T09:00:00.000Z",
  "id": "reference_id",
  "jointl_url": "https://join.tl/checks/check_id/references/reference_id",
  "referee_company_name": "Example Co",
  "referee_email": "morgan@example.com",
  "referee_job_title": "Engineering Manager",
  "referee_name": "Morgan Example",
  "reference_id": "reference_id",
  "reference_type": "Manager",
  "sent_at": "2026-08-30T09:01:00.000Z",
  "status": "completed"
}
```

## Find Verification Results

- Zapier key: `find_verification_results`
- Kind: search
- Jointl operation: `checks.verifications.get`

Finds the available verification types and latest authorized results for one Check.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `applicant_id` | Check | string | Yes | Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Check ID | string | No |  |
| `data` | Verification Results | value | No |  |

### Sample output

```json
{
  "data": {},
  "id": "check_id"
}
```

## Find Public Profile Results

- Zapier key: `find_public_profile_results`
- Kind: search
- Jointl operation: `checks.publicProfiles.get`

Finds the latest authorized public-profile discovery results for one Check.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `applicant_id` | Check | string | Yes | Choices: . |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Check ID | string | No |  |
| `data` | Public Profile Results | value | No |  |

### Sample output

```json
{
  "data": {},
  "id": "check_id"
}
```

## Find Exit Intelligence Result

- Zapier key: `find_exit_intelligence_result`
- Kind: search
- Jointl operation: `employees.exitIntelligence.get`

Finds the latest or one exact authorized Exit Intelligence result for an Employee.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `employee_id` | Employee | string | Yes | Choices: . |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No | Map this from an Exit Intelligence trigger to retrieve that exact request. Leave blank to retrieve the latest visible request. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Exit Intelligence Request ID | string | No |  |
| `employee` | Employee | value | No |  |
| `request` | Exit Intelligence Result | value | No |  |

### Sample output

```json
{
  "employee": {
    "_id": "employee_id",
    "fullName": "Alex Example",
    "status": "left"
  },
  "id": "exit_intelligence_request_id",
  "request": {
    "_id": "exit_intelligence_request_id",
    "completedAt": "2026-01-01T12:00:00.000Z",
    "flow": {
      "_id": "flow_id",
      "title": "Exit Intelligence"
    },
    "metrics": {},
    "questions": []
  }
}
```

## Create Check & Send Flow Invitation

- Zapier key: `create_check_send_invitation`
- Kind: action
- Jointl operation: `checks.bulkCreate`

Creates one Check and sends the invitation configured by the selected Flow.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `flow_id` | Flow | string | Yes | Choices: . |
| `full_name` | Candidate Full Name | string | Yes |  |
| `email` | Candidate Email | string | Yes |  |
| `source_key` | Unique Source Key | string | Yes | Map a stable unique key from the event, submission, row change, or execution that started this Zap. Jointl uses it to prevent duplicate writes across retries. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Check ID | string | No |  |
| `check_id` | Check ID | string | No |  |
| `candidate_name` | Candidate Full Name | string | No |  |
| `candidate_email` | Candidate Email | string | No |  |
| `flow_id` | Flow ID | string | No |  |
| `invitation_status` | Invitation Status | string | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `created_count` | Created Check Count | integer | No |  |
| `error_count` | Error Count | integer | No |  |
| `execution_id` | Jointl Execution ID | string | No |  |
| `replayed` | Replayed Existing Result | boolean | No |  |

### Sample output

```json
{
  "candidate_email": "alex@example.com",
  "candidate_name": "Alex Example",
  "check_id": "check_id",
  "created_count": 1,
  "error_count": 0,
  "execution_id": "execution_id",
  "flow_id": "flow_id",
  "id": "check_id",
  "invitation_status": "queued",
  "jointl_url": "https://join.tl/checks/check_id/overview",
  "replayed": false
}
```

## Create Checks in Bulk & Send Flow Invitations

- Zapier key: `bulk_create_checks`
- Kind: action
- Jointl operation: `checks.bulkCreate`

Creates up to 250 Checks in one retry-safe import and sends the invitations configured by the selected Flow.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `flow_id` | Flow | string | Yes | Choices: . |
| `applicants` | Candidates | line items | Yes |  |
| `↳ full_name` | Candidate Full Name | string | Yes | Map aligned name and email line items from a prior step. One run accepts 1–250 candidates. |
| `↳ email` | Candidate Email | string | Yes |  |
| `source_key` | Unique Source Key | string | Yes | Map a stable unique key from the event, submission, row change, or execution that started this Zap. Jointl uses it to prevent duplicate writes across retries. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Check Import ID | string | No |  |
| `created_count` | Created Check Count | integer | No |  |
| `error_count` | Error Count | integer | No |  |
| `flow_id` | Flow ID | string | No |  |
| `checks` | Checks | line items | No |  |
| `↳ source_row_number` | Source Row Number | integer | No |  |
| `↳ check_id` | Check ID | string | No |  |
| `↳ candidate_name` | Candidate Full Name | string | No |  |
| `↳ candidate_email` | Candidate Email | string | No |  |
| `↳ invitation_status` | Invitation Status | string | No |  |
| `↳ jointl_url` | Jointl URL | string | No |  |
| `execution_id` | Jointl Execution ID | string | No |  |
| `replayed` | Replayed Existing Result | boolean | No |  |

### Sample output

```json
{
  "checks": [
    {
      "candidate_email": "alex@example.com",
      "candidate_name": "Alex Example",
      "check_id": "check_id_1",
      "invitation_status": "queued",
      "jointl_url": "https://join.tl/checks/check_id_1/overview",
      "source_row_number": 1
    },
    {
      "candidate_email": "taylor@example.com",
      "candidate_name": "Taylor Example",
      "check_id": "check_id_2",
      "invitation_status": "queued",
      "jointl_url": "https://join.tl/checks/check_id_2/overview",
      "source_row_number": 2
    }
  ],
  "created_count": 2,
  "error_count": 0,
  "execution_id": "execution_id",
  "flow_id": "flow_id",
  "id": "execution_id",
  "replayed": false
}
```

## Send Reference Request

- Zapier key: `send_reference_request`
- Kind: action
- Jointl operation: `references.request`

Creates and sends one manual reference request for a Check.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `check_id` | Check | string | Yes | Choices: . |
| `template_id` | Reference Template | string | Yes | Choices: . |
| `referee_name` | Referee Full Name | string | Yes |  |
| `referee_email` | Referee Email | string | Yes |  |
| `referee_phone` | Referee Mobile Phone | string | No | Use an international E.164 number, for example +14155552671. |
| `phone_message_consent` | Referee Consented to SMS | boolean | No | Default: "false". |
| `source_key` | Unique Source Key | string | Yes | Map a stable unique key from the event, submission, row change, or execution that started this Zap. Jointl uses it to prevent duplicate writes across retries. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Reference ID | string | No |  |
| `reference_id` | Reference ID | string | No |  |
| `check_id` | Check ID | string | No |  |
| `referee_name` | Referee Full Name | string | No |  |
| `referee_email` | Referee Email | string | No |  |
| `invitation_status` | Invitation Status | string | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `execution_id` | Jointl Execution ID | string | No |  |
| `replayed` | Replayed Existing Result | boolean | No |  |

### Sample output

```json
{
  "check_id": "check_id",
  "execution_id": "execution_id",
  "id": "reference_id",
  "invitation_status": "queued",
  "jointl_url": "https://join.tl/checks/check_id/references/reference_id",
  "referee_email": "morgan@example.com",
  "referee_name": "Morgan Example",
  "reference_id": "reference_id",
  "replayed": false
}
```

## Update Employee

- Zapier key: `update_employee`
- Kind: action
- Jointl operation: `employees.bulkImport`

Updates one exact Employee work record while preserving the Employee’s other work records.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `employee_id` | Employee | string | Yes | Choices: . |
| `position_id` | Work Record | string | Yes | Choose the exact existing work record to update. Other work records are preserved. Choices: . |
| `full_name` | Full Name | string | Yes |  |
| `email` | Work Email | string | No |  |
| `company_id` | Company | string | Yes | Choices: . |
| `position_title` | Position Title | string | Yes |  |
| `start_date` | Start Date | string | Yes | Use YYYY-MM-DD. |
| `end_date` | End Date | string | No | Optional. Use YYYY-MM-DD. |
| `update_manager` | Update Manager | boolean | No | When true, Manager Full Name replaces the manager on this work record. Leave the name blank to clear it; false preserves it. |
| `manager_name` | Manager Full Name | string | No |  |
| `replace_tags` | Replace Tags | boolean | No | When true, Tags replaces the tags on this work record. Leave Tags blank to clear them; false preserves them. |
| `tag_names` | Tags | string | No |  |
| `source_key` | Unique Source Key | string | Yes | Map a stable unique key from the event, submission, row change, or execution that started this Zap. Jointl uses it to prevent duplicate writes across retries. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Employee ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `full_name` | Full Name | string | No |  |
| `email` | Work Email | string | No |  |
| `status` | Employee Status | string | No |  |
| `outcome` | Action Outcome | string | No |  |
| `position_id` | Work Record ID | string | No |  |
| `company_id` | Company ID | string | No |  |
| `company_name` | Company Name | string | No |  |
| `position_title` | Position Title | string | No |  |
| `start_date` | Start Date | string | No |  |
| `end_date` | End Date | string | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `execution_id` | Jointl Execution ID | string | No |  |
| `replayed` | Replayed Existing Result | boolean | No |  |

### Sample output

```json
{
  "company_id": "company_id",
  "company_name": "Example Company",
  "email": "sam@example.com",
  "employee_id": "employee_id",
  "end_date": null,
  "execution_id": "execution_id",
  "full_name": "Sam Example",
  "id": "employee_id",
  "jointl_url": "https://join.tl/employees/employee_id/overview",
  "outcome": "updated",
  "position_id": "position_id",
  "position_title": "Engineer",
  "replayed": false,
  "start_date": "2026-09-01",
  "status": "active"
}
```

## Import Employees in Bulk

- Zapier key: `bulk_import_employees`
- Kind: action
- Jointl operation: `employees.bulkImport`

Creates or updates up to 250 Employees in one retry-safe import using the existing Employee matching rules.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `default_company_id` | Default Company | string | No | Optional fallback for employee lines without their own Company. This is convenient when every employee belongs to the same company. Choices: . |
| `employees` | Employees | line items | Yes |  |
| `↳ full_name` | Full Name | string | Yes | Map aligned employee line items from a prior step. One run accepts 1–250 rows; repeated identities can add positions. |
| `↳ email` | Work Email | string | No |  |
| `↳ company_id` | Company | string | No | Overrides Default Company for this employee line. Choices: . |
| `↳ position_title` | Position Title | string | Yes |  |
| `↳ start_date` | Start Date | string | Yes | Use YYYY-MM-DD. |
| `↳ end_date` | End Date | string | No | Optional. Use YYYY-MM-DD. |
| `↳ update_manager` | Update Manager | boolean | No | When true, Manager Full Name replaces the manager on a matching position. Leave the name blank to clear it; false preserves it. |
| `↳ manager_name` | Manager Full Name | string | No |  |
| `↳ replace_tags` | Replace Tags | boolean | No | When true, Tags replaces the tags on a matching position. Leave Tags blank to clear them; false preserves them. |
| `↳ tag_names` | Tags | string | No | Map one text value per employee line and separate multiple tag names with commas. |
| `↳ gross_amount` | Gross Compensation | number | No |  |
| `↳ net_amount` | Net Compensation | number | No |  |
| `↳ currency` | Compensation Currency | string | No | Use a three-letter currency code such as USD or EUR. |
| `↳ pay_period` | Compensation Pay Period | string | No | Choices: annual, daily, hourly, monthly, weekly. |
| `↳ compensation_effective_date` | Compensation Effective Date | string | No | Optional. Uses Start Date when omitted; otherwise use YYYY-MM-DD. |
| `source_key` | Unique Source Key | string | Yes | Map a stable unique key from the event, submission, row change, or execution that started this Zap. Jointl uses it to prevent duplicate writes across retries. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Employee Import ID | string | No |  |
| `created_count` | Created Employee Count | integer | No |  |
| `updated_count` | Updated Employee Count | integer | No |  |
| `unchanged_count` | Unchanged Employee Count | integer | No |  |
| `error_count` | Error Count | integer | No |  |
| `employees` | Employees | line items | No |  |
| `↳ employee_id` | Employee ID | string | No |  |
| `↳ full_name` | Full Name | string | No |  |
| `↳ email` | Work Email | string | No |  |
| `↳ outcome` | Import Outcome | string | No |  |
| `↳ source_row_numbers` | Source Row Numbers | integer | No |  |
| `↳ jointl_url` | Jointl URL | string | No |  |
| `errors` | Import Errors | line items | No |  |
| `↳ source_row_numbers` | Source Row Numbers | integer | No |  |
| `↳ row_count` | Affected Row Count | integer | No |  |
| `↳ reason` | Error Reason | string | No |  |
| `execution_id` | Jointl Execution ID | string | No |  |
| `replayed` | Replayed Existing Result | boolean | No |  |

### Sample output

```json
{
  "created_count": 2,
  "employees": [
    {
      "email": "sam@example.com",
      "employee_id": "employee_id_1",
      "full_name": "Sam Example",
      "jointl_url": "https://join.tl/employees/employee_id_1/overview",
      "outcome": "created",
      "source_row_numbers": [
        1
      ]
    },
    {
      "email": "taylor@example.com",
      "employee_id": "employee_id_2",
      "full_name": "Taylor Example",
      "jointl_url": "https://join.tl/employees/employee_id_2/overview",
      "outcome": "created",
      "source_row_numbers": [
        2
      ]
    }
  ],
  "error_count": 0,
  "errors": [],
  "execution_id": "execution_id",
  "id": "execution_id",
  "replayed": false,
  "unchanged_count": 0,
  "updated_count": 0
}
```

## Run All Available Verification Checks

- Zapier key: `run_all_verification_checks`
- Kind: action
- Jointl operation: `checks.verifications.runAll`

Starts every verification available and eligible for one Check; active runs and completed results that cannot be repeated are reused.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `check_id` | Check | string | Yes | Jointl uses the applicant details stored on this Check. Verification types that require unavailable details are skipped. Choices: . |
| `source_key` | Unique Source Key | string | Yes | Map a stable unique key from the event, submission, row change, or execution that started this Zap. Jointl uses it to prevent duplicate writes across retries. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Verification Run Group ID | string | No |  |
| `check_id` | Check ID | string | No |  |
| `run_group_id` | Verification Run Group ID | string | No |  |
| `status` | Run Group Status | string | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `runs` | Verification Runs | line items | No |  |
| `↳ run_id` | Verification Run ID | string | No |  |
| `↳ verification_type` | Verification Type | string | No |  |
| `↳ status` | Verification Status | string | No |  |
| `↳ already_running` | Already Running | boolean | No |  |
| `↳ immutable_result_reused` | Immutable Result Reused | boolean | No |  |
| `execution_id` | Jointl Execution ID | string | No |  |
| `replayed` | Replayed Existing Result | boolean | No |  |

### Sample output

```json
{
  "check_id": "check_id",
  "execution_id": "execution_id",
  "id": "run_group_id",
  "jointl_url": "https://join.tl/checks/check_id/overview",
  "replayed": false,
  "run_group_id": "run_group_id",
  "runs": [
    {
      "already_running": false,
      "immutable_result_reused": false,
      "run_id": "run_id",
      "status": "queued",
      "verification_type": "sanctions"
    }
  ],
  "status": "started"
}
```

## Start Public Profile Discovery

- Zapier key: `start_public_profile_discovery`
- Kind: action
- Jointl operation: `checks.publicProfiles.find`

Starts public-profile discovery for a Check, or reuses or rescores an existing completed run when applicable.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `check_id` | Check | string | Yes | Jointl automatically uses this Check’s name, email, saved location, and confirmed profile links. Choices: . |
| `full_name` | Known Full Name | string | No | Optional. Use only a known full-name spelling that should override the Check name for this search. |
| `aliases` | Known Aliases | string | No | Optional. Add up to eight known alternate names; do not add speculative identities. |
| `cities` | Relevant Cities | string | No |  |
| `states` | Relevant States or Regions | string | No |  |
| `relevant_countries` | Relevant Countries | string | No | Optional. Use two-letter country codes such as US, GB, or TR. |
| `profile_urls` | Known Profile URLs | string | No | Optional. Add up to 16 public profile URLs already known to belong to this person. |
| `source_key` | Unique Source Key | string | Yes | Map a stable unique key from the event, submission, row change, or execution that started this Zap. Jointl uses it to prevent duplicate writes across retries. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Public Profile Run ID | string | No |  |
| `check_id` | Check ID | string | No |  |
| `run_id` | Public Profile Run ID | string | No |  |
| `status` | Run Status | string | No |  |
| `already_running` | Already Running | boolean | No |  |
| `rescored` | Stored Results Rescored | boolean | No |  |
| `match_count` | Profile Match Count | integer | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `execution_id` | Jointl Execution ID | string | No |  |
| `replayed` | Replayed Existing Result | boolean | No |  |

### Sample output

```json
{
  "already_running": false,
  "check_id": "check_id",
  "execution_id": "execution_id",
  "id": "run_id",
  "jointl_url": "https://join.tl/checks/check_id/overview",
  "match_count": null,
  "replayed": false,
  "rescored": false,
  "run_id": "run_id",
  "status": "queued"
}
```

## Change Check Status

- Zapier key: `change_check_status`
- Kind: action
- Jointl operation: `checks.status.set`

Changes one Check to a new status and cancels its pending lifecycle emails and reminders.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `check_id` | Check | string | Yes | Choices: . |
| `current_status` | Current Status | string | Yes | Map the current status from the trigger or the unique Check source returned by Find Person. Jointl rejects stale changes instead of overwriting a newer status. Choices: archived, inProgress, new, rejected, selected, shortlisted. |
| `new_status` | New Status | string | Yes | Selected is intentionally unavailable because selecting a candidate creates an employee through a separate Jointl workflow. Choices: archived, inProgress, new, rejected, shortlisted. |
| `source_key` | Unique Source Key | string | Yes | Map a stable unique key from the event, submission, row change, or execution that started this Zap. Jointl uses it to prevent duplicate writes across retries. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Check ID | string | No |  |
| `check_id` | Check ID | string | No |  |
| `previous_status` | Previous Check Status | string | No |  |
| `status` | Check Status | string | No |  |
| `changed` | Status Changed | boolean | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `execution_id` | Jointl Execution ID | string | No |  |
| `replayed` | Replayed Existing Result | boolean | No |  |

### Sample output

```json
{
  "changed": true,
  "check_id": "check_id",
  "execution_id": "execution_id",
  "id": "check_id",
  "jointl_url": "https://join.tl/checks/check_id/overview",
  "previous_status": "new",
  "replayed": false,
  "status": "shortlisted"
}
```

## Change Employee Status

- Zapier key: `change_employee_status`
- Kind: action
- Jointl operation: `employees.status.set`

Marks one Employee active or left; leaving can close active positions and queue an Exit Intelligence request.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `employee_id` | Employee | string | Yes | Choices: . |
| `current_status` | Current Status | string | Yes | Map the current status from the trigger or the unique Employee source returned by Find Person. Jointl rejects stale changes instead of overwriting a newer status. Choices: active, left. |
| `new_status` | New Status | string | Yes | Choices: active, left. |
| `source_key` | Unique Source Key | string | Yes | Map a stable unique key from the event, submission, row change, or execution that started this Zap. Jointl uses it to prevent duplicate writes across retries. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Employee ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `previous_status` | Previous Employee Status | string | No |  |
| `status` | Employee Status | string | No |  |
| `changed` | Status Changed | boolean | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `exit_intelligence_invitation_status` | Exit Intelligence Invitation Status | string | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `execution_id` | Jointl Execution ID | string | No |  |
| `replayed` | Replayed Existing Result | boolean | No |  |

### Sample output

```json
{
  "changed": true,
  "employee_id": "employee_id",
  "execution_id": "execution_id",
  "exit_intelligence_invitation_status": "queued",
  "exit_intelligence_request_id": "exit_intelligence_request_id",
  "id": "employee_id",
  "jointl_url": "https://join.tl/employees/employee_id/overview",
  "previous_status": "active",
  "replayed": false,
  "status": "left"
}
```

## Change Talent Pool Status

- Zapier key: `change_talent_status`
- Kind: action
- Jointl operation: `talents.status.set`

Changes one Talent Pool profile to a new, shortlisted, or archived status.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `talent_id` | Talent | string | Yes | Choices: . |
| `current_status` | Current Status | string | Yes | Map the current status from the trigger or the unique Talent source returned by Find Person. Jointl rejects stale changes instead of overwriting a newer status. Choices: archived, new, shortlisted. |
| `new_status` | New Status | string | Yes | Choices: archived, new, shortlisted. |
| `source_key` | Unique Source Key | string | Yes | Map a stable unique key from the event, submission, row change, or execution that started this Zap. Jointl uses it to prevent duplicate writes across retries. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Talent ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `previous_status` | Previous Talent Status | string | No |  |
| `status` | Talent Status | string | No |  |
| `changed` | Status Changed | boolean | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `execution_id` | Jointl Execution ID | string | No |  |
| `replayed` | Replayed Existing Result | boolean | No |  |

### Sample output

```json
{
  "changed": true,
  "execution_id": "execution_id",
  "id": "talent_id",
  "jointl_url": "https://join.tl/talents/talent_id/overview",
  "previous_status": "new",
  "replayed": false,
  "status": "shortlisted",
  "talent_id": "talent_id"
}
```

## Send Exit Intelligence Request

- Zapier key: `send_exit_intelligence_request`
- Kind: action
- Jointl operation: `employees.status.set`

Creates or reuses an Exit Intelligence request for an Employee already marked Left and queues its invitation.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `employee_id` | Employee | string | Yes | The employee must already be marked Left with no active positions. Use Change Employee Status when the employee is still active. Choices: . |
| `exit_intelligence_flow_id` | Exit Intelligence Flow | string | Yes | Choose an active Exit Intelligence Flow available for one of this employee’s companies. Choices: . |
| `source_key` | Unique Source Key | string | Yes | Map a stable unique key from the event, submission, row change, or execution that started this Zap. Jointl uses it to prevent duplicate writes across retries. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Exit Intelligence Request ID | string | No |  |
| `exit_intelligence_request_id` | Exit Intelligence Request ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `employee_status` | Employee Status | string | No |  |
| `invitation_status` | Invitation Status | string | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `execution_id` | Jointl Execution ID | string | No |  |
| `replayed` | Replayed Existing Result | boolean | No |  |

### Sample output

```json
{
  "employee_id": "employee_id",
  "employee_status": "left",
  "execution_id": "execution_id",
  "exit_intelligence_request_id": "exit_intelligence_request_id",
  "id": "exit_intelligence_request_id",
  "invitation_status": "queued",
  "jointl_url": "https://join.tl/employees/employee_id/overview",
  "replayed": false
}
```

## Add Note to Check

- Zapier key: `add_note_to_check`
- Kind: action
- Jointl operation: `checks.addNote`

Adds a note to one Check.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `check_id` | Check | string | Yes | Choices: . |
| `text` | Note | text | Yes |  |
| `visible_to_team` | Visible to Team | boolean | No | Default: "false". |
| `source_key` | Unique Source Key | string | Yes | Map a stable unique key from the event, submission, row change, or execution that started this Zap. Jointl uses it to prevent duplicate writes across retries. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Check ID | string | No |  |
| `check_id` | Check ID | string | No |  |
| `note_added` | Note Added | boolean | No |  |
| `visible_to_team` | Visible to Team | boolean | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `execution_id` | Jointl Execution ID | string | No |  |
| `replayed` | Replayed Existing Result | boolean | No |  |

### Sample output

```json
{
  "check_id": "check_id",
  "execution_id": "execution_id",
  "id": "check_id",
  "jointl_url": "https://join.tl/checks/check_id/overview",
  "note_added": true,
  "replayed": false,
  "visible_to_team": false
}
```

## Add Note to Employee

- Zapier key: `add_note_to_employee`
- Kind: action
- Jointl operation: `employees.addNote`

Adds a note to one Employee.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `employee_id` | Employee | string | Yes | Choices: . |
| `text` | Note | text | Yes |  |
| `visible_to_team` | Visible to Team | boolean | No | Default: "false". |
| `source_key` | Unique Source Key | string | Yes | Map a stable unique key from the event, submission, row change, or execution that started this Zap. Jointl uses it to prevent duplicate writes across retries. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Employee ID | string | No |  |
| `employee_id` | Employee ID | string | No |  |
| `note_added` | Note Added | boolean | No |  |
| `visible_to_team` | Visible to Team | boolean | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `execution_id` | Jointl Execution ID | string | No |  |
| `replayed` | Replayed Existing Result | boolean | No |  |

### Sample output

```json
{
  "employee_id": "employee_id",
  "execution_id": "execution_id",
  "id": "employee_id",
  "jointl_url": "https://join.tl/employees/employee_id/overview",
  "note_added": true,
  "replayed": false,
  "visible_to_team": false
}
```

## Add Note to Talent

- Zapier key: `add_note_to_talent`
- Kind: action
- Jointl operation: `talents.addNote`

Adds a note to one Talent.

### Input fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `talent_id` | Talent | string | Yes | Choices: . |
| `text` | Note | text | Yes |  |
| `visible_to_team` | Visible to Team | boolean | No | Default: "false". |
| `source_key` | Unique Source Key | string | Yes | Map a stable unique key from the event, submission, row change, or execution that started this Zap. Jointl uses it to prevent duplicate writes across retries. |

### Output fields

| Key | Label | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| `id` | Talent ID | string | No |  |
| `talent_id` | Talent ID | string | No |  |
| `note_added` | Note Added | boolean | No |  |
| `visible_to_team` | Visible to Team | boolean | No |  |
| `jointl_url` | Jointl URL | string | No |  |
| `execution_id` | Jointl Execution ID | string | No |  |
| `replayed` | Replayed Existing Result | boolean | No |  |

### Sample output

```json
{
  "execution_id": "execution_id",
  "id": "talent_id",
  "jointl_url": "https://join.tl/talents/talent_id/overview",
  "note_added": true,
  "replayed": false,
  "talent_id": "talent_id",
  "visible_to_team": false
}
```

## Delivery contract

See [Zapier webhook event delivery](/rest-api/zapier-webhook-event-delivery) for the notification envelope, delivery behavior, and links to the machine-readable contracts.
