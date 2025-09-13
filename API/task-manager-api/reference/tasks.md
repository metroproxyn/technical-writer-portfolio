# Tasks

Tasks are the core building blocks of the Task Manager API. Use these endpoints to create, manage, and track your to-do items.

## The Task Object

| Attribute | Type | Description |
| :--- | :--- | :--- |
| `id` | integer | The unique identifier for the task. Read-only. |
| `title` | string | The title of the task. |
| `description` | string | A detailed description of the task. Optional. |
| `status` | string | The current status of the task. One of: `open`, `in_progress`, `completed`, `archived`. Default: `open`. |
| `due_date` | string <br> (ISO 8601) | The due date and time for the task. Optional. |
| `project_id` | integer | The ID of the project this task belongs to. Optional. |
| `labels` | array of strings | Tags for categorizing the task. Optional. |
| `created_at` | string <br> (ISO 8601) | The timestamp when the task was created. Read-only. |
| `updated_at` | string <br> (ISO 8601) | The timestamp when the task was last updated. Read-only. |

## List all tasks

Retrieves a paginated list of your tasks.

```http
GET /tasks
```

### Query parameters

| Parameter   | Type    | Description                                                       |
|-------------|---------|-------------------------------------------------------------------|
| `status`    | string  | Filter tasks by status.                                           |
| `project_id`| integer | Filter tasks by project ID.                                       |
| `due_date`  | string  | Filter tasks by due date (supports ISO 8601 date ranges).         |
| `q`         | string  | Search term to filter tasks by title or description.              |
| `per_page`  | integer | Number of items per page (default: 20, max: 100).                 |
| `page`      | integer | Page number (default: 1).                                         |

**Example request**

```bash
curl -X GET "https://api.taskmanager.com/v1/tasks?status=open&per_page=5" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE"
```

**Example response**

```json
{
  "data": [
    {
      "id": 67890,
      "title": "Learn the Task Manager API",
      "description": "Complete the quick start guide",
      "status": "open",
      "due_date": "2025-03-15T23:59:59Z",
      "project_id": 12345,
      "labels": ["documentation", "api"],
      "created_at": "2025-03-10T10:30:00Z",
      "updated_at": "2025-03-10T10:30:00Z"
    }
  ],
  "pagination": {
    "page": 1,
    "per_page": 5,
    "total_count": 23,
    "total_pages": 5
  }
}
```

## Create a task

To create a task, you need to provide the following request:

```http
POST /tasks
```

### Request body parameters

| Attribute     | Type             | Required | Description                                                   |
|---------------|------------------|----------|---------------------------------------------------------------|
| `title`       | string           | Yes      | The title of the task.                                        |
| `description` | string           | No       | A detailed description of the task.                           |
| `status`      | string           | No       | The status of the task. Default: `open`.                      |
| `due_date`    | string           | No       | The due date and time (ISO 8601 format).                      |
| `project_id`  | integer          | No       | The ID of the project this task belongs to.                   |
| `labels`      | array of strings | No       | Tags for categorizing the task.                               |


**Example request**

```bash
curl -X POST "https://api.taskmanager.com/v1/tasks" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE" \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Review API documentation",
    "description": "Check the new endpoints for accuracy",
    "status": "in_progress",
    "due_date": "2025-03-20T18:00:00Z",
    "labels": ["review", "important"]
  }'

```

**Example response**

```json
{
  "data": {
    "id": 78901,
    "title": "Review API documentation",
    "description": "Check the new endpoints for accuracy",
    "status": "in_progress",
    "due_date": "2025-03-20T18:00:00Z",
    "project_id": null,
    "labels": ["review", "important"],
    "created_at": "2025-03-11T09:15:00Z",
    "updated_at": "2025-03-11T09:15:00Z"
  }
}
```

## Retrieve a task

To retrieve a task, you need to get a specific task by its ID.

```http
GET /tasks/{id}
```

**Path parameters**

| Parameter | Description |
| :--- | :--- |
| `id` | The ID of the task to retrieve |

**Example request**

```bash
curl -X GET "https://api.taskmanager.com/v1/tasks/78901" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE"
```

**Example response**

```json
{
  "data": {
    "id": 78901,
    "title": "Review API documentation",
    "description": "Check the new endpoints for accuracy",
    "status": "in_progress",
    "due_date": "2025-03-20T18:00:00Z",
    "project_id": null,
    "labels": ["review", "important"],
    "created_at": "2025-03-11T09:15:00Z",
    "updated_at": "2025-03-11T09:15:00Z"
  }
}
```

## Update a task

To update an existing task, you need to provide the following request:

```http
PATCH /tasks/{id}
```

**Path parameters**

| Parameter | Description |
| :--- | :--- |
| `id` | The ID of the task to update |

**Example request**

Same as create endpoint, but all fields are optional.

```bash
curl -X PATCH "https://api.taskmanager.com/v1/tasks/78901" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE" \
  -H "Content-Type: application/json" \
  -d '{
    "status": "completed",
    "labels": ["review", "important", "done"]
  }'
```

**Example response**

```json
{
  "data": {
    "id": 78901,
    "title": "Review API documentation",
    "description": "Check the new endpoints for accuracy",
    "status": "completed",
    "due_date": "2025-03-20T18:00:00Z",
    "project_id": null,
    "labels": ["review", "important", "done"],
    "created_at": "2025-03-11T09:15:00Z",
    "updated_at": "2025-03-11T14:20:00Z"
  }
}
```

## Delete a task

To delete a task permanently, you need to provide the following request:

```http
DELETE /tasks/{id}
```

**Path parameters**

| Parameter | Description |
| :--- | :--- |
| `id` | The ID of the task to delete |

**Example request**

```bash
curl -X DELETE "https://api.taskmanager.com/v1/tasks/78901" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE"
```

**Response**

Returns `204 No Content` on successful deletion.

**Errors**

This endpoint may return the following errors:

| Status code | Error code | Description |
| :--- | :--- | :--- |
| 400 | `validation_error` | The request body contains invalid data. |
| 403 | `forbidden` | You don't have permission to access this task. |
| 404 | `not_found` | The specified task could not be found. |

---

*This is a sample API documentation project for portfolio purposes. All company names, endpoints, and data are fictional.*