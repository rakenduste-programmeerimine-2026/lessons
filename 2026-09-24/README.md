# Lesson #3: Node.js: Group Learning Assignments

## Questions After Presentations

The previous-numbered group asks the presenting group **two questions**.

With 12 groups:

- Group 12 asks Group 1.
- Group 1 asks Group 2.
- Group 2 asks Group 3.
- This continues until Group 11 asks Group 12.

Each member of the questioning group asks one question. Prepare questions
while listening. Questions must concern the presentation or demonstration.

Each presentation slot is approximately five minutes:

- 3½ minutes: explanation and demonstration;
- 1½ minutes: two questions, answers and switching groups.

## Work During the Independent Hour

Prepare your assigned Node.js topic with the same partner.

Suggested schedule:

Your draft must include:

1. A plain-language explanation.
2. A runnable example.
3. Instructions for running it.
4. One common mistake and its correction.
5. Its connection to the Task Tracker backend.

Use the provided starter for topics that depend on a running Express server.
You do not need to build earlier groups' examples before researching your topic.

## 1. What Node.js Is and Running JavaScript Outside the Browser

### Research and explain

- Node.js as a JavaScript runtime.
- Browser JavaScript versus server-side JavaScript.
- Why Node.js does not provide the browser's `document`.
- Why running a JavaScript file does not automatically create a web server.
- Checking Node.js and npm versions.

### Demonstrate

Create `index.js` and run:

```bash
node index.js
```

Print a greeting and the supplied task data.

### Completion requirement

The program runs in the terminal without using browser APIs.

## 2. npm, package.json and Project Scripts

### Research and explain

- Creating a project with `npm init -y`.
- Dependencies versus development dependencies.
- `package.json`, `package-lock.json` and `node_modules`.
- `npm install` versus `npm ci`.
- Creating and running npm scripts.
- Ignoring `node_modules` in Git.

### Demonstrate

Add a script that runs the application with:

```bash
npm start
```

### Completion requirement

Another student can install the project and run it using the README.

## 3. Modules and Reusable Task Functions

### Research and explain

- `"type": "module"` in `package.json`.
- Named exports and imports.
- Relative import paths and `.js` extensions.
- Separating data, processing functions and startup code.
- Returning values instead of only logging them.

### Demonstrate

Export these functions:

```js
getAllTasks(tasks)
getTaskById(tasks, id)
getCompletedTasks(tasks)
```

### Completion requirement

- Functions work with different arrays.
- Empty arrays are handled.
- An unknown ID returns `undefined`.
- The input data is not mutated.

## 4. HTTP, APIs and JSON

### Research and explain

- Client and server.
- Requests and responses.
- URL, path, query string, headers and body.
- `GET`, `POST`, `PATCH` and `DELETE`.
- Status codes: `200`, `201`, `204`, `400`, `404` and `500`.
- JavaScript objects versus JSON text.

### Demonstrate

Using a supplied local example, inspect a request and response.

Explain this planned request:

```text
GET /api/tasks/2
```

And its JSON response:

```json
{
  "id": 2,
  "title": "Practise React state",
  "completed": false
}
```

### Completion requirement

Identify the request method, URL, response status and response body.

## 5. Express and Your First API Route

### Research and explain

- What Express adds to Node.js.
- Installing Express.
- Creating an Express application.
- `req`, `res`, `res.json()` and `app.listen()`.
- Ports and localhost.
- Separating the exported app from the file that starts listening.

### Demonstrate

Create:

```text
GET /api/health
```

Returning:

```json
{ "status": "ok" }
```

### Completion requirement

Export `app` from `src/app.js`.
Start the server from `src/server.js`.
The health route returns status `200` and the expected JSON.

## 6. GET Routes, Route Parameters and Query Parameters

### Research and explain

- Reading a collection.
- `req.params` versus `req.query`.
- Converting strings to the intended data type.
- Why the string `"false"` is truthy in JavaScript.
- Handling a valid ID that does not exist.

### Demonstrate

Implement:

```text
GET /api/tasks
GET /api/tasks/:id
GET /api/tasks?completed=true
GET /api/tasks?completed=false
```

### Completion requirement

The routes return the correct data. Unknown task IDs return `404`.
An invalid `completed` query value returns `400`.

## 7. POST Routes, Request Bodies and Validation

### Research and explain

- Creating a resource with `POST`.
- `express.json()`.
- `Content-Type: application/json`.
- Reading `req.body`.
- Why the backend must validate data even if React already validates it.
- Generating IDs on the server.

### Demonstrate

Implement:

```text
POST /api/tasks
```

Accept:

```json
{ "title": "Learn Express" }
```

### Completion requirement

- Trim the title.
- Reject missing, non-string and whitespace-only titles with `400`.
- Assign a unique integer ID.
- Set `completed` to `false`.
- Return the created task with status `201`.

## 8. PATCH and DELETE Routes

### Research and explain

- Updating part of a resource with `PATCH`.
- Deleting a resource with `DELETE`.
- Looking up tasks by ID.
- Validating supplied fields.
- Why a `204` response has no body.

### Demonstrate

Implement:

```text
PATCH /api/tasks/:id
DELETE /api/tasks/:id
```

### Completion requirement

