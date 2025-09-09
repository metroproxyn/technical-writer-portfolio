# API Reference

This section provides detailed documentation for all available API endpoints. Explore the resources below to understand the request and response formats, parameters, and errors.

## Core Resources

*   **[Tasks](API/task-manager-api/reference/tasks.md)** – Manage your to-do items. Create, read, update, delete, and filter tasks.
*   **[Projects](API/task-manager-api/reference/projects.md)** – Organize tasks into projects for better structure.
*   **[Labels](API/task-manager-api/reference/labels.md)** – Categorize and filter tasks using custom labels.

## System Endpoints 
(TBD)

*   **[Users]()** – Retrieve your profile and account information.

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