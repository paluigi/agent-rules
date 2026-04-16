# 🦀 Rust Development Standards

This instruction set defines the standards for **Rust** development, focusing on high-performance CLI tools, GUI applications, and AI Agent orchestration frameworks.
---

### 1. Tooling & Environment
* **Build System:** Use **Cargo** for all project management and builds.
* **Workflow:** After every code edit, you **must** run:
    1. `cargo fmt` to ensure standard formatting.
    2. `cargo clippy` to catch idiomatic mistakes and potential bugs.
* **Async Runtime:** Use **Tokio** as the standard asynchronous runtime for all I/O, networking, and concurrent agent tasks.
* **Dependencies:** Use `cargo add <crate>` to manage the `Cargo.toml`.

### 2. Architecture (Trait-Based OOP)
* **Paradigm:** Implement Object-Oriented patterns using **Structs** and **Traits**.
    * Use **Traits** to define shared interfaces (e.g., `Agent`, `Tool`, `Repository`).
    * Favor **Composition over Inheritance** to build complex systems.
* **State Management:** Use `Arc<Mutex<T>>` or `Arc<RwLock<T>>` when state needs to be shared across async tasks in your orchestration frameworks.
* **Standard Layout:** Always use the standard Cargo layout (`src/main.rs`, `src/lib.rs`, `src/bin/`).

### 3. Error Handling (Fail Fast to Hardened)
* **Development Phase (Fail Fast):** Use the **`anyhow`** crate for flexible, context-rich error handling and the `?` operator for easy propagation.
* **Hardening Phase:** When transitioning to a "Stable" status, refactor critical errors to use the **`thiserror`** crate for defined, structured, and exhaustive error types.
* **Panic Policy:** Avoid `unwrap()` and `expect()` in production code. During the "Fail Fast" phase, `expect("clear reason")` is allowed to help debug, but must be refactored later.

### 4. Memory & Performance
* **Ownership:** Follow strict ownership and borrowing principles. Do not "over-clone" to bypass the borrow checker. If a lifetime issue arises, stop and ask the user for architectural guidance.
* **Vectorization:** Prefer iterator patterns (`.map()`, `.filter()`, `.collect()`) for data processing.
* **Unsafe Code:** **STRICT RULE:** Do not use `unsafe` blocks unless there is a documented, unavoidable performance requirement.

### 5. AI Agent Orchestration Specifics
* **Serialization:** Use **Serde** for all JSON/YAML data handling and configuration.
* **Validation:** Any crate not inherently part of the "core" stack (e.g., `reqwest`, `sqlx`, `egui`, `clap`) must be proposed and validated during the planning stage.