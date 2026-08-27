<!--
  SETUP
  1. Create a PUBLIC repo named exactly your GitHub username.
  2. Put this file at the root as README.md.
  3. It will render at the top of github.com/<your-username>.

  Replace every YOUR-HANDLE below with your GitHub username.
-->

<div align="center">

# Arslan Afzal

**Applied AI Engineer · LLM agents, RAG and production AI systems**

Lahore, Pakistan

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/muhammad-arslan-afzal-33396613a/)
[![Email](https://img.shields.io/badge/Email-Get_in_touch-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:arslanafzalch515@gmail.com)

</div>

---

I build LLM systems that run in production, for enterprise customers who care about
where their data lives and whether the agent can be audited afterwards.

Right now I'm technical lead on an enterprise AI platform for a global infrastructure
investment firm. One conversational entry point routes staff requests across 15+
specialised agents working over confidential deal, legal and financial data. Most of my
time goes into the parts that don't demo well: what happens when a tool call fails
halfway through a plan, how retrieval respects document-level permissions, and how you
tell whether last week's prompt change made the agent worse.

## What I work on

**Agent orchestration.** A LangGraph supervisor routing to department-scoped
sub-agents, with Postgres checkpointing so long runs survive interruption, parallel
fan-out where the plan allows it, and resume after mid-flow clarification without
re-querying agents that already answered.

**Retrieval that respects permissions.** Hybrid BM25 and vector search across
department indices, with metadata filtering so every retrieval stays inside the user's
entitlements. One detail I'm oddly fond of: a wildcard probe fired before the real
query, so the agent can tell "you don't have access" apart from "nothing matched."
Those two failures look identical to a user and mean completely different things.

**Agent memory.** Short-term working memory on a hybrid time-and-turn window,
long-term memory on pgvector with a distance gate that stops cold-start false recalls.

**Tools and extensibility.** An MCP connector platform where users attach their own
tool servers via per-user OAuth, so agents work against each person's actual workspace
rather than a fixed tool list.

**Evaluation.** Tracing every plan step, tool call and retrieval, then running curated
regression sets against tool-selection accuracy, groundedness, failure rate and p95
latency. Trial-and-error prompt tuning doesn't survive contact with production.

## How the orchestrator fits together

```mermaid
flowchart TD
    U([User request]) --> C[Classify intent]
    C --> S{Supervisor<br/>router}

    S --> F[Finance agent]
    S --> L[Legal agent]
    S --> D[Deal team agent]
    S --> O[Operations agent]

    F --> R[(Hybrid retrieval<br/>BM25 + vector<br/>permission filtered)]
    L --> R
    D --> R
    O --> R

    R --> G{Groundedness<br/>check}
    G -->|fails| R
    G -->|passes| Y[Synthesise + cite]
    Y --> ST([SSE stream to client])

    S -.durable state.-> PG[(Postgres<br/>checkpointer)]
    S -.recall.-> M[(pgvector<br/>long-term memory)]
```

## Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![LangChain](https://img.shields.io/badge/LangGraph_%2F_LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL_%2B_pgvector-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![Azure](https://img.shields.io/badge/Azure-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)

<details>
<summary><b>The fuller list</b></summary>

<br>

| Area | Tools |
| --- | --- |
| **Agents** | LangGraph, LangChain, AutoGen, CrewAI, ReAct, Plan-and-Execute, MCP, A2A, tool calling, agent memory, durable checkpointing |
| **Retrieval** | Hybrid BM25 + HNSW, query rewriting, relevance grading, groundedness checks, reranking, permission filtering, Azure AI Search, pgvector, FAISS, LlamaIndex |
| **Models** | Anthropic Claude, OpenAI / Azure OpenAI, Cohere, xAI, Hugging Face, LiteLLM, structured outputs, LoRA / QLoRA / PEFT, RLHF |
| **Evaluation** | Langfuse, regression and golden datasets, groundedness checks, retrieval precision and recall, tool-selection accuracy, p50/p95 latency, token and cost budgeting |
| **Backend** | Python, FastAPI, Django / DRF, async, SQLAlchemy 2, SSE streaming, PostgreSQL, Redis, Alembic, Docker, CI/CD |
| **Cloud** | Microsoft Foundry (Foundry SDK, project-scoped deployments, region-pinned for data residency), Azure App Service, AI Search, Document Intelligence, Blob Storage, Entra ID, AWS |
| **ML** | PyTorch, TensorFlow, CNN, YOLO, Vision Transformer, ARIMA, LSTM, signal processing |

</details>

## Before the LLM wave

Four years of applied ML before agents were the interesting problem, and it still shapes
how I think about evaluation:

- Forecasting network quality across 250+ cell parameters on mobile towers, joined with
  weather data to model propagation effects like atmospheric ducting, then predicting
  which RF parameters to change before quality dropped
- Gesture classification from smartwatch IMU streams, and heart screening from
  wearable ECG and PPG signals
- Cough-based TB and COVID-19 screening, owning the data engineering through to training

## Elsewhere

- [LinkedIn](https://www.linkedin.com/in/muhammad-arslan-afzal-33396613a/)
- [arslanafzalch515@gmail.com](mailto:arslanafzalch515@gmail.com)

<div align="center">
<sub>Open to conversations about agent architecture, retrieval and production LLM systems.</sub>
</div>
