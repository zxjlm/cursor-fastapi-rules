---
description: FastAPI best practices and patterns for building modern Python web APIs
globs: **/*.py, app/**/*.py, api/**/*.py
---
# Python FastAPI Development Standards

## 1. Project Structure Standards

### 1.1 Directory Organization

- Ensure a clear project structure with the following directories separated:
  - `src/` or `app/` - Source code directory
  - `tests/` - Test code directory
  - `docs/` - Documentation directory
  - `config/` - Configuration files directory

### 1.2 Modular Design

- Implement modular design within the source code directory, organizing code into different files:
  - **models** - Data models and database models
  - **serializers** - Business logic layer
  - **routers** - API routes and controllers
  - **schemas** - DTO layer, defining data structures via Pydantic
  - **utils** - Utility functions and helper classes

## 2. Code Quality Standards

### 2.1 Code Style Consistency

- Use **Ruff** tool to enforce code style consistency
- Maintain a clean and uniform codebase style

### 2.2 AI-Friendly Coding Practices

To enhance code readability and AI-assisted development efficiency, follow these practices:

- **Descriptive Naming**: Use clear, descriptive variable and function names
- **Type Hints**: Add type hints for all function parameters, return values, and variables
- **Detailed Comments**: Provide detailed comments for complex logic
- **Rich Error Context**: Provide detailed context information in error handling for easier debugging

Example:

```python
from typing import List, Optional

def calculate_user_score(
    user_id: int,
    transactions: List[dict],
    bonus_multiplier: Optional[float] = None
) -> float:
    """
    Calculate user score
    
    Args:
        user_id: User ID
        transactions: List of transaction records
        bonus_multiplier: Optional bonus multiplier
        
    Returns:
        Calculated user score
        
    Raises:
        ValueError: When user_id is invalid or transaction records are empty
    """
    if not user_id or user_id <= 0:
        raise ValueError(f"Invalid user_id: {user_id}. Must be a positive integer.")
    
    if not transactions:
        raise ValueError(f"No transactions found for user_id: {user_id}")
    
    # Calculate base score
    base_score = sum(t.get('amount', 0) for t in transactions)
    
    # Apply bonus multiplier (if provided)
    if bonus_multiplier:
        base_score *= bonus_multiplier
    
    return base_score
```

## 3. Error Handling and Logging

### 3.1 Error Handling

- Implement robust error handling mechanisms
- Use FastAPI's exception handling middleware to handle exceptions uniformly
- Provide meaningful error messages and status codes for all exceptions

### 3.2 Logging

- Use the loguru module
- Log critical operations, errors, and debug information
- Include sufficient context information (such as user ID, request ID, timestamp, etc.)

## 4. Dependency Management

### 4.1 Dependency Management Tools

- Prioritize using **uv** ([GitHub](https://github.com/astral-sh/uv)) for dependency management
- Use virtual environments to isolate project dependencies
- Define project dependencies in `pyproject.toml`

### 4.2 Dependency Version Management

- Pin version numbers for major dependencies
- Regularly update dependencies to obtain security patches and new features
- Use dependency lock files to ensure environment consistency

## 5. Configuration Management

### 5.1 Environment Variables

- Manage configuration files in the `config/` directory
- Use environment variables to store sensitive information and environment-specific configurations
- Use `pydantic-settings` for configuration validation and management

## 6. Documentation Standards

### 6.1 Code Documentation

- Provide detailed docstrings for all public functions, classes, and modules
- Use Google or NumPy style docstring format
- Document parameters, return values, and possible exceptions

## 7. Testing Standards

### 7.1 Testing Framework

- Use **pytest** for comprehensive testing
- Test code should be located in the `tests/` directory

### 7.2 Test Coverage

- Write unit tests, integration tests, and end-to-end tests
- Ensure adequate test coverage for critical business logic
- Use pytest fixtures to manage test dependencies

### 7.3 Test Organization

- Test file naming: `test_*.py` or `*_test.py`
- Test function naming: `test_*`
- Use descriptive test names to explain test scenarios

## 8. FastAPI-Specific Best Practices

### 8.1 Route Organization

- Use APIRouter to organize related routes
- Group routes by functional modules
- Use route prefixes and tags to organize APIs

### 8.2 Dependency Injection

- Leverage FastAPI's dependency injection system
- Inject database connections, authentication, etc. as dependencies
- Use dependencies to share common logic

### 8.3 Data Validation

- Use Pydantic models for request and response validation
- Define clear input and output models
- Leverage Pydantic's validation features to ensure data integrity

### 8.4 Asynchronous Programming

- Prioritize using asynchronous functions for I/O operations
- Use `async`/`await` syntax
- Avoid using blocking operations in asynchronous contexts

### 8.5 Database and ORM

- Prioritize using SQLModel for ORM work, supplemented with SQLAlchemy for additional functionality
