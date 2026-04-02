# Integrations Rules (Cursor) — Imported Skill

Source: `araguaci/cursor-skills` → `integrations/CURSOR.md` (imported manually).

## TESIS uchun adoptatsiya (MVP)
- TESIS integratsiyalari: **Open-Meteo**, **Gemini (embed + explain)**, **ChromaDB**.
- Bu skill’dan TESIS uchun keraklisi:
  - tashqi servislar bilan ishlashda timeout/retry
  - input/output validatsiya
  - xavfsizlik: SSRF’ga o‘xshash risklarni oldini olish

---

# CURSOR IDE Rules for Integrations Development

## Overview
This document establishes rules and best practices for working with system integrations in CURSOR IDE. It covers webhooks, microservices, databases, message queues, and general integration patterns.

## Integration Standards
**MANDATORY Requirements:**
- Use proper error handling
- Implement proper logging
- Use secure communication
- Follow integration best practices

## Database Integration
**Database-Specific Guidelines:**
- Implement proper connection pooling
- Use transactions
- Follow database's security best practices

## Security Rules
**Security Requirements:**
- Validate all integration inputs
- Sanitize data before processing
- Use secure coding practices
- Follow OWASP guidelines

