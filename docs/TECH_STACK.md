# Tech Stack – RAG Project

## 1. Environment & Tools

- **OS:** Ubuntu  
- **Editor:** VS Code  
- **Version Control:** Git + GitHub  
- **Python Version:** 3.12  
- **Environment Manager:** `venv` (virtual environment)

**Why `venv` (and not Conda)?**  
- Lighter and simpler for small projects  
- No extra 1–3 GB installation  
- Perfect for a single Python project with clear dependencies  

---

## 2. Core Python Libraries

### 🔹 torch
- **Package:** `torch`
- **Why:** Required backend for many deep learning / embedding models (CPU version only).
- **Used for:**  
  - Supporting models inside `sentence-transformers` and `transformers`.

### 🔹 sentence-transformers
- **Package:** `sentence-transformers`
- **Why:** Easy-to-use sentence and document embedding models.
- **Used for:**  
  - Converting text chunks into dense vector embeddings for retrieval.

### 🔹 transformers
- **Package:** `transformers`
- **Why:** Hugging Face library for modern NLP / LLM models.
- **Used for:**  
  - Loading encoder / LLM models if needed later.  
  - Extending beyond sentence-transformers (e.g. custom models).

### 🔹 langchain
- **Package:** `langchain`
- **Why:** High-level framework for building LLM / RAG workflows.
- **Used for:**  
  - (Later) chaining steps like: load → chunk → embed → retrieve → generate answer.

### 🔹 faiss-cpu
- **Package:** `faiss-cpu`
- **Why:** Fast similarity search library developed by Facebook/Meta.
- **Used for:**  
  - Storing embeddings in a vector index.  
  - Retrieving top-k most similar chunks for a query.

### 🔹 pypdf
- **Package:** `pypdf`
- **Why:** Pure Python library to read and extract text from PDFs.
- **Used for:**  
  - Loading user PDFs into raw text (used in `loaders.py`).

### 🔹 streamlit
- **Package:** `streamlit`
- **Why:** Quick way to build a simple web UI for Python apps.
- **Used for:**  
  - Creating the RAG app frontend (`app.py`) with file upload + chat interface.

### 🔹 numpy
- **Package:** `numpy`
- **Why:** Fundamental library for numerical arrays.
- **Used for:**  
  - Representing embeddings as arrays.  
  - Interfacing with FAISS.

### 🔹 pandas
- **Package:** `pandas`
- **Why:** Dataframes and basic data handling.
- **Used for:**  
  - (Optional) Logging interactions, experiments, or storing metadata.

---

## 3. Project Structure (High Level)

- `app.py` → Streamlit entry point (RAG UI).
- `src/loaders.py` → Functions to load documents (e.g. PDF).
- `src/chunker.py` → Functions to split text into chunks.
- `src/embedder.py` → Functions to create embeddings using sentence-transformers.
- `src/retriever.py` → Functions to build / query FAISS index.
- `src/rag_pipeline.py` → Orchestrates full RAG pipeline.

- `data/raw/` → Original documents (PDFs).
- `data/processed/` → Preprocessed artifacts (embeddings, indexes, etc.).
- `tests/` → Simple tests (e.g. import test).
- `docs/` → Documentation (this file, setup log, design notes, etc.).

---

## 4. External Services

Currently: **none** (fully local RAG).  
Future options (not used yet):
- OpenAI / Anthropic / other LLM APIs
- Vector DB services (e.g. Pinecone, Weaviate)

## Chunking

- **What it is:** Breaking long documents into smaller pieces (chunks).
- **Why:** LLMs and embeddings work better with shorter text; also many models have token limits.
- **How we do it in this project:** 
  - File: `src/chunker.py`
  - Function: `simple_chunk_text(text, chunk_size=500, chunk_overlap=100)`
  - Idea: move through text with overlap so context is not lost between chunks.

