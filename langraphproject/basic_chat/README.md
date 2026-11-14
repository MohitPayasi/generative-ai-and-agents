# 💬 LangGraph Basic Chat, Monitoring & Multi-Agent Systems

This directory contains practical Jupyter Notebooks demonstrating stateful, graph-based agents built with **LangGraph**, dynamic model initialization, end-to-end observability via **LangSmith**, and complex multi-agent architectures.

---

## 📌 Notebooks Overview

| Notebook | Core Concepts Covered | Key Features |
| :--- | :--- | :--- |
| [`basic_chat_1.ipynb`](./basic_chat_1.ipynb) | StateGraph Fundamentals | TypedDict state schema, computational nodes, directional edges, and ChatGroq integration. |
| [`debug_monitoring.ipynb`](./debug_monitoring.ipynb) | Observability & Tool Routing | Dynamic `init_chat_model`, token metadata inspection, custom callback handlers (`MonitoringCallbackHandler`), and `ToolNode` with `tools_condition`. |
| [`multiaiagent.ipynb`](./multiaiagent.ipynb) | Multi-Agent Coordination | Specialized agent nodes collaborating via shared message state. |
| [`super_multi_ai_agent.ipynb`](./super_multi_ai_agent.ipynb) | Supervisor-Worker Multi-Agent Architecture | Dynamic planning, worker task delegation (Researcher), iteration control loops, and `MemorySaver` thread checkpointing. |

---

## 🚀 Detailed Notebook Breakdown

### 1. `basic_chat_1.ipynb` — LangGraph Fundamentals
* **State**: Defined a strongly-typed shared state schema using Python's `typing.TypedDict`.
* **Nodes**: Implemented standalone computational functions (nodes) that read from and update the graph state.
* **Edges**: Added standard directional edges connecting nodes, as well as `START` and `END` control nodes.
* **Graph Compilation**: Compiled the `StateGraph` into an executable runnable using `.compile()`.
* **Chat Node Implementation**: Connected a ChatGroq LLM inside a node to generate conversational responses.

### 2. `debug_monitoring.ipynb` — Model Initialization & Observability
* **Unified Model Initialization**:
  ```python
  from langchain.chat_models import init_chat_model
  model1 = init_chat_model(model='openai/gpt-oss-20b', model_provider='groq')
  ```
  Decoupled application logic from specific vendor SDKs.
* **Response Metadata Inspection**: Extracted token usage (`usage_metadata`) and execution latency from model responses.
* **Lifecycle Callbacks (`MonitoringCallbackHandler`)**: Built custom `BaseCallbackHandler` implementing `on_llm_start`, `on_llm_end`, and `on_llm_error` for client-side logging and debugging.
* **Tool Calling & ToolNode**: Built a self-routing agent workflow using `@tool`, `bind_tools`, `ToolNode`, and `tools_condition` with message state reducer (`add_messages`).

### 3. `multiaiagent.ipynb` — Multi-Agent Architecture
* Multi-agent orchestration, collaboration, and role specialization in LangGraph.
* Passing structured message state across multiple distinct agents.

### 4. `super_multi_ai_agent.ipynb` — Supervisor Multi-Agent System
* **Supervisor Pattern**:
  * An orchestrator agent dynamically breaks down user requests into actionable sub-tasks (`workflow_stage = 'planning'`).
  * Directs task assignments to specialized workers (e.g., `researcher`).
* **Iteration Safeguards**:
  * Tracks an `iteration_count` variable to prevent infinite loops while agents converse.
* **Memory Checkpointing**:
  * State persistence and session resumption across conversational turns using `langgraph.checkpoint.memory.MemorySaver`.
* **Synthesis Node**:
  * Synthesizes findings from all worker outputs into a single coherent response for the end-user.

---

## 🔑 Environment Setup (`.env`)

Ensure the following variables are configured in `.env`:

```env
GROQ_API_KEY=your_groq_api_key
LANGCHAIN_TRACING_V2=true
LANGCHAIN_API_KEY=your_langsmith_api_key
LANGCHAIN_PROJECT=langgraph-agent-systems
```
