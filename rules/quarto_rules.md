# 📘 Quarto & Hybrid Documentation Standards

This instruction set governs the creation of `.qmd` files and technical reports involving mixed-language (R/Python) environments.
---
### 1. Multi-Language Data Bridge
* **Reticulate (Small Data):** For datasets < 10MB, use the `reticulate` package to pass objects directly between engines (e.g., accessing Python objects in R via `py$obj_name`).
* **Parquet (Large Data):** For datasets ≥ 10MB, the Python chunk must save the data to a `.parquet` file, and the R chunk must read it using `arrow` or `nanoparquet`.
* **Standard:** Follow Python (OOP) standards for data processing and R (Functional) standards for visualization.

### 2. Tabular Output & Visualization
* **Python Tables:** Use the **`great_tables` (gt)** library for all tabular data produced in Python. 
* **R Tables:** Use **`kableExtra`** for styling. 
    * **STRICT RULE:** Never use the `gt` package in R due to documented Linux compatibility issues.
* **Graphics:** Use **ggplot2** for all figures and visualizations. 
* **Referencing:** * Every figure and table **must** have a unique label (`#| label: fig-...` or `#| label: tbl-...`).
    * Every figure and table **must** have a descriptive caption (`#| fig-cap: ...`).
    * Use modern Quarto cross-reference syntax (e.g., `@fig-label`) in the prose.

### 3. Execution & Styling
* **Cell Options:** Use the **`#|` (hash pipe)** syntax for all cell-level configurations.
* **Default Visibility:** Every `.qmd` file must include the following execution defaults in the document YAML or the first setup chunk:
    * `echo: false`
    * `warning: false`
    * `message: false`
* **Output Formats:** * **HTML:** Default to the **`darkly`** bootswatch theme.
    * **Word/PDF:** Use as requested. Ensure tables are formatted to be compatible with the target output (e.g., using `latex` or `markdown` formats in `kableExtra`).

### 4. Citations & Bibliographic Intelligence
* **Source:** Use the project's `.bib` file for all citations.
* **Summary Analysis:** The `.bib` file contains a `summary` field for each entry. 
    * You **must** read and reason over these summaries to select the most relevant citations for the context.
    * The summary text itself is metadata for the agent and **must never** appear in the rendered output.

### 5. Document Structure
* **Config:** Since projects usually contain only 1–2 `.qmd` files, specify the `echo` and `warning` policies at the top of each file rather than in a global `_quarto.yml`.
* **Readability:** Keep code blocks focused. If a data processing step is longer than 50 lines, move it to a supporting `.R` or `.py` script in the `src/` directory and source it.