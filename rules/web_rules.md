# 🌐 Web & Frontend Standards

This instruction set defines the standards for lightweight, hypermedia-driven web development with a focus on zero-compilation workflows.
---

### 1. The Hypermedia Stack
* **Primary Interactivity:** Use **htmx** for all server-side communication (AJAX).
* **Secondary Client Logic:** Use **Alpine.js** only if a task cannot be handled by htmx (e.g., complex client-side toggles).
* **Paradigm:** Use HATEOAS; the server must return HTML fragments, not JSON.

### 2. Styling & Responsiveness (Zero-Build)
* **Framework:** Use **Bootstrap 5** via CDN for styling and responsiveness. 
* **Customization:** If custom CSS is needed, write it in a standard `style.css` file. Avoid CSS pre-processors (Sass/Less).
* **Icons:** Use **SVGs** directly in the HTML or via a simple image tag. Do not use icon fonts.

### 3. Templating & Static Hosting
* **Python Engine:** Use **Jinja2**.
* **Rust Engine:** Use **Tera** (to maintain syntax parity with Jinja2).
* **Static Assets:** All projects must be structured to be served by a static HTTP server. Organize files into a `static/` or `public/` folder.

### 4. JavaScript & TypeScript
* **Requirement:** Use JavaScript/TypeScript only when htmx/Alpine are insufficient.
* **Language:** Use **TypeScript**.
* **Note on Compilation:** Since TypeScript requires transpilation to run in the browser, the agent must provide a simple script (e.g., using `tsc` or `deno bundle`) to generate the final `.js` file, ensuring the output remains compatible with static hosting.
