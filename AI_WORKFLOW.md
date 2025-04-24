# 🧠 Working with AI Coding Assistants

This guide provides best practices for working with AI coding assistants to build production-quality software using this project template.

## 1. 🔑 Golden Rules

*   Use markdown files to manage the project (`README.md`, `PLANNING.md`, `TASK.md`).
*   Keep files under 500 lines. Split into modules when needed.
*   Start fresh conversations often. Long threads degrade response quality.
*   Don't overload the model. One task per message is ideal.
*   Test early, test often. Every new function should have unit tests.
*   Be specific in your requests. The more context, the better. Examples help a lot.
*   Write docs and comments as you go. Don't delay documentation.
*   Implement environment variables yourself. Don't trust the AI with API keys.
*   Don't ignore best practices.

## 2. 🧠 Planning & Task Management

Before writing any code, have a conversation with the AI to plan the initial scope and tasks for the project:

### `PLANNING.md`

*   **Purpose**: High-level vision, architecture, constraints, tech stack, tools, etc.
*   **Prompt to AI**:
    > "Use the structure and decisions outlined in `PLANNING.md`."
*   Have the AI reference this file at the beginning of any new conversation.

### `TASK.md`

*   **Purpose**: Tracks current tasks, backlog, and sub-tasks.
*   **Includes**: Bullet list of active work, milestones, and anything discovered mid-process.
*   **Prompt to AI**:
    > "Update `TASK.md` to mark XYZ as done and add ABC as a new task."
*   Can prompt the AI to automatically update and create tasks as well.

## 3. ⚙️ Global Rules (For AI IDEs)

Consider adding these rules to your AI IDE to enforce consistency:

```text
### 🔄 Project Awareness & Context
- **Always read `PLANNING.md`** at the start of a new conversation to understand the project's architecture, goals, style, and constraints.
- **Check `TASK.md`** before starting a new task. If the task isn't listed, add it with a brief description and today's date.
- **Use consistent naming conventions, file structure, and architecture patterns** as described in `PLANNING.md`.

### 🧱 Code Structure & Modularity
- **Never create a file longer than 500 lines of code.** If a file approaches this limit, refactor by splitting it into modules or helper files.
- **Organize code into clearly separated modules**, grouped by feature or responsibility.
- **Use clear, consistent imports** (prefer relative imports within packages).

### 🧪 Testing & Reliability
- **Always create unit tests for new features** (functions, classes, routes, etc).
- **After updating any logic**, check whether existing unit tests need to be updated. If so, do it.
- **Tests should live in a `/tests` folder** mirroring the main app structure.
  - Include at least:
    - 1 test for expected use
    - 1 edge case
    - 1 failure case

### ✅ Task Completion
- **Mark completed tasks in `TASK.md`** immediately after finishing them.
- Add new sub-tasks or TODOs discovered during development to `TASK.md` under a "Discovered During Work" section.

### 📎 Style & Conventions
- Follow established code style guidelines for your chosen language.
- Write **docstrings for every function**.

### 📚 Documentation & Explainability
- **Update `README.md`** when new features are added, dependencies change, or setup steps are modified.
- **Comment non-obvious code** and ensure everything is understandable to a mid-level developer.
- When writing complex logic, **add an inline `# Reason:` comment** explaining the why, not just the what.

### 🧠 AI Behavior Rules
- **Never assume missing context. Ask questions if uncertain.**
- **Never hallucinate libraries or functions** – only use known, verified packages.
- **Always confirm file paths and module names** exist before referencing them in code or tests.
- **Never delete or overwrite existing code** unless explicitly instructed to or if part of a task from `TASK.md`.
```

## 4. 🧩 Modular Prompting Process

For follow-up fixes or changes, focus on **one task per prompt** unless tasks are trivial:

*   **Good example:**
    > "Now update the `process_data` function to add a parameter for filtering the records."
*   **Bad example:**
    > "Update process_data to add filtering. Then I'm getting an error for the create_model function that says data format is wrong. Plus I need to add better documentation to the main function and in `README.md` for how to use this project."

## 5. ✅ Test After Every Feature

Ensure the AI writes unit tests after each feature, or do it yourself as a follow-up:

**Best practices for testing:**

*   Create tests in a `tests/` directory mirroring the app structure.
*   Always **mock** external service calls (DB, APIs, etc.) to avoid real interactions during tests.
*   For each function/feature, test at least:
    *   One successful scenario (happy path).
    *   One intentional failure (e.g., invalid input) to ensure proper error handling.
    *   One edge case (e.g., empty list, boundary values).
