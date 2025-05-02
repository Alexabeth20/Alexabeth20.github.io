

# Developer Onboarding Guide: FictionalApp REST API

Welcome to the **FictionalApp API**! This guide is designed to help developers quickly understand how to integrate with our productivity platform's RESTful API.

---

## What is FictionalApp?

FictionalApp is a productivity platform that helps remote teams manage tasks, projects, and collaboration. Developers can use our API to create users, assign tasks, and build tools or dashboards that extend the platform.

---

## Getting Started

### Base URL

```
https://api.fictionalapp.com/v1
```

All API endpoints start with this base URL.

---

## Authentication

To authenticate, use the `/auth/token` endpoint to retrieve a bearer token:

**POST /auth/token**

**Request Example:**
```json
{
  "email": "user@example.com",
  "password": "yourpassword"
}
```

**Response Example:**
```json
{
  "token": "your-jwt-token-here"
}
```

Include the token in all subsequent requests using the `Authorization` header:

```
Authorization: Bearer your-jwt-token-here
```

---

## Common API Actions

### 1. Create a User

**POST /users**

Create a new user account.

### 2. Create a Task

**POST /tasks**

**Request Example:**
```json
{
  "title": "Write blog post",
  "description": "Write Swagger API tutorial",
  "due_date": "2025-04-25"
}
```

### 3. Get All Tasks

**GET /tasks**

Retrieve all tasks for the authenticated user.

### 4. Get a Single Task

**GET /tasks/{id}**

Retrieve a specific task by ID.

### 5. Update a Task

**PUT /tasks/{id}**

Update the title, status, or due date of a task.

### 6. Delete a Task

**DELETE /tasks/{id}**

Remove a task permanently.

---

## Error Handling

| Status Code | Meaning | Description |
|-------------|---------|-------------|
| 400 | Bad Request | Something is wrong with the data you sent. |
| 401 | Unauthorized | Your token is missing or invalid. |
| 404 | Not Found | The requested resource doesn't exist. |
| 500 | Server Error | Something went wrong on our end. |

---

## Rate Limiting

To prevent abuse, the API supports rate limiting. Headers include:

```
X-RateLimit-Limit: 100
X-RateLimit-Remaining: 75
X-RateLimit-Reset: 1615987200
```

---

## Try It Out

Use our interactive [Swagger UI](https://editor.swagger.io/) to test the API live using the OpenAPI spec (`openapi.yaml`).

---

## Final Notes

- All requests should use `application/json` as the Content-Type.
- Always authenticate before making calls to protected endpoints.
- This documentation pairs with the OpenAPI YAML spec to provide both human- and machine-readable reference.
