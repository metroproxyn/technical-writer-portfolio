# Quick Start Guide

This guide will help you make your first API request in under 5 minutes. Follow these steps to set up your environment, authenticate, and manage your first task.

## Prerequisites

Before you begin, make sure you have:

- A command-line tool (like curl) or an API client (like Postman or Insomnia).
- Your API key from the [Developer Dashboard](https://app.taskmanager.com/developers). *(Example link)*

## Step 1: Authenticate a Request

Let's start by fetching your user profile. This verifies your API key is working correctly.

**Request:**

```bash
curl -X GET "https://api.taskmanager.com/v1/me" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE"
```

**Response:**

```
json
{
  "data": {
    "id": 12345,
    "name": "Your Name",
    "email": "your.email@example.com",
    "timezone": "UTC"
  }
}
```

>**Success:** If you see a response similar to this, your authentication is working! If you get an error, double-check your API key.

## Step 2: Create Your First Task

Now, let's create a new task using the /tasks endpoint.

**Request:**

```bash
curl -X POST "https://api.taskmanager.com/v1/tasks" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE" \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Learn the Task Manager API",
    "description": "Complete the quick start guide and make my first API call.",
    "status": "open"
  }'
```

**Response:**

```json
{
  "data": {
    "id": 67890,
    "title": "Learn the Task Manager API",
    "description": "Complete the quick start guide and make my first API call.",
    "status": "open",
    "created_at": "2025-03-10T10:30:00Z",
    "updated_at": "2025-03-10T10:30:00Z"
  }
}
```

>**Note:** Save the `id` returned in the response (e.g., `67890`). You'll need it for the next steps.

## Step 3: Retrieve Your Tasks

Let's list all your tasks to confirm the new task was created.

**Request:**

```bash
curl -X GET "https://api.taskmanager.com/v1/tasks" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE"
```

**Response:**

```json
{
  "data": [
    {
      "id": 67890,
      "title": "Learn the Task Manager API",
      "description": "Complete the quick start guide and make my first API call.",
      "status": "open",
      "created_at": "2025-03-10T10:30:00Z",
      "updated_at": "2025-03-10T10:30:00Z"
    }
  ],
  "pagination": {
    "page": 1,
    "per_page": 20,
    "total_count": 1,
    "total_pages": 1
  }
}
```

## Step 4: Update the Task

Mark the task as completed by updating its status.

**Request:**

```bash
curl -X PATCH "https://api.taskmanager.com/v1/tasks/67890" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE" \
  -H "Content-Type: application/json" \
  -d '{
    "status": "completed"
  }'
```

**Response:**

```json
{
  "data": {
    "id": 67890,
    "title": "Learn the Task Manager API",
    "description": "Complete the quick start guide and make my first API call.",
    "status": "completed",
    "created_at": "2025-03-10T10:30:00Z",
    "updated_at": "2025-03-10T10:35:00Z"
  }
}
```

## Step 5: Filter Tasks (Optional)

Now, let's retrieve only your completed tasks.

**Request:**

```bash
curl -X GET "https://api.taskmanager.com/v1/tasks?status=completed" \
  -H "Authorization: Bearer YOUR_API_KEY_HERE"
```

**Response:**

```json
{
  "data": [
    {
      "id": 67890,
      "title": "Learn the Task Manager API",
      "status": "completed",
      "created_at": "2025-03-10T10:30:00Z",
      "updated_at": "2025-03-10T10:35:00Z"
    }
  ],
  "pagination": {
    "page": 1,
    "per_page": 20,
    "total_count": 1,
    "total_pages": 1
  }
}
```

## What's Next?

Now that you've successfully made your first API calls, you can:

- **Explore the API Reference:** Learn about all available endpoints, parameters, and advanced features.
  - [Tasks Reference](reference/tasks.md)
  - [Projects Reference](reference/projects.md)
  - [Labels Reference](reference/labels.md)

- **Learn Advanced Concepts:** Understand pagination, rate limiting, and error handling in detail.
  - [Core Concepts](concepts.md)

- **Try the Postman Collection:** Import our ready-to-use collection for easier testing.
  - [Download Postman Collection](assets/postman-collection.json) (*Example asset*)

## Need Help?

- Check the [Core Concepts](concepts.md) for information about authentication and errors.

- If you encounter issues, verify your API key and ensure you're using the correct base URL (`https://api.taskmanager.com/v1`).

---

*This is a sample API documentation project for portfolio purposes. All company names, endpoints, and data are fictional.*