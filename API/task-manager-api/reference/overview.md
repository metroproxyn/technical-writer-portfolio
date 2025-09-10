# API Reference

This section provides detailed documentation for all available API endpoints. Explore the resources below to understand the request and response formats, parameters, and errors.

## Core Resources

-   **[Tasks](tasks.md)** – Manage your to-do items. Create, read, update, delete, and filter tasks.
-   **[Projects](projects.md)** – Organize tasks into projects for better structure.
-   **[Labels](labels.md)** – Categorize and filter tasks using custom labels.

## System Endpoints 
(TBD)

-   **[Users](users.md)** – Retrieve your profile and account information.

## Response Format

All successful API responses return a JSON object. The structure may vary by endpoint but generally follows these patterns:

**Single Resource:**
```json
{
  "data": {
    "id": 123,
    "attribute": "value",
    ...
  }
}
```

**List of Resources:**
```json
{
  "data": [
    { "id": 123, ... },
    { "id": 456, ... }
  ],
  "meta": {
    "per_page": 20,
    "page": 1,
    "total_count": 2
  }
}
```
**Error Response:**
```json
{
  "error": {
    "code": "invalid_request",
    "message": "The 'title' parameter is required."
  }
}
```