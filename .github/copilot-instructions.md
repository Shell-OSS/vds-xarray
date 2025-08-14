# GitHub Copilot Instructions

This document provides guidelines for using GitHub Copilot effectively in your InnerSource project.

---

## Folder Structure
Ensure your project follows this structure:

```
project-root/
    ├── .github/
        ├── copilot/
            ├── config.json
            ├── prompts.md
            ├── instructions/
                ├── cs.instructions.md
                ├── js.instructions.md
                ├── py.instructions.md
                ├── sql.instructions.md
        ├── ISSUE_TEMPLATE/
            ├── bug_report.md
            ├── feature_request.md
        ├── PULL_REQUEST_TEMPLATE.md
    ├── src/                  # Application source code
    ├── tests/                # Unit and integration tests
    ├── docs/                 # Documentation (Markdown files)
    ├── scripts/              # Logs or automation scripts
    ├── README.md
    ├── CONTRIBUTION.md
    ├── CODEOWNER.md
    ├── CODE_OF_CONDUCT.md
    ├── LICENSE
    ├── sonar-project.properties
    ├── .gitignore
```

---

## Documentation Guidelines
- Use concise Markdown documentation.
- Add docblocks for functions with:
  - `@param` – Describe input parameters.
  - `@return` – Describe return values.
  - `@throws` – List exceptions.
  - `@author` – Add author information.

---

## Code Commenting Requirements

### General Commenting Standards
- Write clear, concise comments that explain **why**, not **what**.
- Use proper grammar and spelling in all comments.
- Keep comments up-to-date when code changes.
- Avoid redundant comments that simply restate the code.

### Inline Comments
- Use inline comments for complex logic or business rules.
- Explain algorithms, workarounds, or non-obvious implementations.
- Use TODO comments for future improvements: `// TODO: Optimize this algorithm for better performance`
- Use FIXME comments for known issues: `// FIXME: Handle edge case when input is null`

### File Headers
Include at the top of each source file:
```javascript
/**
 * File: filename.js
 * Description: Brief description of file's purpose
 * Author: Your Name
 * Created: YYYY-MM-DD
 * Last Modified: YYYY-MM-DD
 */
```

### Language-Specific Guidelines
- **JavaScript/TypeScript**: Use JSDoc format
- **Python**: Use docstrings with black format
- **C#**: Use XML documentation comments
- **Java**: Use Javadoc format
- **SQL**: Use `--` for single line, `/* */` for multi-line comments

---

## Unit Testing Requirements

### Coverage Standards
- **Minimum code coverage**: 80% for all new code
- **Target code coverage**: 90% or higher
- **Critical paths**: 100% coverage for security and business-critical functions
- Coverage reports must be generated and reviewed in CI/CD pipeline

### Testing Framework Guidelines
Choose appropriate testing frameworks based on your technology stack:

- **JavaScript/TypeScript**: Jest, Mocha, or Vitest
- **Python**: pytest, unittest, or nose2
- **C#**: NUnit, xUnit, or MSTest
- **Java**: JUnit 5, TestNG, or Mockito
- **SQL**: tSQLt, pgTAP, or database-specific testing tools


### Testing Best Practices
- **Unit Tests**: Test individual functions/methods in isolation
- **Integration Tests**: Test component interactions
- **Edge Cases**: Test boundary conditions, null values, empty inputs
- **Error Handling**: Test all error paths and exception scenarios
- **Mocking**: Use mocks for external dependencies (APIs, databases)
- **Test Naming**: Use descriptive test names that explain the scenario
- **Arrange-Act-Assert**: Follow the AAA pattern for test structure

### Coverage Configuration
Include coverage configuration in your project:

**For JavaScript/Jest:**
```json
{
  "jest": {
    "collectCoverage": true,
    "coverageThreshold": {
      "global": {
        "branches": 80,
        "functions": 80,
        "lines": 80,
        "statements": 80
      }
    },
    "coverageReporters": ["text", "lcov", "html"]
  }
}
```

**For Python/pytest:**
```ini
[tool:pytest]
addopts = --cov=src --cov-report=html --cov-report=term --cov-fail-under=80
```

### CI/CD Integration
- Run tests automatically on pull requests
- Fail builds if coverage drops below 80%
- Generate and store coverage reports
- Include coverage badges in README.md
- Block merges if tests fail or coverage is insufficient

### Test Documentation
- Document complex test scenarios
- Explain mock setups and data fixtures
- Include performance test requirements for critical paths
- Maintain test data in separate files or factories

---

