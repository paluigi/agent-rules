# 📊 R Development Standards

This instruction set defines the standards for **R** development, prioritizing functional programming, tidy data principles, and strict environment isolation.
---

### 1. Environment & Version Management
* **Version Control:** Use **`rig`** to manage and switch between R versions if a specific version is required.
* **Project Isolation:** Use **`renv`** for all projects.
    * Always initialize with `renv::init()` if not present.
    * Use `renv::install("package")` for adding dependencies.
    * **Snapshotting:** After any package installation or removal, you must run `renv::snapshot()` to ensure the `renv.lock` file is current.
* **Granular Imports:** Do **not** use `library(tidyverse)`. Import only the specific component libraries needed (e.g., `library(dplyr)`, `library(ggplot2)`, `library(purrr)`, `library(tidyr)`).

### 2. Functional Programming (FP) Style
* **Paradigm:** Use a **Pure Functional** approach. Encapsulate logic in small, single-purpose functions. Avoid Object-Oriented (S3/S4/R6) approaches unless strictly necessary for a specific library.
* **Data Flow:** Use the **native pipe `|>`** for all data sequences. Avoid the `magrittr` pipe `%>%`.
* **Iteration:** Use the **`purrr`** family of functions (e.g., `map()`, `walk()`, `modify()`) or base R `lapply`/`sapply` for iteration. Avoid `for` loops as per global vectorization rules.
* **Side Effects:** Functions should return modified data rather than modifying objects in the global environment (avoid `<<-`).

### 3. Documentation & Code Quality
* **Function Documentation:** Every function must be documented using **`roxygen2`** style headers (e.g., `#' @param`, `#' @return`).
* **Style Guide:** Adhere strictly to the **Tidyverse Style Guide** (spacing, naming conventions like snake_case).
* **Data Handling:** Use **`dplyr`** for all data manipulation. Prefer `tibble` over standard `data.frame`.

### 4. Project Structure & Testing
* **Layout:** Implement the **`src/` layout**. 
    * `src/main.R` or `src/analysis.R` as the primary entry point.
    * `src/utils.R` or separate files in `src/functions/` for modular logic.
* **Testing:** Do not write tests by default. Use **`testthat`** only if explicitly requested by the user. 
* **Validation:** Any library not mentioned (e.g., `shiny`, `targets`, `sf`) must be proposed and validated in the `PLAN.md` during the planning stage.
