---
applyTo: '**/*.cs'
---
# C# Coding Best Practices

## C#-Specific Guidelines
- Use `var` when the type is obvious; otherwise, specify the type explicitly.
- Prefer properties over public fields.
- Use `async` and `await` for asynchronous programming.
- Avoid using `dynamic` unless absolutely necessary.
- Use `nameof()` instead of hardcoded strings for member names.

## Formatting
- Use PascalCase for class names, methods, and properties.
- Use camelCase for local variables and parameters.
- Place opening braces on a new line (Allman style) or same line (K&R style), depending on team conventions.
- Indent consistently using 4 spaces.
- Group related members logically and use regions if necessary.

## Error Handling
- Use `try...catch` blocks to handle exceptions gracefully.
- Catch specific exceptions rather than using a general `Exception`.
- Avoid swallowing exceptions silently; log or rethrow as needed.
- Use `finally` to release resources or use `using` statements for automatic disposal.

## Performance
- Avoid unnecessary object allocations in performance-critical code.
- Use `StringBuilder` for string concatenation in loops.
- Minimize boxing and unboxing of value types.
- Prefer `foreach` over `for` unless indexing is required.

## Security
- Validate all user input to prevent injection attacks.
- Use parameterized queries with ADO.NET or ORM tools.
- Avoid storing sensitive data in plain text.
- Use secure coding practices when handling authentication and authorization.

## Maintainability
- Use meaningful and descriptive names for variables, methods, and classes.
- Keep methods short and focused on a single task.
- Write XML documentation comments for public APIs.
- Refactor duplicated code into reusable methods or classes.
- Organize code into namespaces and folders by feature or layer.

## Version Control
- Store all source code in version control.
- Use `.gitignore` to exclude build artifacts and user-specific files.
- Write clear and descriptive commit messages.
- Follow a branching strategy (e.g., Git Flow, trunk-based development).
