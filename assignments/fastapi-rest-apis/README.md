# 📘 Assignment: Building REST APIs with FastAPI

## 🎯 Objective

Build a task-tracking REST API with FastAPI using HTTP methods, JSON request bodies, and meaningful response codes. Practice defining routes, validating data with Pydantic, and testing API behavior.

## 📝 Tasks

### 🛠️	Launch Your First API

#### Description
Create a project folder and a Python virtual environment, then install FastAPI with its standard dependencies using `python -m pip install "fastapi[standard]"`. Create `main.py` with a FastAPI application named `app`, start it with `fastapi dev main.py`, and open `http://127.0.0.1:8000/docs`.

#### Requirements
Completed program should:

- Start locally without errors using `fastapi dev main.py`.
- Provide a `GET /` endpoint that returns status `200` and the JSON object `{"message": "Task API is running"}`.
- Display the root endpoint in FastAPI's interactive documentation at `/docs`.

### 🛠️	Build Task CRUD Endpoints

#### Description
Implement create, read, update, and delete (CRUD) operations for tasks. Store tasks in memory using a list or dictionary; no database is required, and tasks may be cleared when the server restarts.

#### Requirements
Completed program should:

- Represent each task with an integer `id`, a string `title`, and a boolean `completed` field that defaults to `false` when a task is created.
- Accept a Pydantic request model containing `title` and optional `completed`, without requiring a client-provided `id`.
- Implement `POST /tasks` to assign a unique server-generated ID and return the created task with status `201`; do not reuse IDs after deletion during a server run.
- Implement `GET /tasks` to return all tasks as a JSON array, including an empty array when no tasks exist.
- Implement `GET /tasks/{task_id}` to return the task with the requested integer ID and status `200`.
- Implement `PUT /tasks/{task_id}` to replace an existing task's `title` and `completed`, requiring both fields and preserving its ID, and return the updated task with status `200`.
- Implement `DELETE /tasks/{task_id}` to remove a task and return status `204` with no response body.

Example creation request:

```http
POST /tasks
Content-Type: application/json

{"title": "Review Python functions"}
```

Example response with status `201`:

```json
{"id": 1, "title": "Review Python functions", "completed": false}
```

### 🛠️	Validate Requests and Handle Missing Tasks

#### Description
Use Pydantic constraints to reject invalid task data, and use FastAPI's `HTTPException` to report requests for tasks that do not exist.

#### Requirements
Completed program should:

- Require titles to contain at least one non-whitespace character and no more than 100 characters; apply the same validation to creation and replacement requests.
- Return status `422` for a missing required field, an invalid title, or a non-integer task ID in a URL.
- Return status `404` with a JSON `detail` message when reading, updating, or deleting a task ID that does not exist.
- Leave stored tasks unchanged when a request fails validation or targets a missing task.

### 🛠️	Test the API Workflow

#### Description
Use `/docs` to try the endpoints, then write automated tests in `test_main.py` using FastAPI's `TestClient`. Install the testing dependencies with `python -m pip install pytest httpx` and run your tests with `python -m pytest`.

#### Requirements
Completed program should:

- Pass a test that creates a task, lists tasks, retrieves the new task, replaces it, and deletes it, checking response codes and returned data at each step.
- Pass a test confirming that a deleted task returns `404` when requested again and that the deletion response has no body.
- Pass tests for a whitespace-only title, a title longer than 100 characters, a missing required field, and a non-integer task ID, each expecting `422`.
- Pass tests confirming that reading, updating, and deleting a missing task each return `404` with a `detail` message.
- Reset in-memory task storage between tests so tests do not depend on execution order.