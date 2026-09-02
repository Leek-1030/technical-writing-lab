# Exercise B – API Reference Entry

# Create Task

## HTTP Method and Endpoint

```http
POST /api/v1/projects/{project_id}/tasks
```

## Description

Creates a new task inside an existing project.

The authenticated user must have permission to create tasks in the selected project.

A task must contain a title, an assignee, a due date, and a priority level. A description is optional.

## Request Parameters

### Path Parameters

| Parameter | Data Type | Required | Description |
|---|---|---|---|
| `project_id` | Integer | Yes | Unique ID of the project where the new task will be created. |

### Query Parameters

This endpoint does not require any query parameters.

### Request Body Parameters

| Parameter | Data Type | Required | Description |
|---|---|---|---|
| `title` | String | Yes | Short title describing the task. |
| `description` | String | No | Additional information or instructions about the task. |
| `assignee_id` | Integer | Yes | Unique user ID of the person assigned to the task. |
| `due_date` | String | Yes | Due date using the `YYYY-MM-DD` format. |
| `priority` | String | Yes | Priority level. Accepted values are `low`, `medium`, or `high`. |

## Required Request Headers

| Header | Required | Description |
|---|---|---|
| `Authorization` | Yes | Authentication token using the Bearer token format. |
| `Content-Type` | Yes | Specifies that the request body contains JSON. Use `application/json`. |
| `Accept` | No | Specifies the preferred response format. Recommended value: `application/json`. |

### Authentication Example

```http
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.example-token
```

## Example Request

```http
POST /api/v1/projects/42/tasks
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.example-token
Content-Type: application/json
Accept: application/json
```

### Example Request Body

```json
{
  "title": "Design login page",
  "description": "Create the initial responsive design for the application's login page.",
  "assignee_id": 18,
  "due_date": "2026-09-15",
  "priority": "high"
}
```

## Successful Response

### HTTP Status

```http
201 Created
```

### Example Response Body

```json
{
  "success": true,
  "message": "Task created successfully.",
  "data": {
    "id": 157,
    "project_id": 42,
    "title": "Design login page",
    "description": "Create the initial responsive design for the application's login page.",
    "assignee": {
      "id": 18,
      "name": "Amina Hassan"
    },
    "due_date": "2026-09-15",
    "priority": "high",
    "status": "open",
    "created_at": "2026-09-02T10:25:30+03:00",
    "updated_at": "2026-09-02T10:25:30+03:00"
  }
}
```

## HTTP Response Codes

| Status Code | Meaning | When It Occurs |
|---|---|---|
| `201 Created` | Success | The task was created successfully. |
| `400 Bad Request` | Invalid Request | The request contains invalid JSON or incorrectly formatted data. |
| `401 Unauthorized` | Authentication Required | The authentication token is missing, invalid, or expired. |
| `403 Forbidden` | Permission Denied | The authenticated user does not have permission to create tasks in the project. |
| `404 Not Found` | Resource Not Found | The specified project or assignee cannot be found. |
| `409 Conflict` | Conflict | The request conflicts with an existing resource or project rule. |
| `422 Unprocessable Entity` | Validation Error | Required information is missing or a field contains an unacceptable value. |
| `500 Internal Server Error` | Server Error | An unexpected problem occurs on the server while creating the task. |

## Example Validation Error

If `priority` is set to `urgent` instead of `low`, `medium`, or `high`, the API could return:

```json
{
  "success": false,
  "message": "Validation failed.",
  "errors": {
    "priority": [
      "Priority must be low, medium, or high."
    ]
  }
}
```

The HTTP response status would be:

```http
422 Unprocessable Entity
```

## Summary

The `POST /api/v1/projects/{project_id}/tasks` endpoint provides a structured way for authenticated users to create tasks in a project management application. Authentication is required, input values are validated before the task is created, and appropriate HTTP status codes help clients identify successful and unsuccessful requests.
