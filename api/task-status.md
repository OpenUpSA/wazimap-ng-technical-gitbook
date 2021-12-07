---
description: API Endpoint for checking the status of a task
---

# Task Status

Check the status of a background task via API.

```
GET /api/v1/tasks/:id/
```

#### Response

```javascript
{
  "id": ":task_id",
  "status": "running|error|success",
}
```
