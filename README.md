# 🧠 AI Engineering & LLM Systems: LangChain, LangGraph & Machine Learning

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![LangChain](https://img.shields.io/badge/🦜🔗_LangChain-0.3+-darkgreen.svg)](https://python.langchain.com/)
[![LangGraph](https://img.shields.io/badge/🕸️_LangGraph-StateGraph-orange.svg)](https://langchain-ai.github.io/langgraph/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-teal.svg)](https://fastapi.tiangolo.com/)
[![Scikit-Learn](https://img.shields.io/badge/scikit--learn-F7931E?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

> A modular, hands-on repository containing production-grade architectures, agentic workflows, declarative LCEL pipelines, RAG systems, and fundamental Machine Learning algorithms.

---

## 📑 Table of Contents

- [🗂️ Repository Architecture](#️-repository-architecture)
- [🧩 Modules Overview](#-modules-overview)
  - [1. LangChain Fundamentals (`1-langchain_basic/`)](#1-langchain-fundamentals-1-langchain_basic)
  - [2. End-to-End RAG, LCEL & Modern LangChain (`langchain_langgraph/`)](#2-end-to-end-rag-lcel--modern-langchain-langchain_langgraph)
  - [3. Agentic Systems with LangGraph (`langraphproject/`)](#3-agentic-systems-with-langgraph-langraphproject)
  - [4. Advanced LangChain Features (`project/`)](#4-advanced-langchain-features-project)
  - [5. API Serving & Deployment (`practice/`)](#5-api-serving--deployment-practice)
  - [6. Machine Learning Foundations & Industry Projects (`Machine_learning/`)](#6-machine-learning-foundations--industry-projects-machine_learning)
- [⚡ Quick Start & Setup](#-quick-start--setup)
- [🔑 Environment Variables](#-environment-variables)
- [🛠️ Tech Stack](#️-tech-stack)
- [👤 Author](#-author)

---

## 🗂️ Repository Architecture

```text
mohit_payasi/
├── 1-langchain_basic/          # Fundamentals: Ingestion, Chunking, Embeddings & Vector DBs
│   ├── 1.1open_ai/             # Chroma, FAISS, OpenAI & HuggingFace Embeddings
│   ├── 1.2ollama/              # Local LLMs & Embeddings via Ollama
│   └── README.md
│
├── langchain_langgraph/        # End-to-End RAG, Embeddings, Ingestion, LCEL & Agents
│   ├── introduction/           # Document Ingestion, HF Embeddings & LangGraph Memory
│   ├── section_6/              # Production RAG pipeline with Groq LLM & FAISS
│   ├── section_7/              # Declarative LCEL Chains & LangServe REST Deployment
│   ├── section_8/              # Stateful Chatbots with Conversation History & Trim Messages
│   ├── section_10/             # Modern LangChain: Dynamic Models, Messages, Tools, Structured Output & Agents
│   └── README.md
│
├── langraphproject/            # Production Agent Systems built with LangGraph
│   ├── basic_chat/             # StateGraph Nodes, Observability & Supervisor Multi-Agent System
│   ├── main.py                 # Standalone StateGraph Agent with Gemini & LangSmith
│   └── README.md
│
├── project/                    # Advanced LangChain Core Features
│   ├── project_1/              # Core Blocks: Tools, Middleware, Structured Output, Streaming
│   ├── chatbot.ipynb           # Token usage metadata & reasoning inspection
│   └── README.md
│
├── practice/                   # Deployment, Web APIs & Serving
│   ├── chat_bot.py             # FastAPI + LangServe API server for LCEL chains
│   ├── fast_api.py             # FastAPI service with Windows UTF-8 banner fix
│   ├── chatbot.ipynb           # Interactive prompt, translation & model testing
│   └── README.md
│
├── Machine_learning/           # Fundamental ML & Industry Projects
│   ├── class/                  # Statistics, EDA, Outliers, Regression, GD from scratch, VIF
│   │   ├── class_2.ipynb to class_9.ipynb
│   ├── project/
│   │   └── Linear_regression/  # End-to-End Used Bike Resale Price Estimation project
│   └── README.md
│
├── scripts/                    # Automation & developer utility scripts
│   ├── auto_commit.ps1         # Periodic git sync utility
│   ├── update_notebook.py      # Notebook maintenance utility
│   ├── update_notebook.ps1     # PowerShell maintenance wrapper
│   └── README.md
│
├── .github/workflows/          # GitHub Actions continuous integration
│   └── lint.yml                # Python syntax sanity check
│
├── .env.example                # Template for LLM and Observability credentials
├── pyproject.toml              # Unified package configuration
├── requirements.txt            # Project dependencies
├── LICENSE                     # MIT Open Source License
└── README.md                   # Repository overview
```

---

## 🧩 Modules Overview

### 1. LangChain Fundamentals (`1-langchain_basic/`)
* **Document Loaders**: `PyPDFLoader`, `TextLoader`, `WebBaseLoader` for unstructured data parsing.
* **Text Chunking**: Comparisons between `CharacterTextSplitter` and `RecursiveCharacterTextSplitter`.
* **Embedding Providers**: OpenAI (`text-embedding-3-small`) and open-source HuggingFace models (`sentence-transformers/all-MiniLM-L6-v2`).
* **Vector Stores**: Dense semantic indexing and search using **FAISS** and **ChromaDB**.
* 👉 Check out [`1-langchain_basic/README.md`](./1-langchain_basic/README.md) for full module documentation.

### 2. End-to-End RAG, LCEL & Modern LangChain (`langchain_langgraph/`)
* **RAG Pipeline (Section 6)**: Production Question-Answering system connecting Groq LLM, FAISS retriever, and structured prompt templates.
* **Modern LCEL & Serving (Section 7)**: Declarative pipeline construction with Unix-style pipe syntax (`prompt | model | parser`) and FastAPI/LangServe endpoints (`serve.py`).
* **Stateful Chatbots (Section 8)**: Session-based conversation memory with `ChatMessageHistory`, `RunnableWithMessageHistory`, and context window management with `trim_messages`.
* **LangChain 0.3 Core & Agents (Section 10)**: Provider-agnostic model initialization (`init_chat_model`), structured JSON schema extraction with Pydantic, execution modes (`invoke`, `batch`, `stream`), custom `@tool` creation, and autonomous agent loops with `create_agent`.
* **State Checkpointing**: Thread management using `langgraph.checkpoint.memory.MemorySaver`.
* 👉 Check out [`langchain_langgraph/README.md`](./langchain_langgraph/README.md) for full module documentation.

### 3. Agentic Systems with LangGraph (`langraphproject/`)
* **StateGraph Architecture**: Cyclic graphs with shared `TypedDict` state schemas.
* **Routing**: Dynamic branch execution using conditional edges and function tools.
* **Supervisor-Worker Pattern**: Multi-agent coordination with planning, delegation to specialized researcher agents, iteration counters, and memory checkpointing.
* **Model Dynamic Initialization**: Provider switching with `init_chat_model()`.
* **Observability**: Production monitoring, latency tracing, and token tracking with **LangSmith**.
* 👉 Check out [`langraphproject/README.md`](./langraphproject/README.md) for full module documentation.

### 4. Advanced LangChain Features (`project/`)
* **Structured Output**: Extracting schema-validated JSON directly into Pydantic models with `.with_structured_output()`.
* **Custom Tools**: Equipping agents with external execution capabilities via `@tool` decorators.
* **Lifecycle Callbacks**: Custom middleware handlers (`BaseCallbackHandler`) intercepting `on_llm_start`, `on_llm_end`, and `on_llm_error`.
* 👉 Check out [`project/README.md`](./project/README.md) for full module documentation.

### 5. API Serving & Deployment (`practice/`)
* **FastAPI + LangServe**: Exposing LCEL chains as production REST endpoints with automated OpenAPI docs and interactive web playgrounds (`/rag_chain/playground`).
* **Platform Hardening**: Windows UTF-8 command-line encoding resolutions for seamless server boots.
* 👉 Check out [`practice/README.md`](./practice/README.md) for full module documentation.

### 6. Machine Learning Foundations & Industry Projects (`Machine_learning/`)
* **Statistics & EDA (Classes 2-5)**: Univariate/multivariate analysis, correlation matrices, boxplots, and outlier filtering using IQR and Z-scores.
* **Linear Regression & Evaluation (Classes 6-7)**: Simple and Multiple Linear Regression models with train-test split, weights analysis, and metrics ($R^2$, MSE, RMSE).
* **Algorithms from Scratch (Class 8)**: Custom Gradient Descent optimization engine evaluating epoch loss progression on multivariate regression.
* **Feature Selection & VIF (Class 9)**: Detecting severe multicollinearity using Variance Inflation Factor (VIF).
* **End-to-End Industry Project**: Used Bike Resale Price Estimation (`project/Linear_regression/`) featuring raw data audit, sanitization, regression modeling, and serialized artifact export (`.joblib`).
* 👉 Check out [`Machine_learning/README.md`](./Machine_learning/README.md) for full module documentation.

---

## ⚡ Quick Start & Setup

### 1. Clone Repository
```bash
git clone https://github.com/MohitPayasi/generative-ai-and-agents.git
cd generative-ai-and-agents
```

### 2. Create Virtual Environment
```bash
# Windows
python -m venv .venv
.venv\Scripts\activate

# Linux / macOS
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

---

## 🔑 Environment Variables

Copy the provided [`.env.example`](./.env.example) to `.env` and configure your API credentials:

```bash
cp .env.example .env
```

Key variables required:
```env
GROQ_API_KEY=your_groq_api_key
GOOGLE_API_KEY=your_google_gemini_key
OPENAI_API_KEY=your_openai_api_key
HF_TOKEN=your_huggingface_token
LANGCHAIN_API_KEY=your_langsmith_api_key
LANGCHAIN_TRACING_V2=true
```

---

## 🛠️ Tech Stack

| Category | Technologies |
| :--- | :--- |
| **LLM Orchestration** | LangChain, LangGraph, LCEL, LangServe |
| **Model Providers** | Groq (Llama 3, Mixtral), Google Gemini, OpenAI, Ollama |
| **Embeddings & Vector Stores** | HuggingFace Sentence Transformers, FAISS, ChromaDB |
| **Backend & Serving** | FastAPI, Uvicorn, Pydantic |
| **Data Science & ML** | Scikit-Learn, NumPy, Pandas, Matplotlib, Seaborn, SciPy, Statsmodels, Joblib |
| **Monitoring & Tracing** | LangSmith |

---

## 👤 Author

**Mohit Payasi**
* GitHub: [@MohitPayasi](https://github.com/MohitPayasi)
* Repository: [generative-ai-and-agents](https://github.com/MohitPayasi/generative-ai-and-agents)
