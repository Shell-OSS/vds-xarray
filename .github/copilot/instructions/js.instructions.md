---
applyTo: '**/*.js'
---
# JavaScript Coding Best Practices

## JS-Specific Guidelines
- Use `const` and `let` instead of `var`.
- Prefer arrow functions for anonymous functions.
- Avoid using global variables; encapsulate logic in modules or functions.
- Use strict equality (`===`) instead of loose equality (`==`).
- Avoid using deprecated or non-standard APIs.

## Formatting
- Use consistent indentation (e.g., 2 or 4 spaces).
- Place opening braces on the same line as the statement.
- Use semicolons consistently to terminate statements.
- Break long lines into multiple lines for readability.
- Group related code blocks logically and use whitespace to separate them.

## Error Handling
- Use `try...catch` blocks for error-prone operations.
- Always handle promise rejections with `.catch()` or `try...await`.
- Log meaningful error messages for debugging.

## Performance
- Avoid unnecessary DOM manipulations; batch updates when possible.
- Use event delegation for handling events efficiently.
- Minimize use of synchronous operations in asynchronous code.
- Avoid memory leaks by cleaning up event listeners and intervals.

## Security
- Never expose sensitive data (e.g., API keys) in client-side code.
- Validate and sanitize user input to prevent XSS and injection attacks.
- Use HTTPS for secure communication.
- Keep dependencies up to date to patch known vulnerabilities.

## Maintainability
- Use consistent naming conventions (e.g., camelCase for variables and functions).
- Write modular, reusable functions and components.
- Document complex logic with comments and JSDoc annotations.
- Avoid deeply nested code; refactor into smaller functions.

## Version Control
- Store all source code in version control.
- Use clear and descriptive commit messages.
- Follow branching strategies (e.g., Git Flow or trunk-based development).