- PATCH accepts a valid title and/or boolean `completed`.
- PATCH returns the updated task with `200`.
- Invalid updates return `400`.
- Unknown task IDs return `404`.
- Successful DELETE returns `204` with no response body.
- A deleted task no longer appears in GET responses.

## 9. Middleware and Consistent Error Handling

### Research and explain

- What middleware is and why its order matters.
- `next()`.
- Request logging.
- Middleware for routes that do not exist.
- Express error-handling middleware.
- Validation errors versus unexpected server errors.

### Demonstrate

Use a consistent error response:

```json
{ "error": "Task not found" }
```

Add logging and demonstrate one handled error.

### Completion requirement

- Unknown API routes return JSON with `404`.
- Validation errors use `400`.
- Unexpected errors use `500` with a generic message.
- Responses do not expose stack traces to the client.

## 10. Connecting React to Node.js

### Research and explain

- Frontend and backend as separate processes.
- Different origins and why CORS may be needed.
- Configuring the allowed frontend origin on the backend.
- Vite environment variables and `VITE_API_URL`.
- Why deployed frontend code cannot use your computer's localhost.
- Why changing a frontend environment variable requires rebuilding
  the deployed frontend.
- Sending JSON with `fetch`.

### Demonstrate

Replace the frontend's local JSON loading with:

```text
GET /api/tasks
```

Then demonstrate creating a task with POST using a provided example.

### Completion requirement

- React loads tasks from Express.
- A submitted task reaches the backend.
- React uses the task returned by the server, including its ID.
- Requests go through `src/services/taskApi.js`.
- Request failures produce visible feedback.

## 11. Automated API Tests and Repeatable Test Data

### Research and explain

- What an API integration test checks.
- Vitest and Supertest.
- Checking status codes and response bodies.
- Testing valid and invalid inputs.
- Why tests must start with predictable data.
- Why `app` is exported separately from `app.listen()`.

### Demonstrate

Using a provided test setup, test:

- GET returns tasks;
- POST creates a valid task;
- POST rejects an empty title;
- an unknown task returns `404`;
- DELETE removes a task.

### Completion requirement

Tests can run automatically without manually starting a server.
Each test receives fresh data and does not depend on another test running first.

## 12. Saving Tasks to a JSON File

### Research and explain

- Why in-memory data disappears on restart.
- Reading and writing with `node:fs/promises`.
- `JSON.parse()` and `JSON.stringify()`.
- Handling a missing or invalid file.
- Why concurrent file writes need care.
- Why a database is preferable for a larger application.

### Demonstrate

Save tasks and load them again after restarting the program.

### Completion requirement

Tasks survive a restart. Tests use a temporary file rather than real user data.

## 13. Environment Variables and Backend Configuration

### Research and explain

- What is an environment variable?
- How does Node.js read values through `process.env`?
- Why are environment variable values strings?
- Why should configuration be separate from application logic?
- What is `.env.example`, and why should secrets stay out of Git?

### Demonstrate

Make these settings configurable:

- `PORT`: the server port, defaulting to `3000`.
- `TASKS_FILE`: the task data file path, defaulting to `./data/tasks.json`.

Use the teacher-provided environment-loading setup.

### Completion requirement

- The application works with the default settings.
- Changing `PORT` changes the server's port.
- Changing `TASKS_FILE` changes where tasks are saved and loaded.
- The README explains both settings.
- `.env.example` contains example configuration without secrets.

### Connection to our project

The same backend can run with different settings without editing its routes.

## 14. Handling Missing and Corrupted Data Files

### Research and explain

- Briefly recap `async`, `await` and `try/catch`.
- What is the difference between a missing file and invalid JSON?
- How can the error code `ENOENT` identify a missing file?
- Why should other errors not silently return an empty array?
- Why must corrupted data not be automatically overwritten?

### Demonstrate

Extend Topic 12's file-loading function:

loadTasks(filePath)

Demonstrate three situations:

1. A valid file containing a task array.
2. A file that does not exist.
3. A file containing invalid JSON.

### Completion requirement

- A valid task array is returned.
- A missing file returns an empty array.
- Invalid JSON produces a clear error.
- Valid JSON that is not an array produces a clear error.
- Other file errors are propagated instead of returning an empty array.
- Loading never creates, modifies or overwrites the file.

### Connection to our project

The backend handles missing data gracefully while reporting corrupted data
instead of silently discarding it.

## 15. Testing Saving and Loading with a Temporary File

### Research and explain

- Why should tests avoid the application's real data file?
- What is a temporary directory?
- Why must tests use their own data?
- Why should cleanup happen even when a test fails?

### Demonstrate

Use the teacher-provided testing setup and Topic 12's save/load functions.

Write one test that:

1. Creates a unique temporary directory.
2. Saves two tasks to a JSON file inside it.
3. Loads the tasks from that file.
4. Checks that the loaded tasks match the original tasks.
5. Removes the temporary directory afterward.

Use the teacher-provided cleanup code.

### Completion requirement

- The test runs automatically without starting the Express server.
- The loaded data matches the saved data.
- The test passes repeatedly.
- The application's real task file is never changed.
- Temporary files are removed even if an assertion fails.

### Connection to our project

Automated tests can verify persistence without affecting existing task data
or other test runs.
