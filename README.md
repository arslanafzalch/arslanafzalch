<!--
  SETUP
  1. Create a PUBLIC repo named EXACTLY your GitHub username.
  2. Put this file at the root as README.md.
  3. It renders at the top of github.com/<your-username>.
-->

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1F3B63,100:2E86C1&height=180&section=header&text=Arslan%20Afzal&fontSize=52&fontColor=ffffff&fontAlignY=35&desc=Applied%20AI%20Engineer&descSize=20&descAlignY=57" width="100%" />

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=20&pause=1200&color=2E86C1&center=true&vCenter=true&width=620&lines=LLM+agents+that+run+in+production;RAG+over+permission-scoped+enterprise+data;Multi-agent+orchestration+with+LangGraph;Evaluation+%3E+trial+and+error" alt="Typing SVG" />

<br>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/muhammad-arslan-afzal-33396613a/)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:arslanafzalch515@gmail.com)
![Location](https://img.shields.io/badge/Lahore,_PK-1F3B63?style=for-the-badge&logo=googlemaps&logoColor=white)

</div>

<div align="center">

`Technical Lead` · `6+ yrs engineering` · `4+ yrs LLM systems` · `15+ agents in production`

</div>

---

## <img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="28"> About

- Technical lead on an enterprise AI platform for a **global infrastructure investment firm**
- One entry point routing staff requests across **15+ specialised agents** over confidential deal, legal and financial data
- I spend my time on what doesn't demo well: **failed tool calls mid-plan**, permission-scoped retrieval, and knowing whether last week's prompt change made things worse
- Earlier work: **+40%** ticket-assignment accuracy, **−60%** manual operational processes

---

## <img src="https://media.giphy.com/media/iY8CRBdQXODJSCERIr/giphy.gif" width="28"> Tech Stack

<div align="center">

**Core**

<img src="https://skillicons.dev/icons?i=python,fastapi,django,postgres,redis,docker,azure,aws&theme=dark" />

**AI & Agents**

[![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white)](#)
[![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white)](#)
[![MCP](https://img.shields.io/badge/MCP-000000?style=for-the-badge&logo=anthropic&logoColor=white)](#)
[![Claude](https://img.shields.io/badge/Claude-D97757?style=for-the-badge&logo=anthropic&logoColor=white)](#)
[![OpenAI](https://img.shields.io/badge/Azure_OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)](#)
[![Cohere](https://img.shields.io/badge/Cohere-39594D?style=for-the-badge&logo=cohere&logoColor=white)](#)
[![pgvector](https://img.shields.io/badge/pgvector-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](#)
[![Langfuse](https://img.shields.io/badge/Langfuse-0A0A0A?style=for-the-badge&logo=tracing&logoColor=white)](#)

**ML & Data**

<img src="https://skillicons.dev/icons?i=pytorch,tensorflow,sklearn,opencv,anaconda&theme=dark" />

**Frontend & Tooling**

<img src="https://skillicons.dev/icons?i=react,redux,ts,tailwind,vite,git,github,linux,nginx,postman&theme=dark" />

</div>

<details>
<summary align="center"><b>📋 The full breakdown</b></summary>

<br>

| Area | Tools |
| --- | --- |
| **Agents** | LangGraph, LangChain, AutoGen, CrewAI, ReAct, Plan-and-Execute, MCP, A2A, tool calling, agent memory, durable checkpointing, human-in-the-loop |
| **Retrieval** | Hybrid BM25 + HNSW, query rewriting, relevance grading, groundedness checks, reranking, permission filtering, Azure AI Search, pgvector, FAISS, LlamaIndex |
| **Models** | Anthropic Claude, OpenAI / Azure OpenAI, Cohere, xAI, Hugging Face, LiteLLM, structured outputs, LoRA / QLoRA / PEFT, RLHF |
| **Evaluation** | Langfuse, regression and golden datasets, groundedness checks, retrieval precision and recall, tool-selection accuracy, p50/p95 latency, token and cost budgeting |
| **Backend** | Python, FastAPI, Django / DRF, async, SQLAlchemy 2, SSE streaming, PostgreSQL, Redis, Alembic, Docker, CI/CD |
| **Cloud** | Microsoft Foundry (Foundry SDK, project-scoped deployments, region-pinned for data residency), Azure App Service, AI Search, Document Intelligence, Blob Storage, Entra ID, AWS |
| **Classical ML** | PyTorch, TensorFlow, CNN, YOLO, Vision Transformer, ARIMA, LSTM, signal processing |

</details>

---

## <img src="https://media.giphy.com/media/dWesBcTLavkZuG35MI/giphy.gif" width="28"> How the orchestrator fits together

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

---

## <img src="https://media.giphy.com/media/LnQjpWaON8nhr21vNW/giphy.gif" width="28"> What I build

| | |
| --- | --- |
| 🧭 **Orchestration** | LangGraph supervisor routing to department-scoped sub-agents. Postgres checkpointing so long runs survive interruption, parallel fan-out where the plan allows, resume after mid-flow clarification without re-querying agents that already answered. |
| 🔍 **Retrieval** | Hybrid BM25 + vector across department indices, metadata filtered so retrieval stays inside the user's entitlements. A wildcard probe fires first, so the agent tells *"you don't have access"* apart from *"nothing matched"* — identical to a user, completely different problems. |
| 🧠 **Memory** | Short-term on a hybrid time-and-turn window. Long-term on pgvector with a distance gate that stops cold-start false recalls. |
| 🔌 **Tooling** | MCP connector platform where users attach their own tool servers via per-user OAuth, so agents work against each person's real workspace instead of a fixed tool list. |
| 📊 **Evaluation** | Tracing every plan step, tool call and retrieval, then running regression sets against tool-selection accuracy, groundedness, failure rate and p95 latency. |

---

<details>
<summary><b>🔬 Before the LLM wave — four years of applied ML</b></summary>

<br>

- **Network quality forecasting** — 250+ cell parameters across mobile towers, joined with weather data to model propagation effects like atmospheric ducting, predicting which RF parameters to change before quality dropped
- **Wearables** — gesture classification from smartwatch IMU streams, heart screening from ECG and PPG signals
- **Audio screening** — cough-based TB and COVID-19 detection, owning data engineering through to model training
- **Vision** — CNN and YOLO for wildlife monitoring, Vision Transformer for geospatial classification

</details>

---

<div align="center">

### Open to conversations about agent architecture, retrieval and production LLM systems.

[![LinkedIn](https://img.shields.io/badge/Let's_talk-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/muhammad-arslan-afzal-33396613a/)

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:2E86C1,100:1F3B63&height=120&section=footer" width="100%" />

</div>
