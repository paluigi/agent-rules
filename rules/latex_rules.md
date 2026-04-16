# 🎓 LaTeX & Academic Writing Standards

This instruction set governs the production of academic papers and Beamer presentations, specifically tailored for Economics and Statistics.
---

### 1. Bibliographic & Citation Style
* **Format:** Use **APA style** for all in-text citations and the bibliography.
* **Implementation:** Use the **`biblatex`** package with `style=apa`.
* **Intelligence:** You must read the `summary` field in the `.bib` file to ensure you are citing the correct work for the context.
    * **STRICT RULE:** The `summary` field is for your internal reasoning only. It must never be rendered in the final document.

### 2. Visuals & Tables (The "Journal Look")
* **Table Construction:** Use the **`booktabs`** package for all tables.
    * **STRICT RULE:** Do not use vertical lines.
    * Use `\toprule`, `\midrule`, and `\bottomrule`.
* **Alignment:** Align numerical data (coefficients, p-values) by the decimal point using the **`siunitx`** package (preferred) or `dcolumn`.
* **Captions & Labels:** * Every table and figure **must** have a descriptive caption and a unique label.
    * Always quote them in the prose using `Table~\ref{label}` or `Figure~\ref{label}`.

### 3. Mathematical Notation
* **Vectors & Matrices:** Use **bold** font for vectors and matrices (e.g., $\mathbf{\beta}$, $\mathbf{X}$).
* **Operators:** Use standard mathematical operators.
    * Use `\mathbb{E}[...]` for Expectations.
    * Use `\text{Var}(...)` for Variance.
    * Use `\text{P}(...)` or `\text{Pr}(...)` for Probability.
* **Display Math:** Always use `\[ ... \]` for standalone equations; never use the legacy `$$...$$`.

### 4. Writing Style & Tone
* **Journal Voice:** Write with the tone of a **top-tier Economics/Statistics journal**.
* **Directness:** Use the **Active Voice** (e.g., "We estimate..." instead of "It is estimated...").
* **Clarity:** Avoid flowery or pompous language. Be rigorous and precise. State the result clearly, then follow with the technical evidence.
* **Consistency:** Ensure notation is consistent across the paper and any accompanying slides.

### 5. Beamer Presentations
* **Theme:** Default to the **Metropolis** theme (`\usetheme{metropolis}`).
* **Cognitive Load:** One main idea per slide.
* **Overlays:** Use sequential reveals (e.g., `\pause`) to prevent the audience from reading ahead during complex explanations.