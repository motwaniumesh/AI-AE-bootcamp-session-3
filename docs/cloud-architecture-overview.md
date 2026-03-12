# Cloud Architecture Overview

This monorepo runs as a simple full-stack application with a React frontend and an Express backend. The frontend sends HTTP requests to the backend API, and the backend stores task data in an in-memory SQLite database using `better-sqlite3`.

Because the database is in memory, data exists only for the lifetime of the backend process. There are no external cloud services, managed databases, or third-party integrations in the current architecture.

## System Context

```mermaid
flowchart LR
    user[User]
    frontend[React Frontend\npackages/frontend]
    api[Express API\npackages/backend]
    store[(In-Memory SQLite Store)]

    user -->|Uses browser UI| frontend
    frontend -->|HTTP /api/tasks| api
    api -->|Reads and writes tasks| store
```

## Sequence: Creating a TODO

```mermaid
sequenceDiagram
    actor User
    participant Frontend as React Frontend
    participant API as Express API
    participant Store as In-Memory SQLite Store

    User->>Frontend: Enter title, description, and optional due date
    User->>Frontend: Submit task form
    Frontend->>API: POST /api/tasks
    Note right of Frontend: Sends task data as JSON
    API->>API: Validate request body
    API->>Store: Insert task record
    Store-->>API: Return new task ID and stored row
    API-->>Frontend: 201 Created with new task JSON
    Frontend->>API: GET /api/tasks
    API->>Store: Query current task list
    Store-->>API: Return task rows
    API-->>Frontend: 200 OK with tasks JSON
    Frontend-->>User: Render updated TODO list
```