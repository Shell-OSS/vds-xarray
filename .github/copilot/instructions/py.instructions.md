---
applyTo: '**/*.py'
---
# Python Coding Best Practices

## Python-Specific Guidelines
- Follow PEP 8 — the official style guide for Python code.
- Use `is` for comparing with `None`, `True`, or `False`; use `==` for value comparisons.
- Prefer list comprehensions over `map()` and `filter()` for readability.
- Avoid using wildcard imports (`from module import *`).
- Use built-in functions and libraries where possible.

## Formatting
- Use 4 spaces per indentation level.
- Limit lines to 79 characters.
- Use blank lines to separate functions, classes, and logical sections.
- Place imports at the top of the file, grouped by standard library, third-party, and local modules.

## Error Handling
- Use `try...except` blocks to handle exceptions gracefully.
- Catch specific exceptions rather than using a bare `except`.
- Use `finally` or context managers (`with`) to manage resources like files or network connections.

## Performance
- Use generators for large data processing to save memory.
- Avoid using mutable default arguments in functions.
- Profile and optimize only when necessary; premature optimization can reduce readability.

## Security
- Avoid using `eval()` or `exec()` with untrusted input.
- Sanitize inputs when working with external data sources.
- Keep dependencies updated and use virtual environments.

## Maintainability
- Use meaningful variable and function names (e.g., `snake_case`).
- Write docstrings for all public modules, functions, classes, and methods.
- Break large functions into smaller, reusable ones.
- Use type hints to improve code clarity and tooling support.

## Version Control
- Store all scripts and modules in version control.
- Use `.gitignore` to exclude virtual environments, compiled files, and sensitive data.
- Write clear, concise commit messages that explain the "why" behind changes.
