# Users

The Users resource allows you to manage user profiles and account information. Currently, you can only retrieve your own user information.

## The User Object

| Attribute | Type | Description |
| :--- | :--- | :--- |
| `id` | integer | Unique identifier for the user. |
| `name` | string | Full name of the user. |
| `email` | string | Email address of the user. |
| `timezone` | string | User's timezone (e.g., "America/New_York"). |
| `created_at` | string | Creation timestamp (ISO 8601 format). |
| `updated_at` | string | Last update timestamp (ISO 8601 format). |

### Example User Object

```json
{
  "data": {
    "id": 12345,
    "name": "John Doe",
    "email": "john.doe@example.com",
    "timezone": "UTC",
    "created_at": "2025-03-01T10:00:00Z",
    "updated_at": "2025-03-10T14:30:00Z"
  }
}
```

## Retrieve Your User Profile
Get the profile information of the currently authenticated user.

```http
GET /me
```

**Example Request**

```bash
curl -X GET "https://api.taskmanager.com/v1/me" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE"
```

**Example Response**

```json
{
  "data": {
    "id": 12345,
    "name": "John Doe",
    "email": "john.doe@example.com",
    "timezone": "UTC",
    "created_at": "2025-03-01T10:00:00Z",
    "updated_at": "2025-03-10T14:30:00Z"
  }
}
```

## Update Your User Profile

Update your profile information (e.g., timezone).

```http
PATCH /me
```

**Request Body**

| Parameter     | Type             | Required | Description                                                   |
|---------------|------------------|----------|---------------------------------------------------------------|
| `name`       | string           | No      | Your full name. |
| `timezone` | string           | No       | Your timezone (must be a valid IANA timezone).|

**Example Request**

```bash
curl -X PATCH "https://api.taskmanager.com/v1/me" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE" \
  -H "Content-Type: application/json" \
  -d '{
    "timezone": "America/New_York"
  }'
```

**Example Response**

```json
{
  "data": {
    "id": 12345,
    "name": "John Doe",
    "email": "john.doe@example.com",
    "timezone": "America/New_York",
    "created_at": "2025-03-01T10:00:00Z",
    "updated_at": "2025-03-10T15:45:00Z"
  }
}
```

**Error Responses**

| Error code | HTTP Status | Description |
| :--- | :--- | :--- |
| `invalid_timezone` | 400 | The provided timezone is not valid. |

---

*This is a sample API documentation project for portfolio purposes. All company names, endpoints, and data are fictional.*