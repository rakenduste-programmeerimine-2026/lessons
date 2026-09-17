# Lesson #2: React: Group Learning Assignments

## Organisation

Our shared project is a **Task Tracker**. First, we build the React frontend.
Later, we build a Node.js backend and connect them.

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

## What Every Presenting Group Must Explain

1. What is your topic, and what problem does it solve?
2. What does the important syntax mean?
3. How does your working example behave?
4. What is one common mistake, and how do you fix it?
5. How does this concept help build our Task Tracker?

## Preparation and Homework

- Prepare your React presentation during the initial group preparation time.

## Shared Task Data

Use this data structure throughout both parts:

```js
const tasks = [
  { id: 1, title: "Learn JSX", completed: true },
  { id: 2, title: "Practise React state", completed: false },
  { id: 3, title: "Build a Node.js API", completed: false },
];
```

Each task has:

- `id`: a unique integer;
- `title`: a non-empty string;
- `completed`: a boolean.

---

# Part 1: React Fundamentals

## 1. React, Vite and Creating Your First Application

### Research and explain

- What is React?
- What is a component?
- What is Vite?
- What roles do Node.js and npm play when developing a React application?
- Explain `package.json`, `node_modules`, `index.html`, `src/main.jsx`
  and `src/App.jsx`.
- Explain the difference between installing dependencies and starting
  the development server.

### Demonstrate

Create a JavaScript React project:

```bash
npm create vite@latest task-tracker -- --template react
cd task-tracker
npm install
npm run dev
```

Change the main heading to `Task Tracker` and show the browser updating.

### Completion requirement

The project starts successfully and displays the heading.

## 2. Git Workflow, Commit Conventions and Prettier

### Research and explain

- `git status`, `git add`, `git commit` and `git push`.
- Why `node_modules` should not be committed.
- Why `package-lock.json` should be committed.
- Angular-style commit messages: `type: description`.
- Common types: `feat`, `fix`, `docs`, `style`, `refactor` and `chore`.
- Installing the Prettier VS Code extension and Prettier in the project.
- Setting Prettier as the default formatter and enabling format on save.
- `.prettierrc` and `.prettierignore`.
- The difference between Prettier formatting and ESLint checks.

### Demonstrate

Format a file using agreed rules, such as:

```json
{
  "semi": true,
  "singleQuote": true,
  "tabWidth": 2
}
```

Commit the change using a meaningful message:

```text
style: format task tracker components
```

### Completion requirement

Formatting can be checked with a project command. The repository contains
a formatter configuration and meaningful commits.

## 3. JSX, Components and Basic Styling

### Research and explain

- JSX versus HTML.
- Capitalised component names.
- Closing tags and using a single parent or Fragment.
- JavaScript expressions inside `{}`.
- `className` and importing CSS.
- Exporting and importing components.

### Demonstrate

Create and render:

- `Header`;
- `TaskCard`.

Use a CSS class to style a task card.

### Completion requirement

`App` renders components imported from separate files.

## 4. Props and Reusable Components

### Research and explain

- Passing data from parent to child.
- Receiving props with destructuring.
- Passing strings, booleans and objects.
- Why props are read-only.
- Using different data with the same component.

### Demonstrate

Create a named export:

```jsx
export function TaskCard({ task }) {
  // Render the supplied task.
}
```

Render two cards with different task objects.

### Completion requirement

Each card displays the supplied title and completion status.
The component must not change the supplied object.

## 5. Events, useState and Conditional Rendering

### Research and explain

- `onClick` and event-handler functions.
- The difference between passing and calling a function.
- State versus an ordinary variable.
- `useState` and its setter.
- Updating based on previous state.
- Calling Hooks at the top level of a component.
- Conditional rendering with `if`, a ternary expression and `&&`.

### Demonstrate

Build a small completion toggle that changes between:

- `Completed`;
- `Not completed`.

Use state to make the change visible.

### Completion requirement

Clicking the button updates the displayed status. Clicking again reverses it.

## 6. Lists, Keys and Filtering

### Research and explain

- Rendering task objects with `.map()`.
- Why React needs keys.
- Why stable task IDs are suitable keys.
- Filtering with `.filter()`.
- Keeping the filter choice in state.
- Calculating a filtered list from existing state instead of storing
  another copy of the list.

