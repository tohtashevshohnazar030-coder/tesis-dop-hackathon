# Testing Rules (Cursor) — Imported Skill

Source: `araguaci/cursor-skills` → `testing/CURSOR.md` (imported manually).

## TESIS uchun adoptatsiya (MVP)
- TESIS demo tez chiqishi uchun testlar **minimal** bo‘ladi:
  - `engine.py` deterministik qaror (unit test)
  - `POST /analyze` uchun 1-2 ta “happy path” + 1 ta “Gemini fail → fallback” (integration test)
- Frontend E2E MVP’da shart emas.

---

# CURSOR IDE Rules for Testing Development

## Overview
This document establishes rules and best practices for working with testing strategies in CURSOR IDE. It covers unit testing, integration testing, end-to-end testing, and general testing patterns.

## Testing Standards
**MANDATORY Requirements:**
- Follow testing principles
- Implement proper test organization
- Follow testing best practices

## Testing Requirements
**Testing Standards:**
- Unit tests for core functionality
- Integration tests for workflows
- End-to-end tests for user journeys
- Test coverage minimum 80%

## Security Rules
**Security Requirements:**
- Validate all testing inputs
- Sanitize data before processing
- Use secure coding practices

