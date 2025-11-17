# RAG Master Document

*(This file will be saved inside your project folder as a proper Markdown book. You can copy this entire document into `docs/RAG_MASTER_BOOK.md` so it stays version-controlled in GitHub and grows like a real book.)*

## 0. Foundations

* 0.1 What is RAG?
* 0.2 Why RAG exists (problem it solves)
* 0.3 How RAG works (high-level architecture)
* 0.4 Components of RAG (Loader → Chunker → Embedder → Retriever → Generator)
* 0.5 Tools & frameworks used (sentence-transformers, FAISS, etc.)

## 1. Project Setup

* 1.1 Create project folder structure
* 1.2 Create virtual environment
* 1.3 Install core dependencies
* 1.4 Create .gitignore
* 1.5 Initialize Git & GitHub
* 1.6 Create docs/ folder (documentation system)

## 2. Document Processing

* 2.1 PDF loading
* 2.2 Page extraction
* 2.3 Cleaning text
* 2.4 Chunking strategies

  * Character-based chunks
  * Token-based chunks (later)
  * Sentence-based chunks (later)
* 2.5 Testing text extraction + chunks
* 2.6 Documenting the processing pipeline

## 3. Embeddings

* 3.1 What embeddings are
* 3.2 Why embeddings are needed in RAG
* 3.3 Choosing an embedding model (sentence-transformers)
* 3.4 Embedding chunks
* 3.5 Embedding queries
* 3.6 Shape testing
* 3.7 Saving embeddings
* 3.8 Documenting embeddings

## 4. Vector Search / Retrieval

* 4.1 What is vector search?
* 4.2 Why FAISS exists
* 4.3 Building a FAISS index
* 4.4 Adding embeddings to FAISS
* 4.5 Searching top-K relevant chunks
* 4.6 Checking retrieval correctness
* 4.7 Saving & loading FAISS index
* 4.8 Documenting retrieval

## 5. RAG Pipeline (Backend Engine)

* 5.1 Putting all stages together
* 5.2 PDF → text → chunks → embeddings → index
* 5.3 Query → embed → retrieve → context
* 5.4 Handling edge cases
* 5.5 Logging queries
* 5.6 Designing a clean API function (e.g., `get_answer(query)`)
* 5.7 Documenting final RAG architecture

## 6. Frontend (Streamlit UI)

* 6.1 File uploader (PDF upload)
* 6.2 Running pipeline on uploaded PDF
* 6.3 Chat interface (question input)
* 6.4 Showing retrieved chunks
* 6.5 Displaying metadata (page number, score, etc.)
* 6.6 Adding a simple LLM (optional)
* 6.7 Polishing UI (colors, layout, header)

## 7. Advanced Topics (Optional Future Expansion)

* 7.1 Token-based chunking (with LLM tokenizer)
* 7.2 Multi-PDF retrieval
* 7.3 Storing FAISS index on disk
* 7.4 Using larger embedding models
* 7.5 Adding OpenAI / Claude / Llama as Generator
* 7.6 Adding caching
* 7.7 Adding reranking (colBERT / cross-encoders)
* 7.8 Evaluating RAG (precision, recall, grounding)

## 8. Documentation

* 8.1 TECH_STACK.md
* 8.2 SETUP_LOG.md
* 8.3 RAG_NOTES.md
* 8.4 RAG architecture diagram
* 8.5 Folder structure explanation
* 8.6 Future improvements list / TODO
