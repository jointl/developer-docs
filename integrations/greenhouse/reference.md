---
title: Greenhouse endpoint reference
description: The production origin is https://api.join.tl.
---

The production origin is `https://api.join.tl`. These are the only Jointl endpoints in the Greenhouse integration. Greenhouse Harvest calls are upstream dependencies and are not Jointl endpoints.

| Method | Path | Authentication |
| --- | --- | --- |
| `POST` | `/api/apps/greenhouse/v1/webhook/{installationId}` | signature |
| `GET` | `/api/apps/greenhouse/v1/assessment/list_tests` | basic |
| `POST` | `/api/apps/greenhouse/v1/assessment/send_test` | basic |
| `GET` | `/api/apps/greenhouse/v1/assessment/test_status` | basic |
| `POST` | `/api/apps/greenhouse/v1/assessment/response_error` | basic |

## Accepted webhook actions

- `ping`
- `job_created`
- `job_deleted`
- `new_candidate_application`
- `application_updated`
- `candidate_stage_change`
- `hire_candidate`
- `unhire_candidate`
- `reject_candidate`
- `unreject_candidate`
- `delete_candidate`

## Receive webhook

`POST /api/apps/greenhouse/v1/webhook/{installationId}`

Authentication: the `Signature` header plus `Greenhouse-Event-ID`.

Example request and response:

```json
{
  "actions": {
    "application_updated": {
      "action": "application_updated",
      "payload": {
        "application": {
          "candidate": {
            "email_addresses": [
              {
                "type": "work",
                "value": "ada@example.test"
              }
            ],
            "first_name": "Ada",
            "id": 20001,
            "last_name": "Example",
            "photo_url": "https://example.com/images/ada.png",
            "url": "https://example.com/candidates/20001"
          },
          "current_stage": {
            "id": 40001,
            "name": "Jointl Review"
          },
          "id": 10001,
          "jobs": [
            {
              "id": 30001
            }
          ],
          "prospect": false,
          "status": "active"
        }
      }
    },
    "candidate_stage_change": {
      "action": "candidate_stage_change",
      "payload": {
        "application": {
          "candidate": {
            "email_addresses": [
              {
                "type": "work",
                "value": "ada@example.test"
              }
            ],
            "first_name": "Ada",
            "id": 20001,
            "last_name": "Example",
            "photo_url": "https://example.com/images/ada.png",
            "url": "https://example.com/candidates/20001"
          },
          "current_stage": {
            "id": 40001,
            "name": "Jointl Review"
          },
          "id": 10001,
          "jobs": [
            {
              "id": 30001
            }
          ],
          "prospect": false,
          "status": "active"
        }
      }
    },
    "delete_candidate": {
      "action": "delete_candidate",
      "payload": {
        "person": {
          "id": 20001
        }
      }
    },
    "hire_candidate": {
      "action": "hire_candidate",
      "payload": {
        "application": {
          "candidate": {
            "id": 20001
          },
          "id": 10001
        }
      }
    },
    "job_created": {
      "action": "job_created",
      "payload": {
        "job": {
          "id": 30001,
          "name": "Example Software Engineer"
        }
      }
    },
    "job_deleted": {
      "action": "job_deleted",
      "payload": {
        "job": {
          "id": 30001,
          "name": "Example Software Engineer"
        }
      }
    },
    "new_candidate_application": {
      "action": "new_candidate_application",
      "payload": {
        "application": {
          "candidate": {
            "email_addresses": [
              {
                "type": "work",
                "value": "ada@example.test"
              }
            ],
            "first_name": "Ada",
            "id": 20001,
            "last_name": "Example",
            "photo_url": "https://example.com/images/ada.png",
            "url": "https://example.com/candidates/20001"
          },
          "current_stage": {
            "id": 40001,
            "name": "Jointl Review"
          },
          "id": 10001,
          "jobs": [
            {
              "id": 30001
            }
          ],
          "prospect": false,
          "status": "active"
        }
      }
    },
    "ping": {
      "action": "ping",
      "payload": {}
    },
    "reject_candidate": {
      "action": "reject_candidate",
      "payload": {
        "application": {
          "candidate": {
            "id": 20001
          },
          "id": 10001
        }
      }
    },
    "unhire_candidate": {
      "action": "unhire_candidate",
      "payload": {
        "application": {
          "candidate": {
            "id": 20001
          },
          "id": 10001
        }
      }
    },
    "unreject_candidate": {
      "action": "unreject_candidate",
      "payload": {
        "application": {
          "candidate": {
            "id": 20001
          },
          "id": 10001
        }
      }
    }
  },
  "conflict": {
    "body": "Webhook event conflict",
    "status": 409
  },
  "request": {
    "body": {
      "action": "candidate_stage_change",
      "payload": {
        "application": {
          "id": 10001
        },
        "candidate": {
          "email_addresses": [
            {
              "value": "ada@example.test"
            }
          ],
          "first_name": "Ada",
          "id": 20001,
          "last_name": "Example"
        }
      }
    },
    "headers": {
      "Greenhouse-Event-ID": "greenhouse-event-example-01",
      "Signature": "sha256=EXAMPLE_SIGNATURE"
    }
  },
  "success": {
    "body": "OK",
    "status": 200
  }
}
```

## List tests

`GET /api/apps/greenhouse/v1/assessment/list_tests`

Authentication: installation API key with HTTP Basic authentication.

Example request and response:

```json
{
  "request": {
    "method": "GET"
  },
  "success": [
    {
      "partner_test_id": "flow_example_01",
      "partner_test_name": "Example Hiring Flow"
    }
  ]
}
```

## Send test

`POST /api/apps/greenhouse/v1/assessment/send_test`

Authentication: installation API key with HTTP Basic authentication.

Example request and response:

```json
{
  "request": {
    "application": {
      "id": 10001
    },
    "candidate": {
      "email": "ada@example.test",
      "first_name": "Ada",
      "greenhouse_profile_url": "https://example.com/candidates/20001",
      "id": 20001,
      "last_name": "Example"
    },
    "partner_test_id": "flow_example_01",
    "url": "https://example.com/assessment/complete"
  },
  "success": {
    "partner_interview_id": "request_example_01"
  }
}
```

## Test status

`GET /api/apps/greenhouse/v1/assessment/test_status`

Authentication: installation API key with HTTP Basic authentication.

Example request and response:

```json
{
  "request": {
    "partner_interview_id": "request_example_01"
  },
  "success": {
    "metadata": {
      "Started At": "Thu, Jan 15 2026, 10:30"
    },
    "partner_profile_url": "https://join.tl/checks/check_example_01/overview",
    "partner_score": 75,
    "partner_status": "in_progress"
  }
}
```

## Response error

`POST /api/apps/greenhouse/v1/assessment/response_error`

Authentication: installation API key with HTTP Basic authentication.

Example request and response:

```json
{
  "request": {
    "error": "invalid_response"
  },
  "success": {
    "body": "OK",
    "status": 200
  }
}
```

## Limits and retry behavior

- Maximum request body: 1048576 bytes.
- POST bodies must be JSON objects; invalid or missing JSON returns `400` without echoing request content, and an oversized body returns `413`.
- Network: 600 requests per minute.
- Webhook installation: 300 requests per minute.
- Assessment reads: 120 requests per minute.
- Assessment mutation: 20 requests per minute.

Preserve the exact webhook event ID and body when retrying. `409` means the event identity was reused for different content; `503` can mean the same event is already processing.
