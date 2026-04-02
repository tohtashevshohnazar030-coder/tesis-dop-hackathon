# CURSOR IDE Best Practices (General) — Imported Skill

Source: `araguaci/cursor-skills` → `CURSOR.md` (imported manually).

## TESIS uchun adoptatsiya (MVP)
- Bu skill **umumiy ish tartibi** uchun: format-on-save, lint/test odatlari, strukturani tartibli saqlash.
- TESIS’da `memory-bank/` har task’da “source of truth” bo‘lib qoladi.

---

# CURSOR IDE Best Practices - General Rules

## Overview
This document establishes general rules and best practices for working with CURSOR IDE across all programming environments. These guidelines ensure consistency, productivity, and quality in development workflows.

## Core Principles

### 1. Environment Setup
**MANDATORY Requirements:**
- Always configure CURSOR IDE for the specific programming environment
- Use appropriate extensions and plugins
- Set up proper linting and formatting
- Configure debugging tools
- Establish version control integration

### 2. Project Structure
**Standardized Approach:**
- Follow environment-specific conventions
- Use consistent naming patterns
- Organize files logically
- Maintain clear separation of concerns
- Document project structure

### 3. Code Quality
**Quality Standards:**
- Write clean, readable code
- Follow language-specific best practices
- Use consistent formatting
- Implement proper error handling
- Write meaningful comments

### 4. Development Workflow
**Process Guidelines:**
- Use version control effectively
- Implement proper testing
- Follow CI/CD practices
- Document changes
- Review code regularly

## General CURSOR IDE Configuration

### Essential Extensions
**Universal Extensions:**
- Git integration
- Language-specific syntax highlighting
- Code formatting tools
- Debugging support
- IntelliSense/autocomplete

### Settings Configuration
**Recommended Settings:**
```json
{
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll": true
  },
  "files.autoSave": "afterDelay",
  "editor.tabSize": 2,
  "editor.insertSpaces": true
}
```

## Security Considerations

### Code Security
**Security Practices:**
- Validate all inputs
- Use secure coding practices
- Handle sensitive data properly
- Implement proper authentication
- Regular security audits

