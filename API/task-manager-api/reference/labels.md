# Labels

Labels are tags that you can use to categorize and filter tasks. Each label is represented by a unique name and color.

## The Label Object

| Attribute | Type | Description |
| :--- | :--- | :--- |
| `id` | string | Unique identifier for the label (read-only). |
| `name` | string | The name of the label (1-50 characters). |
| `color` | string | Hex code of the label color (e.g., `#FF5733`). |
| `created_at` | string | Creation timestamp (ISO 8601 format). |
| `updated_at` | string | Last update timestamp (ISO 8601 format). |

### Example Label Object
```json
{
  "data": {
    "id": "label_abc123",
    "name": "urgent",
    "color": "#FF0000",
    "created_at": "2025-03-10T10:30:00Z",
    "updated_at": "2025-03-10T10:30:00Z"
  }
}
```

## List all labels

Retrieve a paginated list of all labels in your account.

```http
GET /labels
```

### Query parameters

| Parameter   | Type    | Description                                                       |
|-------------|---------|-------------------------------------------------------------------|
| `per_page	`    | integer  | Items per page (default: 20, max: 100). |
| `page`| integer | Page number (default: 1).|

**Example request**

```bash
curl -X GET "https://api.taskmanager.com/v1/labels?per_page=5" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE"
```

**Example response**

```json
{
  "data": [
    {
      "id": "label_abc123",
      "name": "urgent",
      "color": "#FF0000"
    },
    {
      "id": "label_def456",
      "name": "backend",
      "color": "#3366FF"
    }
  ],
  "pagination": {
    "page": 1,
    "per_page": 5,
    "total_count": 12,
    "total_pages": 3
  }
}
```

## Create a Label

To create a new label with the specified name and color, you need to provide the following request:

```http
POST /labels
```

### Request Body Parameters

| Parameter     | Type             | Required | Description                                                   |
|---------------|------------------|----------|---------------------------------------------------------------|
| `name`       | string           | Yes      | Label name (1-50 characters).                                       |
| `color	` | string           | No       | Hex color code (default: #666666).                           |


**Example request**

```bash
curl -X POST "https://api.taskmanager.com/v1/labels" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "documentation",
    "color": "#33CC33"
  }'
```

**Example response**

```json
{
  "data": {
    "id": "label_ghi789",
    "name": "documentation",
    "color": "#33CC33",
    "created_at": "2025-03-10T11:15:00Z",
    "updated_at": "2025-03-10T11:15:00Z"
  }
}
```

## Retrieve a Label

To retrieve a label, you need to specify label by its ID.

```http
GET /labels/{id}
```

**Example request**

```bash
curl -X GET "https://api.taskmanager.com/v1/labels/label_abc123" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE"
```

## Update a Label

To update an existing label's name or color, you need to provide the following request:

```http
PATCH /labels/{id}
```

**Request Body**

| Parameter     | Type             | Required | Description                                                   |
|---------------|------------------|----------|---------------------------------------------------------------|
| `name`       | string           | Yes      | Label name (1-50 characters).                                       |
| `color	` | string           | No       | New hex color code.                           |

**Example request**

```bash
ccurl -X PATCH "https://api.taskmanager.com/v1/labels/label_abc123" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE" \
  -H "Content-Type: application/json" \
  -d '{
    "color": "#CC3333"
  }'
```

## Delete a Label

To delete a label and remove it from all tasks, you need to provide the following request:

```http
DELETE /tasks/{id}
```

**Example request**

```bash
curl -X DELETE "https://api.taskmanager.com/v1/labels/label_abc123" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE"
```

**Response**

Returns `204 No Content` on successful deletion.

## Add Label to Task

To add a label to a specific task, you need to provide the following request:

```http
POST /tasks/{task_id}/labels
```
**Request Body**

| Parameter     | Type             | Required | Description                                                   |
|---------------|------------------|----------|---------------------------------------------------------------|
| `label_id`       | string           | Yes      | ID of the label to add.                          |

**Example request**

```bash
curl -X POST "https://api.taskmanager.com/v1/tasks/task_123/labels" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE" \
  -H "Content-Type: application/json" \
  -d '{
    "label_id": "label_abc123"
  }'
```

## Remove Label from Task

To remove label from a task, you need to provide the following request:

```http
DELETE /tasks/{task_id}/labels/{label_id}
```
**Request Body**

| Parameter     | Type             | Required | Description                                                   |
|---------------|------------------|----------|---------------------------------------------------------------|
| `label_id`       | string           | Yes      | ID of the label to add.                          |

**Example request**

```bash
curl -X DELETE "https://api.taskmanager.com/v1/tasks/task_123/labels/label_abc123" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE"
```

**Response**

Returns `204 No Content` on successful deletion.

**Errors**

This endpoint may return the following errors:

| Error code | HTTP Status | Description |
| :--- | :--- | :--- |
| `label_not_found` | 404 | The specified label doesn't exist. |
| `label_name_taken` | 409 | A label with this name already exists. |
| `invalid_color_format` | 400 | Color must be a valid hex code. |

---

*This is a sample API documentation project for portfolio purposes. All company names, endpoints, and data are fictional.*