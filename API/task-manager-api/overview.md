# Task Manager API Documentation

> **ℹ️ Portfolio Sample Notice**  
> This is a **sample documentation project** created to demonstrate technical writing skills. The API, endpoints, and company described here are fictional. Any referenced links are for example purposes only.

The Task Manager API provides a simple yet powerful interface for creating, tracking, and organizing your tasks and projects. It supports full CRUD operations, filtering, sorting, and user collaboration.

*   **Tools:** OpenAPI 3.1, Redoc, GitHub Actions.
*   **Features:**
    *   Interactive API reference with try-it-out functionality.
    *   Detailed endpoint descriptions with request and response examples.
    *   Code snippets in multiple programming languages.
    *   Error handling documentation.

## Explore the Documentation

* [Core Concepts](concepts.md) – Authentication, rate limiting, pagination, and errors.
* [Quick Start Guide](quickstart.md) – Make your first API request in 5 minutes.
* [API Reference](Aoverview.md) – Detailed endpoint specification with live examples.
* [Guides](guides/search-filter.md) – Practical tutorials and common workflows.

---

## API Basics

**Base URL:** `https://api.taskmanager.com/v1`

**Authentication:** All requests require an API key sent in the `Authorization` header.
```http
Authorization: Bearer YOUR_API_KEY_HERE
```
[Learn about authentication →](concepts.md)

**Data Format:** JSON for all request and response bodies.

**Rate Limiting:** 100 requests per minute per API key.
[See details →](.сoncepts.md#rate-limiting)

---

## Get Started

Ready to start? This example retrieves your user profile.

1.  **Get your API Key:** [Sign up](https://app.taskmanager.com/signup) for a developer account.
2.  **Authenticate your request:** Include your key in the header.
3.  **Call the `/me` endpoint:**

```bash
curl -X GET "https://api.taskmanager.com/v1/me" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE"
```

[Follow the step-by-step Quick Start guide →](quickstart.md)

---

## API Resources

The API is built around a few main resources:

| Resource | Description | Endpoint |
| :--- | :--- | :--- |
| **Task** | An individual to-do item | `/tasks` |
| **Project** | A group of related tasks | `/projects` |
| **Label** | A tag for categorizing tasks | `/labels` |
| **User** | Profile and account information | `/me` |

[View the full API Reference →](./reference/)

---

## SDKs & Tools

*   **Official JavaScript SDK** – [GitHub Repository](https://github.com/example) *(Example link)*
*   **Postman Collection** – [Download Collection](./assets/postman-collection.json) *(Example asset)*
*   **OpenAPI Spec** – [View Specification](./openapi.yaml) – The source of truth for this API.

---

*This is a sample API documentation project for portfolio purposes. All company names, endpoints, and data are fictional.*