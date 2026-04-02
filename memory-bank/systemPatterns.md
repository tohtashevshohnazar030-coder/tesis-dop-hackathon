# TESIS — System Patterns

## Core principle
**Decision intelligence != language intelligence**
- **Decision**: deterministic, rule-based scoring engine (`engine.py`)
- **Explanation**: LLM generates plain-language output, constrained to the engine decision + retrieved agro context

## Request flow (MVP)
1. User submits crop + location + soil moisture
2. Backend fetches weather (Open-Meteo)
3. `engine.py` computes: irrigate yes/no + amounts + confidence + factor labels
4. `rag.py` retrieves top relevant agro chunks from local ChromaDB
5. `explainer.py` asks Gemini to explain the *already-made* decision using retrieved context
6. If Gemini fails: return fallback explanation (demo never fails)

## Minimal structure guidance (adopted from fastapi-templates skill)
Use only the parts that help MVP:
- Keep a **single FastAPI app** entry (`main.py`)
- Keep **Pydantic models** in `models.py`
- Keep **pure rule engine** in `engine.py`
- Keep **integrations** split by concern (`weather.py`, `rag.py`, `explainer.py`)
- Avoid heavy layers (repositories/services/auth) unless explicitly required by MVP scope

