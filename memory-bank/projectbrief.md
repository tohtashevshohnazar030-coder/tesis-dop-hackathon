# TESIS — Termiz Smart Irrigation System
## Project Brief for Cursor AI

---

## WHO I AM
I am the founder building this project. You are my technical co-founder, senior AI engineer, and system architect. You help me build, debug, and make architecture decisions. You do NOT overengineer. Every suggestion must pass this test: "Is this necessary for MVP?"

---

## THE PROBLEM

Farmers in Uzbekistan (focus: Surxondaryo region) currently irrigate based on:
- Fixed schedules
- Intuition and past experience

They do NOT use:
- Real-time soil moisture data
- Weather forecasts
- Crop-specific water needs

This leads to:
- 30–50% water waste
- Reduced crop yield
- Inefficient labor usage

---

## OUR SOLUTION — TESIS

TESIS (Termiz Smart Irrigation System) is an AI-powered irrigation decision engine.

A farmer opens a simple web page, enters 3 things:
- Crop type
- Location (region)
- Soil moisture level (manual input)

The system returns:
- Irrigate: YES or NO
- Water amount (liters)
- Duration (minutes)
- Confidence score
- Factor breakdown (soil / temp / rain)
- Plain-language explanation (why this decision)

We are NOT building hardware. We are NOT building IoT. We are building a decision engine with a web interface.

---

## TECHNICAL ARCHITECTURE

### Stack
- Backend: Python + FastAPI (single service, no microservices)
- Frontend: Vanilla HTML/CSS/JS (single index.html, no build step)
- Weather: Open-Meteo API (free, no API key, covers Uzbekistan)
- Vector DB: ChromaDB (local, free, Python-native)
- Embeddings: Gemini Embedding API (free tier)
- AI Explanation: Google Gemini Flash 2.0 (free tier, 1M tokens/month)
- Code Quality: Ruff (linter) + Pydantic (validation)
- Hosting: Render.com (free tier, auto-deploy from GitHub)

### File Structure

tesis/
├── main.py          # FastAPI app, /analyze endpoint
├── engine.py        # Rule-based scoring engine
├── weather.py       # Open-Meteo API integration
├── explainer.py     # Gemini Flash explanation + RAG context
├── rag.py           # ChromaDB setup, embedding, retrieval
├── models.py        # Pydantic schemas
├── crops.json       # Crop thresholds and parameters
├── knowledge/       # Agro documents for RAG
│   ├── irrigation_norms.txt
│   ├── crop_water_requirements.txt
│   └── climate_uzbekistan.txt
├── utils.py         # Helper functions
├── .env             # API keys
└── index.html       # Frontend

---

## CORE LOGIC — DECISION ENGINE

### Scoring model (engine.py)
The decision is deterministic and explainable. NOT made by AI.

```python
score = 0

if soil_moisture < crop["min_threshold"]:
    score += 2

if temperature > crop["critical_temp"]:
    score += 1

if rain_probability < 30:
    score += 2

irrigate = score >= 3
confidence = score / 5
```

### Output structure

```json
{
  "irrigation": true,
  "water_amount_liters": 120,
  "duration_minutes": 25,
  "confidence": 0.82,
  "factors": {
    "soil": "low",
    "temperature": "high",
    "rain": "none"
  },
  "explanation": "plain language here"
}
```

---

## RAG SYSTEM

### Why RAG?
The technical checkpoint requires the system to have its own trained/retrieved knowledge base. The system must read external agricultural documents, store them as vectors, and retrieve relevant knowledge before generating explanations.

### How it works
1. Agricultural documents (irrigation norms, crop water requirements, climate data) are stored in knowledge/ folder
2. At startup, documents are embedded using Gemini Embedding API and stored in ChromaDB
3. For every /analyze request, relevant chunks are retrieved from ChromaDB
4. Retrieved context is passed to Gemini along with the decision data
5. Gemini generates explanation based on BOTH the decision + domain knowledge

### RAG pipeline (rag.py)
- Load documents from knowledge/ folder
- Chunk text into segments
- Embed using Gemini Embedding API
- Store in ChromaDB collection
- On query: embed the input, find top-3 similar chunks, return as context

---

## API DESIGN

### Endpoint: POST /analyze

Input:

```json
{
  "crop": "cotton",
  "soil_moisture": 18,
  "lat": 37.2,
  "lon": 67.3
}
```

Output:

```json
{
  "irrigation": true,
  "water_amount_liters": 120,
  "duration_minutes": 25,
  "confidence": 0.82,
  "factors": {
    "soil": "low",
    "temperature": "high",
    "rain": "none"
  },
  "explanation": "Tuproq namligi past (18%), havo harorati yuqori (38°C), yaqin 24 soatda yomg'ir kutilmayapti. Sug'orish tavsiya etiladi."
}
```

### Endpoint: GET /health
Returns system status.

---

## WHAT AI DOES AND DOES NOT DO

AI does:
- Generate plain-language explanation of the decision
- Use retrieved agricultural knowledge as context
- Translate technical factors into farmer-friendly language

AI does NOT:
- Make the irrigation decision
- Override the rule engine
- Hallucinate — it only explains what the engine already decided

Key pitch line: "We separated decision intelligence from language intelligence."

---

## CROPS SUPPORTED (MVP)

- Cotton (Paxta)
- Wheat (Bug'doy)
- Tomato (Pomidor)
- Grape (Uzum)
- Corn (Makkajo'xori)

---

## FALLBACK BEHAVIOR

If Gemini API fails:

```python
def fallback_explanation(factors):
    return f"Tuproq namligi {factors['soil']} darajada. Havo harorati {factors['temperature']}. Yomg'ir: {factors['rain']}. Qaror: sug'orish tavsiya etiladi."
```

Demo must NEVER fail because of AI unavailability.

---

## FRONTEND BEHAVIOR

Single index.html:
- Form: crop selector, location (lat/lon or region dropdown), soil moisture slider
- Submit button with loading state
- Result card:
  - Big YES (green) / NO (red) decision
  - Water amount + duration
  - Confidence bar
  - Factor breakdown
  - AI explanation text
- "Why not irrigate?" reason shown when irrigation = false

---

## DEVELOPMENT WORKFLOW

- I work in Cursor using Memory Bank, Rules, and Skills
- Workflow: /van → /plan → /build → /reflect → /archive
- Every task starts with a plan, ends with a reflection
- GitHub → GitHub Desktop → Render.com (auto-deploy)
- No Docker for MVP
- No database — ChromaDB is local vector store only

---

## WHAT I NEED FROM YOU (CURSOR)

1. Help me build each file correctly and minimally
2. Debug errors with root cause + exact fix
3. Suggest better approaches only when necessary
4. Never overengineer
5. Always ask: "Is this necessary for MVP?"
6. Ensure everything works for a live demo

---

## JUDGING CRITERIA (Hackathon)

- Technical quality: clean code, real architecture, explainability
- Business value: water savings, scalability, real problem
- Domain relevance: agricultural context, Uzbekistan focus
- AI usage: proper use of AI (not AI for everything)

---

## PROJECT NAME
TESIS — Termiz Smart Irrigation System
Hackathon: National AI Hackathon, Uzbekistan
Timeline: 2–3 days MVP

