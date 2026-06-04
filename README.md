🎬 AI Video Assistant

Transcribe · Summarise · Chat with your meetings using AI

An end-to-end AI-powered pipeline that takes any YouTube URL or local video/audio file and automatically generates a full transcript, meeting summary, action items, key decisions, and enables RAG-based Q&A — all through a sleek Streamlit UI.

🖥️ Screenshots
Main Dashboard
Show Image
Pipeline Status & RAG Chat
Show Image

✨ Features

🎙️ Audio Transcription — OpenAI Whisper (local, no API cost)
🌐 Hinglish Support — Sarvam AI translates Hindi/Hinglish → English
📋 Auto Summary — Map-reduce summarization using Mistral LLM
✅ Action Items — Automatically extracted from transcript
🔑 Key Decisions — Identified and listed clearly
❓ Open Questions — Unresolved topics flagged for follow-up
💬 RAG Chat — Ask anything about your meeting using ChromaDB + HuggingFace
📥 Download Report — Export full report as .txt file
⏱️ Step Timing — See how long each pipeline stage took


🏗️ Architecture
YouTube URL / Local File
        ↓
 audio_processor.py     ← yt-dlp + pydub + ffmpeg
        ↓
  transcriber.py        ← Whisper (English) / Sarvam AI (Hinglish)
        ↓
  summarizer.py         ← Mistral LLM via LangChain (Map-Reduce)
  extractor.py          ← Action Items, Decisions, Questions
        ↓
  vector_store.py       ← ChromaDB + HuggingFace Embeddings
  rag_engine.py         ← LangChain LCEL RAG Pipeline
        ↓
    app.py              ← Streamlit UI

🛠️ Tech Stack
CategoryTechnologyTranscriptionOpenAI Whisper, Sarvam AILLMMistral AI (mistral-small-latest)OrchestrationLangChain LCELVector StoreChromaDBEmbeddingsHuggingFace all-MiniLM-L6-v2Audioyt-dlp, pydub, ffmpegUIStreamlitLanguagePython 3.11

⚙️ Setup & Installation
Prerequisites

Python 3.10+
FFmpeg installed and in PATH
Mistral AI API key → console.mistral.ai
(Optional) Sarvam AI API key for Hinglish → sarvam.ai

1. Clone the repository
bashgit clone https://github.com/YOUR_USERNAME/ai-meeting-assistant.git
cd ai-meeting-assistant
2. Create virtual environment
bashpython -m venv venv
venv\Scripts\activate        # Windows
# source venv/bin/activate   # Mac/Linux
3. Install dependencies
bashpip install -r Requirements.txt
4. Create .env file
envMISTRAL_API_KEY=your_mistral_api_key_here
WHISPER_MODEL=small
SARVAM_API_KEY=your_sarvam_api_key_here   # optional, for Hinglish
5. Run the app
bashstreamlit run app.py
Open http://localhost:8501 in your browser.

🚀 Usage

Paste a YouTube URL or local file path in the sidebar
Select language: English (Whisper) or Hinglish (Sarvam AI)
Click ⚡ Analyse
View the auto-generated Title, Summary, Action Items, Decisions, Questions
Use 💬 Chat to ask anything about the meeting
Click 📥 Download Report to save the full report


📁 Project Structure
ai-meeting-assistant/
│
├── app.py                  ← Streamlit UI
├── main.py                 ← CLI entry point
├── test.py                 ← Quick test script
├── Requirements.txt
├── .env                    ← API keys (not committed)
├── .gitignore
│
├── core/
│   ├── transcriber.py      ← Whisper + Sarvam AI
│   ├── summarizer.py       ← Map-reduce summarization
│   ├── extractor.py        ← Action items, decisions, questions
│   ├── rag_engine.py       ← LangChain RAG pipeline
│   └── vector_store.py     ← ChromaDB vector store
│
├── utils/
│   └── audio_processor.py  ← Audio download + chunking
│
└── assets/                 ← Screenshots for README

📝 Environment Variables
VariableRequiredDescriptionMISTRAL_API_KEY✅ YesMistral AI API keyWHISPER_MODEL❌ OptionalModel size: tiny/small/medium/large (default: small)SARVAM_API_KEY❌ OptionalOnly needed for Hinglish transcription

🙋 Author
Tarun Pawar
MCA — AI/ML Specialization | LNCT University, Bhopal
LinkedIn · GitHub
