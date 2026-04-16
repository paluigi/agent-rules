# 🐍 Python Development Standards

This instruction set defines the mandatory standards and architectural preferences for all **Python** development tasks.
---

### 1. Project Architecture & Tooling
* **Project Layout:** Always implement the **`src/` layout** (e.g., `src/project_name/`).
* **Dependency Management:** Use **`uv`** for all operations.
    * Add packages via `uv add <package>`.
    * Execute scripts and environments via `uv run`.
* **Linting & Formatting:** * Use **Ruff** for linting.
    * Use **Black** for code formatting.
    * Ensure both are run before finalizing code changes.
* **Secrets Management:** Use `python-dotenv`. Always load via `load_dotenv()` at the application entry point and never hardcode sensitive data.

### 2. Data Handling & Storage
* **Core Library:** Use **Polars** exclusively for tabular data handling. Do not use Pandas unless specifically instructed.
* **Persistence Rules:**
    * **Parquet:** Use for any dataset or result **≥ 10MB**.
    * **CSV:** Use only for small exports or results **< 10MB**.
* **Database Implementation:**
    * **Local:** Use `sqlite3` (with `aiosqlite` for async) or `tinydb`.
    * **Centralized:** Use PostgreSQL (async via `motor` or `asyncpg`) or MongoDB.
    * **Pattern:** Always implement an **Asynchronous Repository Pattern** using an Object-Oriented approach.

### 3. Coding Style & Paradigm
* **Programming Paradigm:** Strict **Object-Oriented Programming (OOP)**. Logic should be encapsulated in classes (Services, Repositories, Orchestrators).
* **Asynchronous Execution:** * Prefer `async/await` for all I/O, database, and network operations.
    * Use **FastAPI** for web or backend-focused projects.
    * Use standard **asyncio** for standalone scripts and data pipelines.
* **Typing & Validation:** * Apply **Type Hints** to all function signatures and class attributes.
    * Use **Pydantic** for creating data classes and models when structure validation or serialization is required.
    * Do not perform static type validation (e.g., mypy) unless explicitly requested.
* **"If a Python project uses the `flet` library, you must strictly follow the rules in `flet_rules.md`. Pay special attention to the v1.0 Service API (no overlay for FilePicker) and the mandatory UTC DatePicker workaround."**

### 4. Testing & Dependencies
* **Testing Framework:** Use **Pytest**. 
    * Generate test cases **only when explicitly requested** by the user.
* **Dependency Validation:** Any library not explicitly mentioned in these standards (uv, polars, dotenv, pydantic, fastapi, etc.) **must be proposed and validated** during the planning stage before installation or use.