# 🤖 Coding Agent Rules

A curated collection of opinionated instruction sets and coding standards for AI coding agents (like Kilo Code, Claude Code, Codex, etc.).

## 📖 The Problem

If you use AI coding assistants frequently, you quickly realize two things:
1.  **Context is expensive:** Re-typing "Don't use try/except blocks for control flow" or "Prefer composition over inheritance" in every new chat session is tedious.
2.  **Consistency is hard:** Without explicit guardrails, agents tend to drift towards "average" patterns or select libraries you don't prefer to use.

## 🚀 The Solution

This repository contains an opinionated set of Markdown files that act as a "System Prompt" or "Constitution" for my coding agents. They define the behavior, constraints, and stylistic preferences that I enforce across all my projects.

Instead of repeating myself, I simply provide the relevant Markdown files to the agent's context to ensure the AI adheres to my specific workflow.

## 📂 What is inside?

The rules are split into two categories:

### 1. Global Rules
These rules apply to *every* project, regardless of language. They define the "personality" and workflow of the agent.
*   **Behavior:** Ask clarification questions instead of speculating.
*   **Documentation:** Document work in detail; no "magic" fixes.
*   **Architecture:** Prefer simplicity but maintain structure.
*   **Workflow:** "Fail fast" during the exploration phase, then harden code afterwards for stability.

### 2. Language-Specific Rules
Opinionated technical instructions based on my preferred stack:
*   **Python:** Linting, typing, and idiomatic patterns.
*   **R:** Tidyverse conventions and data visualization.
*   **Rust:** Memory safety patterns and idiomatic crate usage.
*   **Quarto & LaTeX:** Document generation and typesetting standards.
*   **Web (HTML/CSS/JS):** Simplicity and modern standards.
*   **Flet:** Python-specific UI patterns to avoid issues with recent breaking changes.

## ⚙️ How to Use

There are several ways to use these files depending on your AI tool of choice:

**Option 1: Coding Agent Integration**
If you are using a coding agent, you can place the relevant `.md` files into a dedicated folder of your project or in a global directory to be applied to all projects.

**Option 2: System Prompts**
Copy and paste the content of the relevant Markdown files into the "System Prompt" or "Custom Instructions" section of your AI chat interface (ChatGPT, Claude, etc.).

**Option 3: Remote Instructions**
Many platforms allow you to define remote instructions. Simply point the tool to the files in this repo.

## 💡 Philosophy

These rules are **opinionated**. They reflect years of personal preference regarding code cleanliness, library choices, and architectural patterns.

*   **Simplicity First:** We don't need a factory pattern for a script that prints "Hello World."
*   **Stability Later:** While exploring a solution, code should be allowed to be messy and break often. Once the path is clear, we harden it.
*   **No Guesswork:** An agent should never assume it knows the requirement or your objectives. It should ask.

## 🤝 Contributing

While this repository primarily serves as a personal standard, I welcome discussions and improvements. If you see a rule that could be generalized or improved, feel free to open an Issue or a Pull Request.

If you find this useful, feel free to fork it and adjust the opinions to match your own stack and preferences!

## 📜 License

This project is open source. Feel free to use, modify, and distribute these rules as you see fit. (MIT License).
```