## Security Best Practices
- Sanitize all user inputs.
- Use parameterized database queries.
- Enforce Content Security Policies (CSP).
- Implement CSRF protection.
- Use secure cookies (`HttpOnly`, `Secure`, `SameSite=Strict`).
- Apply role-based access control.
- Enable detailed logging and monitoring.

---

## Required Repository Contents
### 1. **README.md**
Include:
- Project description.
- Key functionalities and technologies.
- How to use and contribute sections.
- Reference to the license file.

### 2. **LICENSE**
Include a standard open-source license or company-specific copyright notice. Please use the below as standard.

```markdown
# *************************************************************************
#
# Shell Information Technology International B.V.
#
# Copyright (c) 2025 Shell Information Technology International B.V. All Rights Reserved.
#
# NOTICE: All information contained herein is, and remains the property of 
# Shell Information Technology International B.V. and its suppliers, if any.
# The intellectual and technical concepts contained herein are proprietary
# to Shell Information Technology International B.V. and its suppliers and
# may be covered by U.S. and Foreign Patents, patents in process, and are
# protected by trade secret or copyright law. Dissemination of this
# information or reproduction of this material is strictly forbidden unless
# prior written permission is obtained from Shell Information Technology
# International B.V..
# *************************************************************************
```

### 3. **CODE_OF_CONDUCT.md**
Outline expected behavior and reporting guidelines. Please use the below as standard.

```markdown
# Code of Conduct 

The Shell company Code of Conduct can be found on the page of the [Ethics-and Compliance Office](https://hub.shell.com/sitepage/369137/ethics-and-compliance-homepage?src=ess).
```

### 4. **CONTRIBUTION.md**
Provide:
- Contribution process overview.
- Steps for contributing.
- Quality management practices.

### 5. **SonarQube Integration**
- Add `sonar-project.properties` for code quality analysis.
- Include a SonarQube badge in the `README.md`.
- Ensure SonarQube scans are part of the CI/CD pipeline.

### 6. **Issue Templates**
Include templates under .github/ISSUE_TEMPLATE:
#### Bug Report

```markdown
---
name: Bug Report
about: Report a problem to help improve the project
title: "[Bug] <Brief description>"
labels: bug
---

## Description  
<!-- Clearly describe the issue, including expected vs. actual behavior -->  

## Steps to Reproduce  
1. Step one  
2. Step two  
3. …  

## Screenshots (if applicable)  
<!-- Add screenshots to illustrate the problem -->  

## Environment  
- OS: [e.g. Windows 10, macOS]  
- Version: [e.g. v1.0.0]  
- Browser: [if applicable]  

## Additional Notes  
<!-- Anything else you'd like to mention -->
```

#### Feature Request
```markdown
---
name: Feature Request
about: Suggest an idea for this project
title: "[Feature] <Brief description>"
labels: enhancement
---

## Summary  
<!-- Describe the feature and why it’s needed -->  

## Proposed Implementation  
<!-- How would this feature work? Provide details or examples -->  

## Alternatives Considered  
<!-- Other approaches you’ve thought about -->  

## Additional Notes  
<!-- Anything else you'd like to mention -->
```

#### Question
```markdown
---
name: Question / Discussion
about: Ask a question or start a discussion
title: "[Question] <Brief description>"
labels: question
---

## Topic  
<!-- What is your question or discussion point? -->  

## Context  
<!-- Provide background information or relevant details -->  

## Additional Notes  
<!-- Anything else you'd like to mention -->
```

### 6. **PULL_REQUEST_TEMPLATE.md**

Include the below pull request template under .github/:

```markdown
## Description  
<!-- Provide a short summary of the changes. Why are they necessary? -->  

## Related Issues  
<!-- Link to relevant issues or discussions. Example: Closes #123 -->  

## Changes Made  
- [ ] Feature added  
- [ ] Bug fixed  
- [ ] Refactoring  
- [ ] Documentation updated  

## Screenshots (if applicable)  
<!-- Add screenshots to clarify UI changes, if relevant -->  

## Checklist  
- [ ] Code follows project guidelines  
- [ ] Tests added and pass successfully  
- [ ] Documentation updated  
- [ ] Ready for review  

## Additional Notes  
<!-- Any other information reviewers should know -->  
```

---

## Using Copilot
- Enable Copilot in Visual Studio Code.
- Use inline suggestions to speed up coding.
- Review and edit suggestions for accuracy.
- Add comments to guide Copilot in generating better code.

---

## Additional Notes
- Ensure compliance with InnerSource Standards.
- Regularly update documentation and templates.
