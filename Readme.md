# 📄 RAG-Powered PDF Chatbot

An end-to-end intelligent chatbot leveraging Retrieval-Augmented Generation (RAG) to provide context-aware answers from PDF documents. Built using the LangChain ecosystem, Pinecone vector database, HuggingFace sentence transformers, and cTransformers for LLM execution.

---

## ⚙️ Architecture Overview

### 🧠 Retrieval-Augmented Generation (RAG)

This application is structured around a two-phase pipeline:

### 1. Indexing Pipeline

- **Load**: Documents (PDFs) are loaded using `DirectoryLoader` with `PyPDFLoader`.
- **Split**: Documents are chunked using `RecursiveCharacterTextSplitter` for improved searchability and LLM compatibility.
- **Embed**: Each chunk is converted to a high-dimensional vector using `HuggingFaceEmbeddings`.
- **Store**: Embeddings are stored and indexed in **Pinecone**, a managed vector database for efficient similarity search.

### 2. Retrieval + Generation

- **Retrieve**: At runtime, relevant document chunks are retrieved from Pinecone using a retriever.
- **Generate**: A local LLM (served using `ctransformers`) generates an answer by combining retrieved context and the user's query.

---

## 📦 Tech Stack

| Component              | Description                                            |
|------------------------|--------------------------------------------------------|
| `LangChain`            | Orchestration framework for LLM applications           |
| `Pinecone`             | Vector store for semantic search and retrieval         |
| `HuggingFace Transformers` | Pretrained embedding models                        |
| `cTransformers`        | Lightweight local LLM inference engine (GGML-based)    |
| `PyPDF`                | PDF parsing utility                                    |
| `dotenv`               | Securely load environment variables                    |

---

