# Core Concepts

This section explains the fundamental principles that apply across the entire Task Manager API, including authentication, rate limiting, and how the API handles requests and responses.

## Authentication

All API requests require authentication using a Bearer Token (JWT). You can obtain your API key from the Developer Dashboard in your account settings.

Include the key in the `Authorization` header of every request:

```http
Authorization: Bearer YOUR_API_KEY_HERE
```

API keys are secret and must not be shared or committed to version control.

## Rate Limiting

To ensure fair use and stability, the API enforces rate limits:

- **100 requests per minute** per API key.
- The limits are tracked on a rolling basis.

If exceeded, you will receive a `429 Too Many Requests` response. Check the following headers for rate limit information:

- `X-RateLimit-Limit`: The total number of requests allowed in a minute.
- `X-RateLimit-Remaining`: The number of requests remaining in the current window.
- `X-RateLimit-Reset`: The time at which the current rate limit window resets (UTC epoch seconds).

## Pagination

Endpoints that return a list of resources (e.g., `GET /tasks`) support pagination to manage large result sets.

By default, these endpoints return 20 items per page. You can specify the page size (max 100) and page number using query parameters:

```http
GET /tasks?page=2&per_page=50
```

The response includes pagination headers:

- `Link`: Contains links to the next, previous, first, and last pages.
- `X-Total-Count`: The total number of items across all pages.

The response body also includes pagination metadata:

```json
{
  "data": [
    // ... array of items
  ],
  "pagination": {
    "page": 2,
    "per_page": 50,
    "total_count": 150,
    "total_pages": 3
  }
}
```

## Errors

The Task Manager API uses conventional HTTP response codes to indicate success or failure.

| Code | Meaning | Description |
| :--- | :--- | :--- |
| `200` | Success | The request was successful. |
| `201` | Created | A resource was created successfully. |
| `400` | Bad Request | The request was invalid (e.g., validation error). |
| `401` | Unauthorized | Invalid or missing API key. |
| `403` | Forbidden | Insufficient permissions for the resource. |
| `404` | Not Found | The requested resource doesn't exist. |
| `429` | Too Many Requests | Rate limit exceeded. |
| `5xx` | Server Error | An internal server error occurred. |

Error responses include a JSON body with details:

```json
{
  "error": {
    "code": "invalid_token",
    "message": "The API key is invalid.",
    "documentation_url": "https://docs.taskmanager.com/concepts#authentication"
  }
}
```

Common error codes:

| Code | Description |
| :--- | :--- |
| `invalid_token` | The API key is missing or invalid. |
| `validation_error` | Request parameters failed validation. |
| `not_found` | The requested resource doesn't exist. |
| `rate_limit_exceeded` | Too many requests in a given time frame. |

## Data Format

All request and response bodies are in JSON format. Use the `Content-Type: application/json` header in your requests.

Request example:

```http
POST /tasks
Content-Type: application/json
Authorization: Bearer YOUR_API_KEY_HERE

{
  "title": "New Task",
  "description": "This is a new task"
}
```

Response example:

```json
{
  "data": {
    "id": 123,
    "title": "New Task",
    "description": "This is a new task",
    "status": "open"
  }
}
```

## Timestamps

All timestamps are returned in ISO 8601 format:

```json
{
  "created_at": "2025-03-01T10:00:00Z",
  "updated_at": "2025-03-01T14:30:00Z"
}
```

## Field Selection

Use the `fields` parameter to limit the returned attributes for each resource. This can improve performance for large objects.

```http
GET /tasks/123?fields=id,title,status
```

Response:

```json
{
  "data": {
    "id": 123,
    "title": "New Task",
    "status": "open"
  }
}
```

---

*This is a sample API documentation project for portfolio purposes. All company names, endpoints, and data are fictional.*
