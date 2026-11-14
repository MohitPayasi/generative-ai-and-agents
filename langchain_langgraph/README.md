# 🦜🕸️ LangChain & LangGraph Workflows

Welcome to the **LangChain & LangGraph** section of the repository! This directory contains practical implementations of end-to-end LLM applications, modern Document Ingestion pipelines, Vector Embeddings, Vector Stores (FAISS), RAG chains with Groq, stateful Chatbots with Memory, and modern LangChain 0.3+ agentic components (Tools, Structured Output, Execution Modes, and Dynamic Model Integrations).

---

## 📌 Direct GitHub Notebook Links

Quickly access individual notebooks and modules:

| Section / Topic | Notebook / File | Description |
| :--- | :--- | :--- |
| **Data Ingestion & Splitting** | [`data_ingestion.ipynb`](./introduction/data_ingestion.ipynb) | Document loaders (PDF, Web, Text, Wiki) & recursive chunking strategies |
| **Embeddings & FAISS** | [`embedding.ipynb`](./introduction/embedding.ipynb) | HuggingFace MiniLM embeddings & FAISS dense vector search |
| **LangChain Core & Memory** | [`langchain.ipynb`](./introduction/langchain.ipynb) | ChatGroq models & `MemorySaver` thread checkpointing |
| **Section 6: End-to-End RAG Project** | [`project.ipynb`](./section_6/project.ipynb) | Production RAG pipeline with Groq LLM & persistent FAISS retriever |
| **Section 7: LCEL Basics** | [`simple_llm_lcel.ipynb`](./section_7/simple_llm_lcel.ipynb) | Modern LangChain Expression Language (LCEL) & Runnable chains |
| **Section 7: API Serving** | [`serve.py`](./section_7/serve.py) | Deploying LCEL chains as REST endpoints with FastAPI & LangServe |
| **Section 8: Conversational Chatbot** | [`chatbot.ipynb`](./section_8/chatbot.ipynb) | Chatbot with `ChatMessageHistory`, `RunnableWithMessageHistory` & `trim_messages` |
| **Section 10: Model Integration** | [`llm_model_integration.ipynb`](./section_10/llm_model_integration.ipynb) | Provider-agnostic dynamic model switching with `init_chat_model()` |
| **Section 10: Message Architecture** | [`message.ipynb`](./section_10/message.ipynb) | Message primitives (`SystemMessage`, `HumanMessage`, `AIMessage`, `ToolMessage`) |
| **Section 10: Execution Paradigms** | [`invoke_batch_stream.ipynb`](./section_10/invoke_batch_stream.ipynb) | Core execution methods: `invoke()`, `batch()`, and streaming tokens with `stream()` |
| **Section 10: Structured Output** | [`structured_output.ipynb`](./section_10/structured_output.ipynb) | Strict schema validation & typed JSON using Pydantic `BaseModel` & `with_structured_output()` |
| **Section 10: Custom Tools** | [`tool_creation.ipynb`](./section_10/tool_creation.ipynb) | Defining custom agent tools using the `@tool` decorator with schema inference |
| **Section 10: Autonomous Agents** | [`agent_using_langchain.ipynb`](./section_10/agent_using_langchain.ipynb) | Building tool-calling AI agents with `create_agent` and automated dispatch |
| **Dependencies** | [`requirement.txt`](./requirement.txt) | Environment requirements for this section |

---

## 🗂️ Directory Structure

```text
langchain_langgraph/
├── introduction/
│   ├── data_ingestion.ipynb          # TextLoader, PyPDFLoader, WebBaseLoader, WikipediaLoader & Text Splitters
│   ├── embedding.ipynb               # HuggingFace Embeddings, SentenceTransformer & FAISS Vector Indexing
│   ├── langchain.ipynb               # ChatGroq, Message types & LangGraph MemorySaver checkpointing
│   └── faiss_index/                  # Serialized FAISS index files (index.faiss, index.pkl)
│
├── section_6/
│   ├── project.ipynb                 # Complete End-to-End RAG Chain with Groq LLM & FAISS Retrieval
│   └── faiss_index/                  # Project-specific persistent FAISS vector store
│
├── section_7/
│   ├── simple_llm_lcel.ipynb         # Declarative pipelines with LangChain Expression Language (LCEL)
│   └── serve.py                      # FastAPI + LangServe production API server
│
├── section_8/
│   └── chatbot.ipynb                 # Stateful Chatbot with ChatMessageHistory & token trimming
│
├── section_10/
│   ├── llm_model_integration.ipynb   # Multi-provider initialization with init_chat_model()
│   ├── message.ipynb                 # In-depth message abstraction, prompt templates & system roles
│   ├── invoke_batch_stream.ipynb     # Synchronous invoke, multi-prompt batching & streaming tokens
│   ├── structured_output.ipynb       # Pydantic schema-driven predictable responses
│   ├── tool_creation.ipynb           # External functions wrapped as tools via @tool
│   └── agent_using_langchain.ipynb   # Function-calling Agents with create_agent
│
├── .env                              # Environment credentials (API keys)
├── requirement.txt                   # All required section dependencies
└── README.md                         # Section documentation
```

