# RAG Master Document

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



## 0.1 What is RAG?

Retrieval-Augmented Generation (RAG) is an AI technique that combines information retrieval with text generation.
Its purpose is to allow Large Language Models (LLMs) such as GPT, Claude, or Llama to produce accurate, factual, and context-aware responses using external knowledge sources.

In traditional AI systems, an LLM generates answers based only on what it learned during training.
It does not automatically know:

Your PDFs
Your company documents
Your notes
Any information added or updated after its training date

RAG solves this limitation by allowing the model to retrieve relevant information in real-time from external data and use it when forming responses.

## Simple Definition

RAG = Retrieve (find relevant information) + Generate (create an answer using that information).

It transforms a general-purpose language model into a customized expert that can answer questions using your specific data.

## Why This Matters

* Without RAG, an LLM:

guesses when it lacks information
hallucinates facts
cannot access your documents
cannot stay updated
cannot handle large volumes of text due to limited context windows

* With RAG, the model becomes:

accurate
grounded in real data
domain-specific
reliable for professional use
Analogy (Intuitive Explanation)

Think of the LLM as a very smart student who has strong general knowledge but has not read your textbook.
If you ask the student a question from your book, they may answer incorrectly because they are guessing.

RAG is like giving the student the exact page from the textbook before they answer your question.

* As a result:

The answer becomes grounded
The answer becomes factual
The answer is based on the actual document

Guessing disappears

* Where RAG Is Used

RAG is now a fundamental part of modern AI systems, used in:

PDF question-answering tools
Customer support chatbots
Internal enterprise knowledge assistants

Legal and medical document search
Research summarization tools
AI-powered search engines
Finance document analysis
Education and learning assistants

Companies such as Google, Amazon, Meta, Microsoft, IBM, and almost all startups use RAG in real products.


0.2 Why RAG Exists (The Problem It Solves)

Large Language Models are powerful, but they have a few natural limitations.
RAG was created to fix these limitations and make AI more accurate and useful in real-world tasks.

1. LLMs do not know your private or updated data

An LLM only knows what it learned during its training.
It does not automatically know:

your PDFs

your class notes

internal company documents

anything updated after its training date

So if you ask a question about your own file, a normal LLM cannot answer correctly.

2. LLMs hallucinate when they lack information

When an LLM doesn’t know something, it may “guess” confidently.
This is called hallucination.

RAG reduces hallucinations by giving the model the exact text from your documents before it answers.

3. LLMs cannot read long documents at once

Even the largest models have a limited context window (they can only read a certain number of tokens).

They cannot process an entire book, report, or PDF in one go.

RAG solves this by:

splitting documents into small chunks

embedding them

retrieving only the relevant chunks when you ask a question

This keeps the system efficient and grounded.

📌 Summary (Why RAG exists)

RAG exists because LLMs cannot access your data, cannot handle huge documents, and sometimes hallucinate.
RAG makes them accurate, grounded, and domain-specific.