### Demonstrate

Display the supplied tasks and provide filters for:

- all tasks;
- completed tasks;
- incomplete tasks.

Display `No tasks found` when the filtered list is empty.

### Completion requirement

Each filter displays the correct tasks without changing the original data.

## 7. Controlled Forms and Validation

### Research and explain

- Controlled inputs: `value` and `onChange`.
- `event.target.value`.
- Handling `onSubmit`.
- `event.preventDefault()`.
- Connecting a label to an input.
- Trimming input and rejecting empty titles.
- Displaying validation feedback.

### Demonstrate

Create:

```jsx
export function TaskForm({ onAddTask }) {
  // Collect a title and call onAddTask with the trimmed title.
}
```

### Completion requirement

- Valid submission calls `onAddTask(trimmedTitle)`.
- Empty and whitespace-only titles are rejected.
- A successful submission clears the input.
- Pressing Enter submits the form.

## 8. Shared State and Adding, Updating and Deleting Tasks

### Research and explain

- Lifting state to a common parent.
- Passing data down and callback functions down.
- Why state arrays and objects must not be modified directly.
- Adding with spread syntax.
- Updating with `.map()`.
- Deleting with `.filter()`.
- Functional state updates.

### Demonstrate

Keep the task array in a shared parent and connect:

- `TaskForm`;
- the task list;
- each `TaskCard`.

Add, toggle and delete tasks.

Adapt `TaskCard` to receive `onToggle` and `onDelete` callbacks.
The card calls them with the task's ID.

### Completion requirement

All three actions update the visible list. New tasks receive unique integer
IDs, and existing task objects are not directly mutated.

## 9. React Router and Task Details

### Research and explain

- Client-side routing.
- Installing React Router and wrapping the application in a router.
- `Routes`, `Route`, `Link` and `NavLink`.
- `BrowserRouter` versus `HashRouter`.
- Dynamic routes and `useParams`.
- URL parameters are strings.
- Handling unknown routes and unknown task IDs.

### Demonstrate

Create routes for:

- `/`: home page;
- `/tasks`: task list;
- `/tasks/:taskId`: task details;
- `*`: page not found.

Use `HashRouter` for this project's GitHub Pages deployment.

### Completion requirement

Navigation works, task links open the correct details, and missing tasks
display a clear message.

Keep shared task state above the pages that need it.

## 10. useEffect, Loading Data and an API Service

### Research and explain

- What an API is.
- Fetching JSON with `fetch` and `async/await`.
- Checking `response.ok`.
- Using `useEffect` to synchronise with an external data source.
- Effect dependencies and cleanup.
- Avoiding repeated requests caused by incorrect dependencies.
- Loading, error, success and empty states.
- Keeping data-loading code in a service file.

### Demonstrate

For now, load `public/tasks.json` through:

```js
fetch(`${import.meta.env.BASE_URL}tasks.json`)
```

Create a named `getTasks` export in `src/services/taskApi.js`.
It must return a promise resolving to the task array.

Use a supplied starter for the effect, including cleanup that prevents an
outdated request from updating the UI.

### Completion requirement

The app displays loaded tasks and handles loading and failure.
Adding and editing tasks remains in memory for now; refreshing resets them.

Explain that next lesson the service will request the Node.js API instead.

## 11. Production Builds and GitHub Pages Deployment

### Research and explain

- Development versus production.
- `npm run build`, `dist` and `npm run preview`.
- Vite's `base` setting for a repository hosted on GitHub Pages.
- Deploying the build through GitHub Actions.
- Why `HashRouter` is useful on GitHub Pages.
- Why GitHub Pages cannot run the future Express backend.
- Frontend environment variables are visible to users and cannot hold secrets.

### Demonstrate

Build, preview and deploy the application using the provided workflow.

### Completion requirement

The deployed application loads, assets work, and refreshing a task details
URL works.

Explain where the frontend will get its backend URL during integration.

## 12. Reusable Layouts and the children Prop

### Research and explain

- Component composition.
- The `children` prop.
- Reusing a layout without repeating its markup.

### Demonstrate

Create:

```jsx
<PageSection title="My tasks">
  <TaskList />
</PageSection>
```

### Completion requirement

The component displays its title and any supplied children.
