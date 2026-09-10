# AI Video Assistant

A complete **AI Meeting Assistant** built from scratch in Python — a free, local-first alternative to paid tools like Otter.ai or Fireflies. It transcribes meetings, summarizes them, extracts action items and decisions, and lets you chat directly with your meeting content using RAG.

## Why This Project

Tools like Otter.ai and Fireflies charge recurring subscriptions for transcription and summarization — and most don't handle Hindi/Hinglish well. This project replicates and extends that functionality end-to-end using local and free-tier AI models, with no subscription cost.

## Features

- 🎥 **Flexible Input** — Accepts any YouTube URL or a local audio/video file
- 🗣️ **Multilingual Transcription** — English via local **Whisper AI**, Hindi & Hinglish via **Sarvam AI**
- 📝 **Meeting Summarization** — Condenses the full meeting into clear bullet points
- ✅ **Action Item Extraction** — Pulls out tasks with assigned owner and deadline
- 📌 **Key Decision Extraction** — Identifies and lists decisions made during the meeting
- ❓ **Open Questions & Follow-ups** — Surfaces unresolved discussion points
- 💬 **Chat With Your Meeting** — RAG-powered Q&A over the transcript using ChromaDB
- 📄 **Exportable Reports** — Download the full report as PDF or TXT

## How It Works (Pipeline Flow)

```
YouTube URL / Audio-Video File
            │
            ▼
    Transcription
  (Whisper - English | Sarvam AI - Hindi/Hinglish)
            │
            ▼
   LangChain LCEL Pipeline (Mistral AI)
            │
   ┌────────┼────────────┬───────────────┐
   ▼        ▼             ▼               ▼
Summary  Action Items  Key Decisions  Open Questions
            │
            ▼
   Embeddings (HuggingFace) → ChromaDB (Vector Store)
            │
            ▼
   RAG Chat Interface (Streamlit) + PDF/TXT Export
```

## Tech Stack

- **Python** — core language
- **OpenAI Whisper** (local, free) — English transcription
- **Sarvam AI** — Hindi & Hinglish transcription
- **LangChain LCEL** — modern chaining/pipeline framework
- **Mistral AI** (free API) — summarization, extraction, and chat reasoning
- **ChromaDB** — vector database for RAG
- **HuggingFace Embeddings** (local, free) — text embeddings for retrieval
- **Streamlit** — user interface

## Project Structure

| File / Folder | Description |
|---|---|
| `core/` | Core logic — transcription, summarization, extraction, and RAG pipeline |
| `utils/` | Helper functions used across the project (file handling, formatting, etc.) |
| `app.py` | Streamlit application — main UI entry point |
| `main.py` | Script entry point for running the pipeline outside the UI |
| `test.py` | Test cases for validating core functionality |
| `Requirements.txt` | Python dependencies |

## Getting Started

### 1. Clone the repo
```bash
git clone https://github.com/themaverick27/ai-video-assistant.git
cd ai-video-assistant
```

### 2. Install dependencies
```bash
pip install -r Requirements.txt
```

### 3. Add API keys
Create a `.env` file with the required keys (Sarvam AI, Mistral AI, and any other services used) before running the app.

### 4. Run the app
```bash
streamlit run app.py
```

Then open the local URL shown in your terminal, upload a file or paste a YouTube URL, and let it transcribe, summarize, and let you chat with your meeting.

## Key Learnings

- Building multilingual transcription pipelines with local and API-based models
- Structuring LangChain LCEL pipelines for multi-output tasks (summary, actions, decisions, questions)
- Implementing RAG from scratch with ChromaDB and HuggingFace embeddings
- Designing a practical, cost-efficient alternative to paid SaaS tools
- Exporting structured AI output into shareable report formats (PDF/TXT)

## Future Improvements

- Support for more languages beyond English/Hindi/Hinglish
- Real-time/live meeting transcription
- Integration with calendar tools to auto-fetch meeting recordings
---
**Author:** _Aniwesh Kumar_