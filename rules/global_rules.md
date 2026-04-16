# 🌍 Global Agent Instructions

These standards apply to all programming languages, environments, and projects handled by the agent.
---
### 1. Communication & Ambiguity (CRITICAL)
- **Zero Speculation:** If an instruction is ambiguous or lacks detail, do not guess. Stop immediately and ask for clarification.
- **Pre-Plan Inquiry:** Before drafting the `PLAN.md`, ask as many clarifying questions as necessary to build a solid common understanding of the goals.
- **Active Dialogue:** If a decision point or technical roadblock arises during implementation, do not speculate on the "preferred way." Stop and ask for directions.
- **Minimalism:** Avoid conversational filler. Once clarity is achieved, move straight to the technical task.

### 2. Workflow & Planning
- **Mandatory Planning:** Unless explicitly instructed to skip, always generate or update a `PLAN.md` file before starting a task.
- **Discovery First:** Before asking the user for context, use terminal tools (`ls -R`, `grep`, `cat`, `find`) to orient yourself.
- **Documentation:** Maintain a `README.md` as a living document. Every edit or new feature must be reflected immediately.
- **Changelog:** Maintain a "Change Log" section at the end of the `README.md`. Entries should be concise and usable as commit messages.

### 3. Architectural Philosophy
- **Structure:** Always implement the **`src/` layout**, even for simple projects.
- **Consolidation:** Avoid module sprawl. Keep logic consolidated within as few files as possible until complexity strictly necessitates a split.
- **Performance:** Favor vectorized operations over manual loops.
- **Memory Efficiency:** For datasets exceeding 500MB, prefer lazy-loading, streaming, or chunked processing.

### 4. Coding Style & Quality
- **Idiomatic Code:** Strictly adhere to the best practices and "Zen" of the language in use (e.g., PEP 8 for Python).
- **Comments:** Use limited, high-impact inline comments to explain the "Why," not the "What."
- **Paradigm:** Prefer Object-Oriented Programming (OOP) to encapsulate state and behavior.

### 5. Error Handling & Logging
- **Development Phase (Fail Fast):** During initial implementation, allow exceptions to propagate to uncover edge cases quickly.
- **Maturation Phase:** Transition to graceful handling and clear logging only when directed by the user to "harden" the code.
- **Logging Style:** Keep logs concise and focused on high-level state changes.

### 6. Dependency Policy
- **Validation:** Any library or tool not explicitly approved in language-specific rules must be proposed and validated during the planning stage.