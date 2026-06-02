# Generic API Usage Pseudocode

These examples are intentionally non-functional and public-safe. They illustrate interaction concepts only.

```text
authenticate user
receive authenticated session context

create incident with:
  project code
  title
  priority
  category
  description

backend validates:
  user identity
  project access
  required fields
  SLA policy

backend creates:
  incident record
  audit event
  notification event
```

```text
request AI assistance for incident

backend collects authorized context:
  incident summary
  lifecycle state
  similar records
  SLA status
  linked problem/change data

AI service returns:
  RCA draft
  risk signal
  knowledge article draft
  recommended next actions
```
