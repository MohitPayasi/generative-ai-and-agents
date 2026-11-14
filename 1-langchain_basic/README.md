# 📚 1-LangChain Basic: RAG & Data Pipelines

This module covers the foundational building blocks of **Retrieval-Augmented Generation (RAG)** systems using **LangChain**. It focuses on data extraction, text chunking, embedding generation, vector stores, and retrieval techniques.

---

## 📌 Direct GitHub Notebook Links

Quickly access individual foundational notebooks:

| Module / Topic | Notebook / File | Core Concepts Covered | Key Libraries |
| :--- | :--- | :--- | :--- |
| **Document Loaders** | [`data_ingestion.ipynb`](./1.1open_ai/data_ingestion.ipynb) | `TextLoader`, `PyPDFLoader`, and `WebBaseLoader` for parsing documents | `pypdf`, `beautifulsoup4`, `langchain` |
| **Text Chunking** | [`data_spitter.ipynb`](./1.1open_ai/data_spitter.ipynb) | Fixed vs. recursive splitting with `chunk_size` and `chunk_overlap` | `langchain-text-splitters` |
| **OpenAI Embeddings** | [`open_ai_embedding.ipynb`](./1.1open_ai/open_ai_embedding.ipynb) | Dense vector extraction using `text-embedding-3-small` / `ada-002` | `langchain-openai` |
| **HuggingFace Embeddings** | [`hugging_face_embedding.ipynb`](./1.1open_ai/hugging_face_embedding.ipynb) | Open-source sentence-transformers (`all-MiniLM-L6-v2`) | `langchain-huggingface` |
| **ChromaDB Vector Store** | [`croma_vector_db.ipynb`](./1.1open_ai/croma_vector_db.ipynb) | Local persistent vector indexing & similarity queries | `chromadb` |
| **FAISS Vector Store** | [`faiss_vector_db.ipynb`](./1.1open_ai/faiss_vector_db.ipynb) | High-performance in-memory index creation and similarity scoring | `faiss-cpu` |
| **Ollama Local LLMs** | [`1.2ollama/README.md`](./1.2ollama/README.md) | Local offline RAG, offline embeddings & open-weight model serving | `langchain-community`, Ollama |

---

## 📂 Subdirectories

- **[`1.1open_ai/`](./1.1open_ai/)** — Comprehensive notebooks for document ingestion, text splitting, OpenAI & HuggingFace embeddings, and Chroma & FAISS vector databases.
- **[`1.2ollama/`](./1.2ollama/)** — Local model orchestration, offline embeddings, and local inference pipelines.

---

## 🛠️ Key Topics Implemented

1. **Document Ingestion (`data_ingestion.ipynb`)**:
   - Ingesting text files (`TextLoader`), PDF documents (`PyPDFLoader`), and web pages (`WebBaseLoader`).
   - Extracting raw text and preserving metadata.

2. **Text Splitting & Chunking (`data_spitter.ipynb`)**:
   - Understanding why chunking is required (context length limitations and retrieval relevance).
   - Comparing fixed-size splitting (`CharacterTextSplitter`) with structure-aware splitting (`RecursiveCharacterTextSplitter`).
   - Setting `chunk_size` and `chunk_overlap` effectively.

3. **Embeddings (`open_ai_embedding.ipynb` & `hugging_face_embedding.ipynb`)**:
   - Converting text chunks into high-dimensional dense vectors.
   - Using proprietary embeddings (OpenAI `text-embedding-3-small` / `ada-002`).
   - Using open-source local embeddings (HuggingFace `sentence-transformers/all-MiniLM-L6-v2`).

4. **Vector Databases (`croma_vector_db.ipynb` & `faiss_vector_db.ipynb`)**:
   - Creating local persistent vector stores with **ChromaDB**.
   - In-memory similarity search and indexing with **FAISS** (Facebook AI Similarity Search).
   - Executing top-k semantic similarity queries (`similarity_search`, `similarity_search_with_score`).

---

## 📦 Requirements & Installation

Dependencies are listed in [`requirement.txt`](./requirement.txt):

```bash
pip install -r requirement.txt
```

Key packages:
- `langchain`
- `langchain-community`
- `langchain-openai`
- `langchain-huggingface`
- `chromadb`
- `faiss-cpu`
- `pypdf`
