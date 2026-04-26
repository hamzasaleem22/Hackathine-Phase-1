# Physical AI & Humanoid Robotics — Interactive Textbook Platform

A university-level educational platform covering Physical AI and Humanoid Robotics, featuring an interactive textbook built with Docusaurus and a RAG-powered chatbot for intelligent Q&A over course content.
<img width="1905" height="838" alt="Screenshot From 2026-04-26 20-42-30" src="https://github.com/user-attachments/assets/ad774acd-0fd7-4b11-a9e0-9627709aba4a" />

## 📖 Live Book

**[https://intellistack-app.netlify.app/](https://intellistack-app.netlify.app/)**

---

## Tech Stack

### Frontend
| Technology | Purpose |
|---|---|
| [Docusaurus 3.x](https://docusaurus.io/) | Static site generator (React-based, academic-optimized) |
| TypeScript 5.x | Type-safe configuration and components |
| MDX | Markdown + React components for rich content |
| GitHub Pages | Hosting & CDN deployment |
| `@docusaurus/theme-live-codeblock` | Interactive in-browser code playgrounds |
| `@docusaurus/theme-mermaid` | Architecture and flow diagrams |
| rehype-katex + remark-math | LaTeX math rendering |
| Jest + Cypress | Unit and end-to-end testing |

### Backend (RAG Chatbot)
| Technology | Purpose |
|---|---|
| [FastAPI](https://fastapi.tiangolo.com/) | Async Python API framework |
| OpenAI `gpt-4o-mini` | LLM for chatbot responses |
| OpenAI `text-embedding-3-small` | Semantic text embeddings |
| [Qdrant Cloud](https://qdrant.tech/) | Vector database for semantic search |
| [Neon Serverless Postgres](https://neon.tech/) | Chat history and analytics |
| SQLAlchemy + Alembic | ORM and database migrations |
| Vercel Serverless Functions | Python API hosting |

---

## Project Structure

```
.
├── frontend/               # Docusaurus textbook site
│   ├── docs/               # MDX course content (modules/chapters)
│   ├── src/                # Custom React components
│   ├── static/             # Images and static assets
│   └── docusaurus.config.ts
│
├── backend/                # FastAPI RAG chatbot
│   ├── api/
│   │   ├── main.py         # FastAPI entry point
│   │   ├── routes/         # API endpoints
│   │   ├── services/       # Business logic (RAG pipeline)
│   │   ├── models/         # Pydantic models
│   │   └── middleware/     # Rate limiting, CORS
│   ├── scripts/            # Content indexing utilities
│   ├── tests/              # Pytest test suite
│   └── db/                 # Schemas and Alembic migrations
│
├── specs/                  # Feature specifications and plans
└── history/                # Architecture Decision Records (ADRs)
```

---

## Getting Started

### Frontend

```bash
cd frontend
npm install
npm start          # Dev server at http://localhost:3000
npm run build      # Production build
```

### Backend

```bash
cd backend
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env   # Fill in API keys
uvicorn api.main:app --reload  # Dev server at http://localhost:8000
```

**Required environment variables** (see `.env.example`):
- `OPENAI_API_KEY` — OpenAI API key
- `QDRANT_URL` + `QDRANT_API_KEY` — Qdrant Cloud credentials
- `DATABASE_URL` — Neon Postgres connection string

---

## Course Modules

| Module | Topic |
|---|---|
| Module 0 | Introduction to Physical AI |
| Module 1 | ROS 2 — Architecture & Core Concepts |
| Module 2 | Gazebo & Unity Simulation |
| Module 3 | Humanoid Robotics Fundamentals |
| Module 4 | Perception & Sensor Fusion |
| Module 5 | Motion Planning & Control |
| Module 6 | End-to-End Capstone Project |

---

## Running Tests

```bash
# Frontend unit tests
cd frontend && npm test

# Frontend E2E tests
cd frontend && npm run test:e2e

# Backend tests
cd backend && pytest
```

---

## Deployment

- **Frontend** — auto-deployed to GitHub Pages via GitHub Actions on push to main
- **Backend** — deployed to Vercel Serverless Functions (`vercel.json` included)
