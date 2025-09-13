# Projects

Projects allow you to group related tasks together for better organization.

## The Project Object

| Attribute | Type | Description |
| :--- | :--- | :--- |
| `id` | integer | The unique identifier for the project. |
| `name` | string | The name of the project. |
| `description` | string | A detailed description of the project. |
| `color` | string | A hex color code associated with the project (e.g., `"#ff0000"`). |
| `created_at` | string (ISO 8601) | The time when the project was created. |
| `updated_at` | string (ISO 8601) | The time when the project was last updated. |

## List Projects

Retrieve a paginated list of your projects.

```http
GET /projects
```

**Query Parameters**

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `per_page` | integer | Number of items per page (default 20, max 100). |
| `page` | integer | Page number (default 1). |

**Example request**

```bash
curl -X GET "https://api.taskmanager.com/v1/projects" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE"
```

**Example response**

```json
{
  "data": [
    {
      "id": 101,
      "name": "Work",
      "description": "Tasks related to my job",
      "color": "#3498db",
      "created_at": "2025-03-01T10:00:00Z",
      "updated_at": "2025-03-01T10:00:00Z"
    },
    {
      "id": 102,
      "name": "Personal",
      "description": "Personal tasks and errands",
      "color": "#e74c3c",
      "created_at": "2025-03-02T11:00:00Z",
      "updated_at": "2025-03-02T11:00:00Z"
    }
  ],
  "pagination": {
    "per_page": 20,
    "page": 1,
    "total_count": 2
  }
}
```

## Create a Project

To create a project, you need to provide the following request:

```http
POST /projects
```

**Request Body**

| Attribute     | Type   | Required | Description                                   |
|---------------|--------|----------|-----------------------------------------------|
| `name`        | string | Yes      | The name of the project.                      |
| `description` | string | No       | A detailed description of the project.        |
| `color`       | string | No       | A hex color code (e.g., `"#ff0000"`).         |

**Example request**

```bash
curl -X POST "https://api.taskmanager.com/v1/projects" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Vacation Planning",
    "description": "Tasks for planning my upcoming vacation",
    "color": "#2ecc71"
  }'
```

**Example response**

```json
{
  "data": {
    "id": 103,
    "name": "Vacation Planning",
    "description": "Tasks for planning my upcoming vacation",
    "color": "#2ecc71",
    "created_at": "2025-03-10T12:00:00Z",
    "updated_at": "2025-03-10T12:00:00Z"
  }
}
```


## Retrieve a Project

To retrieve a project, you need to get a specific task by its ID.

```http
GET /projects/{id}
```

**Example request**

```bash
curl -X GET "https://api.taskmanager.com/v1/projects" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE"
```

**Example response**

```json
{
  "data": {
    "id": 103,
    "name": "Vacation Planning",
    "description": "Tasks for planning my upcoming vacation",
    "color": "#2ecc71",
    "created_at": "2025-03-10T12:00:00Z",
    "updated_at": "2025-03-10T12:00:00Z"
  }
}
```

## Update a Project

To update an existing project, you need to provide the following request:

```http
PATCH /projects/{id}
```

**Request Body**

Same as create, but all fields are optional.

**Example request**

```bash
curl -X PATCH "https://api.taskmanager.com/v1/projects/103" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE" \
  -H "Content-Type: application/json" \
  -d '{
    "description": "Tasks for planning my summer vacation"
  }'
```

**Example response**

```json
{
  "data": {
    "id": 103,
    "name": "Vacation Planning",
    "description": "Tasks for planning my summer vacation",
    "color": "#2ecc71",
    "created_at": "2025-03-10T12:00:00Z",
    "updated_at": "2025-03-10T12:30:00Z"
  }
}
```

## Delete a Project

To delete a project permanently, you need to provide the following request:

```http
DELETE /projects/{id}
```

**Example request**

```bash
curl -X DELETE "https://api.taskmanager.com/v1/tasks/78901" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE"
```

**Response**

Returns `204 No Content` on successful deletion.

---

*This is a sample API documentation project for portfolio purposes. All company names, endpoints, and data are fictional.*