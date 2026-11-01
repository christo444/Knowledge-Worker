# RAG Knowledge Worker

A retrieval-augmented generation (RAG) assistant that retrieves relevant
knowledge-base documents, reranks them, and uses them to answer questions in a
Gradio chat interface.

## Repository layout

```text
.
├── app.py                       # Gradio application entry point
├── rag/
│   ├── __init__.py
│   └── answer.py                # Retrieval, reranking, and answer generation
├── scripts/
│   ├── __init__.py
│   └── ingest.py                # Knowledge-base ingestion entry point
├── knowledge-base/              # Markdown source documents
├── preprocessed_db/             # Persistent Chroma database (generated)
├── .env                         # Local API configuration (not committed)
├── .env.example                 # Credential configuration template
└── requirements.txt
```

## Setup

1. Create and activate a Python virtual environment.
2. Install the dependencies:

   ```powershell
   python -m pip install -r requirements.txt
   ```

3. Copy `.env.example` to `.env` and configure your provider credentials.
4. Place Markdown documents in subfolders under `knowledge-base/`.

## Run

Build the persistent vector store from the knowledge base:

```powershell
python -m scripts.ingest
```

Start the chat application:

```powershell
python app.py
```

The generated `preprocessed_db/` directory and `.env` file are ignored by Git.