---

## 🚀 Detailed Module Breakdown

### 1. `introduction/data_ingestion.ipynb`
* **Document Loaders**:
  * `TextLoader`: Local `.txt` file parsing.
  * `PyPDFLoader`: PDF documents parsing and multi-page extraction.
  * `WebBaseLoader`: Web scraping and converting online HTML content into LangChain Documents.
  * `WikipediaLoader`: Direct Wikipedia querying and document construction.
* **Text Splitting**:
  * `CharacterTextSplitter` & `RecursiveCharacterTextSplitter` with tuned `chunk_size` and `chunk_overlap`.

### 2. `introduction/embedding.ipynb`
* **Embeddings**:
  * HuggingFace open-source sentence-transformer embeddings (`sentence-transformers/all-MiniLM-L6-v2`).
* **Vector Storage**:
  * **FAISS** (Facebook AI Similarity Search) dense vector indexing and local disk persistence (`index.faiss`, `index.pkl`).
* **Retriever Interface**:
  * LangChain `as_retriever()` for semantic vector similarity queries.

### 3. `introduction/langchain.ipynb`
* **ChatGroq Integration**: High-speed inference using models like `mixtral-8x7b-32768` and `llama-3.3-70b-versatile`.
* **LangGraph Checkpointing**: State persistence and thread management with `MemorySaver`.

### 4. `section_6/project.ipynb` (End-to-End RAG Project)
* **Production RAG Architecture**:
  * Question Answering system combining `ChatGroq`, `ChatPromptTemplate`, `FAISS`, and `StrOutputParser`.
  * Dynamic context injection via `create_stuff_documents_chain` and `create_retrieval_chain`.
  * Clean question-answering workflow over external web documentation.

### 5. `section_7/simple_llm_lcel.ipynb` & `serve.py` (LCEL & Serving)
* **LangChain Expression Language (LCEL)**:
  * Unix pipe operator syntax (`prompt | model | parser`).
  * Standard `Runnable` methods: `invoke()`, `batch()`, `stream()`.
  * Elimination of legacy `LLMChain` boilerplate.
* **LangServe API Server (`serve.py`)**:
  * Exposes LCEL pipelines over REST endpoints with FastAPI.
  * Auto-generated interactive Swagger UI and LangServe playground at `/chain/playground`.

### 6. `section_8/chatbot.ipynb` (Stateful Conversation & History)
* **Chat History Management**:
  * `ChatMessageHistory` and `BaseChatMessageHistory` interface.
  * Wrapping chains with `RunnableWithMessageHistory` to bind persistent session IDs.
* **Prompt Memory Injection**:
  * Injecting dynamic message history into prompts using `MessagesPlaceholder(variable_name="messages")`.
* **Context Trimming**:
  * Preventing context window overflow using `trim_messages` strategy with token / message bounds.

### 7. `section_10/` (Modern LangChain Core & Agent Systems)
* **`llm_model_integration.ipynb`**:
  * Modern unified model loader: `init_chat_model(model=..., model_provider=...)`.
  * Decouples application logic from vendor SDKs (Groq, OpenAI, Google Gemini).
* **`message.ipynb`**:
  * Core message role abstractions: `SystemMessage`, `HumanMessage`, `AIMessage`, and `ToolMessage`.
  * Handling multi-turn dialogues, system role framing, and assistant outputs.
* **`invoke_batch_stream.ipynb`**:
  * In-depth comparison of execution paradigms:
    * `invoke()`: Single synchronous prompt execution.
    * `batch()`: Concurrent processing of multiple prompts with optimized latency.
    * `stream()`: Real-time token streaming generator for responsive user interfaces.
* **`structured_output.ipynb`**:
  * Enforcing rigid, predictable JSON/Pydantic schemas using `llm.with_structured_output(Schema)`.
  * Validating entity extraction (e.g., movie titles, ratings, release years) without regex or brittle JSON parsing.
* **`tool_creation.ipynb`**:
  * Extending LLM capabilities to external APIs and deterministic code using `@tool`.
  * Automated JSON schema generation from Python type annotations and docstrings.
  * Inspection of tool calls requested by the model.
* **`agent_using_langchain.ipynb`**:
  * Assembling autonomous agents using `create_agent` with model and tool attachments.
  * ReAct-style agentic loop: query understanding, tool invocation, observation parsing, and final response generation.

---

## ⚙️ Quick Start

### 1. Install Dependencies
```bash
cd langchain_langgraph
pip install -r requirement.txt
```

### 2. Configure Environment Variables
Create or edit your `.env` file inside `langchain_langgraph/`:
```env
GROQ_API_KEY=your_groq_api_key
HF_TOKEN=your_huggingface_token
```

### 3. Run FastAPI / LangServe Server
```bash
python section_7/serve.py
```
Access the interactive playground at [http://localhost:8000/chain/playground](http://localhost:8000/chain/playground).
