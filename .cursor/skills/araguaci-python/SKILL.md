# Python Development Rules (Cursor) — Imported Skill

Source: `araguaci/cursor-skills` → `python/CURSOR.md` (imported manually).

## TESIS uchun adoptatsiya (MVP)
- TESIS backend: **Python + FastAPI**. Bu skill’dan faqat quyilarni “majburiy” deb olamiz:
  - type hints + aniq return type
  - input validation (Pydantic)
  - xavfsiz ishlov: input sanitize/validate
  - minimal, soddalashtirilgan project layout (bizda hozir `main.py`, `engine.py`, `weather.py`, `rag.py`, `explainer.py`, `models.py`)
- Django/Flask/DataScience bo‘limlari TESIS MVP uchun ikkinchi daraja.

---

# CURSOR IDE Rules for Python Development

## Overview
This document establishes rules and best practices for working with Python development in CURSOR IDE. It covers frameworks like Django, Flask, FastAPI, data science tools, and general Python development patterns.

## Environment Setup Rules

### CURSOR IDE Configuration
**MANDATORY Extensions:**
- Python (Microsoft Python extension)
- Pylance (language server)
- Python Debugger (debugging support)
- Python Docstring Generator (documentation)
- Python Indent (indentation)
- Python Test Explorer (testing)
- Jupyter (notebook support)

### Project Structure
**Standard Python Project Layout:**
```
project/
├── src/ (source code)
├── tests/ (test files)
├── docs/ (documentation)
├── requirements.txt
├── requirements-dev.txt
├── setup.py
├── pyproject.toml
└── .env
```

### FastAPI Development
**FastAPI-Specific Guidelines:**
- Follow FastAPI conventions (dependency injection)
- Use FastAPI's built-in features (Pydantic, OpenAPI)
- Implement proper async patterns
- Use FastAPI's testing framework
- Follow FastAPI's security best practices

## Code Quality Rules

### PEP Standards
**MANDATORY Compliance:**
- PEP 8: Style Guide for Python Code
- PEP 257: Docstring Conventions
- PEP 484: Type Hints
- PEP 526: Syntax for Variable Annotations

### Documentation Standards
**Documentation Requirements:**
- Docstrings for all functions and classes
- Type hints for all functions
- Inline comments for complex logic
- README files for projects
- API documentation for services

## Security Rules

### Input Validation
**Security Requirements:**
- Validate all user inputs
- Sanitize data before processing
- Use secure coding practices
- Implement proper authentication
- Follow OWASP guidelines

## Performance Optimization

### Code Optimization
**Performance Guidelines:**
- Use efficient algorithms
- Optimize database queries
- Implement caching strategies
- Use async/await appropriately
- Monitor performance metrics

