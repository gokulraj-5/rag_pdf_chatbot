# 📄 RAG PDF ChatBot

An AI-powered Retrieval-Augmented Generation (RAG) chatbot that lets you upload one or multiple PDFs and chat with them using **Mistral AI**. Built with LangChain, ChromaDB, HuggingFace Embeddings, and Streamlit.

---

## 🚀 Features

- 📂 **Multi-PDF Support** — upload and chat across multiple documents simultaneously
- 🔎 **Per-document filtering** — restrict answers to a specific PDF
- 🧠 **Conversational memory** — follow-up questions work naturally across the chat
- 📝 **One-click summarization** — structured 5-section summary with PDF download
- ⚡ **Smart caching** — re-uploaded PDFs load instantly from saved vectorstore
- 🎯 **Source attribution** — every answer shows which file and page it came from
- 🌙 **Premium dark UI** — clean Streamlit interface with custom styling

---

## 🛠️ Tech Stack

| Layer | Tool |
|---|---|
| LLM | Mistral AI (`mistral-small-latest`) |
| Embeddings | HuggingFace `all-MiniLM-L6-v2` (CPU) |
| Vector DB | ChromaDB (local persistent) |
| RAG Framework | LangChain |
| PDF Loader | PyPDF + pdfplumber fallback |
| UI | Streamlit |
| PDF Export | fpdf2 |

---

## 📁 Project Structure

```
rag-chatbot/
├── app.py                 # Streamlit UI
├── rag_pipeline.py        # RAG logic — chunking, embeddings, chain, summarization
├── requirements.txt       # Python dependencies
├── .env                   # API keys (never commit this)
├── .gitignore
├── chroma_db/             # Auto-created — vector database storage
└── uploaded_*.pdf         # Auto-created — saved uploaded PDFs
```

---

## ⚙️ Setup & Installation

### 1. Clone the repository
```bash
git clone https://github.com/gokulraj-5/rag-chatbot.git
cd rag-chatbot
```

### 2. Create and activate virtual environment
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# Mac / Linux
source venv/bin/activate
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Set up your Mistral API key
Create a `.env` file in the project root:
```
MISTRAL_API_KEY=your_mistral_api_key_here
```
Get your free API key at [console.mistral.ai](https://console.mistral.ai)

### 5. Run the app
```bash
streamlit run app.py
```

Open your browser at `http://localhost:8501`

---

## 🧠 How It Works

```
PDF Upload
   │
   ▼
Chunking (400 + 1200 char multi-size)
   │
   ▼
HuggingFace Embeddings (CPU)
   │
   ▼
ChromaDB Vector Store (persisted to disk)
   │
   ▼
User Question → History-Aware Retriever → Top 8 Chunks
   │
   ▼
Mistral AI → Answer + Source Pages
```

---

## 📦 Requirements

```
langchain==0.3.25
langchain-community==0.3.23
langchain-mistralai==0.2.10
langchain-core==0.3.59
langchain-text-splitters==0.3.8
chromadb==0.5.23
sentence-transformers==4.1.0
pypdf==5.4.0
pdfplumber==0.11.4
streamlit==1.45.1
python-dotenv==1.1.0
fpdf2==2.8.3
```

---

## 🔑 Environment Variables

| Variable | Description |
|---|---|
| `MISTRAL_API_KEY` | Your Mistral AI API key (required) |

---

## 💡 Usage Tips

- Upload **multiple PDFs** at once to chat across all of them
- Use the **filter dropdown** in the sidebar to focus on one document
- Click **Summarize** for an instant structured overview of any document
- Previously uploaded PDFs **load instantly** from cache — no re-embedding needed
- Ask **follow-up questions** naturally — the chatbot remembers the conversation

---

## 🗺️ Roadmap

- [x] Single PDF Q&A
- [x] Multi-PDF support
- [x] Conversational memory
- [x] PDF summarization with download
- [x] Per-PDF caching
- [ ] Hybrid search (BM25 + vector)
- [ ] Re-ranking with cross-encoder
- [ ] OCR for scanned PDFs
- [ ] RAG evaluation with RAGAS
- [ ] Deploy to Streamlit Cloud

---

## 📄 License

MIT License — feel free to use, modify, and share.

---

## 🙋 Author

Built by **Gokulraj V**
- GitHub: [@gokulraj-5](https://github.com/gokulraj-5/)
- LinkedIn: [linkedin.com/in/gokulrajv5](https://www.linkedin.com/in/gokulrajv5/)
- Live Demo: [ragpdfchatbot-xpmjhrcvceyxo4nvyrpxhs.streamlit.app](https://ragpdfchatbot-xpmjhrcvceyxo4nvyrpxhs.streamlit.app/)