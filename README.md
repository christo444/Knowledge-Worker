# Insurellm Expert Assistant

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
├── knowledge-base/              # Markdown source documents (not committed)
├── preprocessed_db/             # Persistent Chroma database (generated)
├── .env                         # Local API configuration (not committed)
└── requirements.txt
```

## Setup

1. Create and activate a Python virtual environment.
2. Install the dependencies:

   ```powershell
   python -m pip install -r requirements.txt
   ```

3. Configure the required provider credentials in `.env`.
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

The generated `preprocessed_db/` directory and local knowledge-base files are
ignored by Git because they are runtime data.
