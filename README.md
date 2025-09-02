# Temporal AI Agent Pipeline

An end-to-end **temporal agentic pipeline** for transforming raw, evolving data into a **dynamic, time-aware knowledge base**, and powering multi-agent retrieval systems on top of it.

This project extends traditional RAG (Retrieval-Augmented Generation) systems by incorporating **temporal reasoning, entity resolution, contradiction handling, and knowledge graph construction** to deliver more accurate and context-aware answers in dynamic domains (e.g., finance, healthcare).

---

## ✨ Features

- **Semantic Chunking**  
  Splits long documents into context-preserving chunks using percentile-based semantic similarity.

- **Atomic Fact Extraction**  
  Converts raw text into granular, labeled statements (Fact, Opinion, Prediction) with temporal attributes (Static, Dynamic, Atemporal).

- **Temporal Validation**  
  Pinpoints *when* statements are valid (valid_at / invalid_at) for true time-aware reasoning.

- **Entity Resolution**  
  Cleans noisy entity mentions (e.g., “AMD” vs. “Advanced Micro Devices, Inc.”) into canonical identities.

- **Contradiction & Invalidation**  
  Detects outdated facts and marks them as expired when new information arrives.

- **Temporal Knowledge Graph**  
  Assembles facts into a graph structure with time-aware edges for efficient querying.

- **Multi-Step Retrieval Agent**  
  Uses LangGraph to plan, orchestrate, and query the temporal KG for complex, multi-hop questions.

---

## 🧩 Example Workflow

### 1. Data Loading
```python
from langchain_community.document_loaders import HuggingFaceDatasetLoader

loader = HuggingFaceDatasetLoader(
    path="jlh-ibm/earnings_call",
    name="transcripts",
    page_content_column="transcript"
)
documents = loader.load()

