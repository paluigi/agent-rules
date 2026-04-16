# Flet (v1.0+) Development Standards

This instruction set is a mandatory guardrail for the Flet 1.0+ "Service-centric" API. It prevents legacy hallucinations and addresses known framework bugs.
---

### 1. The "Service" API (FilePicker, DatePicker, etc.)

- **Pattern:** These are now non-visual services called directly via `await`.
- **STRICT RULE:** **DO NOT** add `FilePicker`, `DatePicker`, or `BottomSheet` to `page.overlay` or use `page.add()`.
- **Implementation Example:**

```python
# Correct v1.0+ Usage
files = await ft.FilePicker().pick_files(allow_multiple=True)
```

### 2. DatePicker UTC Bug Workaround

- **The Issue:** DatePicker returns a datetime object in UTC. In timezones like CET (UTC+1), this often results in the "previous day" at 23:00.
- **Mandatory Logic:** Always use a helper to convert to local date before processing or displaying:

```python
def get_local_date(dt: datetime) -> date:
    """Handles Flet's UTC return value by converting to local timezone."""
    return dt.astimezone().date() if dt.tzinfo else dt.date()

# Usage:
picked_date = await ft.DatePicker().pick_date()
if picked_date:
    clean_date = get_local_date(picked_date)
```

### 3. Enum & Property Syntax (TitleCase)

- **Standard:** All enums and constants must be accessed via TitleCase classes.
- **Icons:** Use `ft.Icons.UPLOAD_FILE`, NOT `ft.icons.UPLOAD_FILE`.
- **Colors:** Use `ft.Colors.BLUE`, NOT `ft.colors.BLUE`.
- **Alignment:** Use `ft.MainAxisAlignment.CENTER`, NOT `ft.main_axis_alignment.CENTER`.
- **Keyboard:** Use `ft.KeyboardType.NUMBER`.

### 4. Packaging & Deployment

- **Tooling:** Use `uv` for dependency management.
- **Packaging:** Prefer `flet pack` over `flet build` to produce single-file executables.
- **CI/CD:** Utilize GitHub Actions to automate `flet pack` for Windows, macOS, and Linux. Ensure the workflow installs `uv` and syncs the environment before packing.

### 5. Application Architecture

- **Paradigm:** Strict Object-Oriented Programming (OOP). Create a class for the app with a `main()` method. Run the app by instantiating the class and calling `main()`:

```python
class MyApp:
    def __init__(self, page: ft.Page):
        self.page = page

    async def main(self):
        # Your app logic here
        await self.page.update_async()

if __name__ == "__main__":
    app = MyApp()
    flet.run(main=app.main)
```

- **Async:** UI event handlers and service calls MUST be `async def`.
- **State Management:** Use `ft.Ref[T]()` to reference controls within class-based views to maintain clean separation of concerns.
