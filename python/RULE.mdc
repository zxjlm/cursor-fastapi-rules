---
globs: *.py
alwaysApply: false
---

# Python Programming Best Practices Guide

Key Principles

- Write concise, technical responses with accurate Python examples.
- Use functional, declarative programming; avoid classes where possible.
- Prefer iteration and modularization over code duplication.
- Use descriptive variable names with auxiliary verbs (e.g., is_active, has_permission).
- Use lowercase with underscores for directories and files (e.g., routers/user_routes.py).
- Favor named exports for routes and utility functions.
- Use the Receive an Object, Return an Object (RORO) pattern.

Python

- Use def for pure functions and async def for asynchronous operations.
- Use type hints for all function signatures. Prefer Pydantic models over raw dictionaries for input validation.
- File structure: exported router, sub-routes, utilities, static content, types (models, schemas).
- Avoid unnecessary curly braces in conditional statements.
- For single-line statements in conditionals, omit curly braces.
- Use concise, one-line syntax for simple conditional statements (e.g., if condition: do_something()).

## 1. Code Style and Readability

### 1.1 Naming Conventions

- Use clear, descriptive variable and function names
- Follow PEP 8 naming conventions:
  - `snake_case` for functions and variables
  - `PascalCase` for classes
  - `UPPER_CASE` for constants

### 1.2 Type Hints

- Add type hints for all function parameters, return values, and variables
- Use the `typing` module for complex types
- Enable static type checking with tools like mypy

### 1.3 Code Formatting

- Use **Ruff** tool to enforce code style consistency
- Maintain a clean and uniform codebase style
- Follow PEP 8 style guidelines

## 2. Error Handling and Validation

### 2.1 Prioritize Error Handling and Edge Cases

- Handle errors and edge cases at the beginning of functions
- Use early returns for error conditions to avoid deeply nested if statements
- Place the happy path last in the function for improved readability

### 2.2 Guard Clauses and Control Flow

- Avoid unnecessary else statements; use the if-return pattern instead
- Use guard clauses to handle preconditions and invalid states early
- Keep the main logic unindented and easy to follow

Example:

```python
def process_user_data(user_id: int, data: dict) -> dict:
    """Process user data with proper guard clauses."""
    
    # Guard clauses - handle errors early
    if not user_id or user_id <= 0:
        raise ValueError(f"Invalid user_id: {user_id}")
    
    if not data:
        raise ValueError("Data cannot be empty")
    
    if "email" not in data:
        raise ValueError("Email is required")
    
    # Happy path - main logic
    processed_data = {
        "user_id": user_id,
        "email": data["email"].lower(),
        "timestamp": datetime.now()
    }
    
    return processed_data
```

### 2.3 Error Logging and Messages

- Implement proper error logging with sufficient context
- Provide user-friendly error messages
- Use custom error types or error factories for consistent error handling
- Include relevant information in exceptions (IDs, values, context)

## 3. Documentation

### 3.1 Docstrings

- Provide detailed docstrings for all public functions, classes, and modules
- Use Google or NumPy style docstring format
- Document parameters, return values, and possible exceptions
- Add detailed comments for complex logic

## 4. Performance Optimization

### 4.1 Efficient Data Operations

- Use appropriate data structures for the task
- Avoid unnecessary iterations and copies
- Use generator expressions for large datasets
- Implement lazy loading techniques when appropriate

### 4.2 Caching

- Implement caching for expensive computations
- Use `functools.lru_cache` for function-level caching
- Consider external caching solutions (Redis, Memcached) for distributed systems

## 5. Testing

### 5.1 Test Framework

- Use **pytest** for comprehensive testing
- Write unit tests, integration tests, and end-to-end tests
- Ensure adequate test coverage for critical logic

### 5.2 Test Organization

- Test file naming: `test_*.py` or `*_test.py`
- Test function naming: `test_*`
- Use descriptive test names to explain test scenarios
- Use pytest fixtures to manage test dependencies

## 6. Dependency Management

### 6.1 Virtual Environments

- Always use virtual environments to isolate project dependencies
- Prioritize using **uv** for dependency management
- Define dependencies clearly in `pyproject.toml`

### 6.2 Version Management

- Pin version numbers for production dependencies
- Regularly update dependencies for security patches
- Use dependency lock files to ensure reproducibility
