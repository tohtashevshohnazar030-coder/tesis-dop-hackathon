# API Development Rules (Cursor) — Imported Skill

Source: `araguaci/cursor-skills` → `api/CURSOR.md` (imported manually).

## TESIS uchun adoptatsiya (MVP)
- TESIS endpointlari: `POST /analyze`, `GET /health`.
- Bu skill’dan TESIS uchun keraklisi:
  - status code’lar, input validation, error response’lar
  - endpoint hujjatlash (FastAPI OpenAPI default yetarli)
  - xavfsizlik: request validate, SSRF/unsafe patterns yo‘q

---

# CURSOR IDE Rules for API Development

## Overview
This document establishes rules and best practices for working with API development in CURSOR IDE. It covers REST APIs, GraphQL, gRPC, and general API development patterns.

## Environment Setup Rules

### CURSOR IDE Configuration
**MANDATORY Extensions:**
- REST Client (API testing)
- Thunder Client (API testing)
- Postman (API testing)
- JSON Tools (JSON manipulation)
- API Documentation (documentation generation)
- Swagger Viewer (OpenAPI documentation)

### API Standards
**MANDATORY Requirements:**
- Follow REST principles
- Use proper HTTP status codes
- Implement API versioning
- Use JSON for data exchange
- Document API endpoints

## Security Rules

### Input Validation
**Security Requirements:**
- Validate all API inputs
- Sanitize data before processing
- Use secure coding practices
- Implement proper authentication
- Follow OWASP guidelines

## Error Handling Rules

### Exception Handling
**Error Management:**
- Implement custom error classes
- Log errors properly
- Handle errors gracefully
- Provide user-friendly messages

