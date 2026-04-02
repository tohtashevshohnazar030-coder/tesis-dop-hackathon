# TESIS — Tech Context

## Stack (MVP)
- **Backend**: Python + FastAPI (single service)
- **Frontend**: single `index.html` (vanilla HTML/CSS/JS; no build step)
- **Weather**: Open-Meteo API
- **Vector store**: ChromaDB (local)
- **Embeddings**: Gemini Embedding API
- **Explanation LLM**: Gemini Flash (RAG context + deterministic decision factors)
- **Validation**: Pydantic
- **Linting**: Ruff
- **Hosting**: Render (GitHub auto-deploy)

## Local dev expectations
- Keep startup simple (single command).
- No Docker for MVP.
- `.env` is used for API keys; never commit it.

