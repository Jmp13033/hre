# 🌍 Hybrid Retriever API

### 🚀 The *Fastest Engine in the World*

```bash
pip install hre-tools --verbose
```

A blazing-fast, lightweight API for real-time hybrid document retrieval using both sparse (TF-IDF + BM25) and dense (embedding-based + cross-encoder) methods.  
Powered by Rust under the hood, HRE delivers unmatched speed and precision perfect for AI agents, enterprise search, internal tools, chat-based QA, and more.

---

## 🔧 Features

- ⚡ **Real-time hybrid search** combining dense & sparse signals
- 🧠 Optional **cross-encoder reranking** for precision
- 🔎 **Lexical fallback** with BM25 + TF-IDF
- 🌐 **CORS-enabled** and API-ready
- 🏢 Designed for business-critical applications

---

## 📦 Requirements

- Python 3.8+
- `numpy`
- PyO3-bound `hre` module (Rust-backed)
- A compatible cross-encoder model (e.g., `cross-encoder/ms-marco-MiniLM-L-6-v2`)
- **Rust toolchain:** [Rust & Cargo](https://www.rust-lang.org/tools/install) (needed to build the Rust extension)

---

## 🧪 Example Usage

```python
import numpy as np
from hre_tools import HybridRetriever

documents = [
    "Doc one",
    "Doc two",
    "Another doc",
] + [f"Doc {i}" for i in range(8)]

# Define matching embeddings
embeddings = np.random.rand(len(documents), 300).astype(np.float32)

# Define query
query_text = "What is in another doc?"
query_emb = np.random.rand(1, 300).astype(np.float32)

# Instantiate retriever
retriever = HybridRetriever(
    embeddings=embeddings,
    documents=documents,
    cross_encoder="cross-encoder/ms-marco-MiniLM-L-6-v2",
    source_filename="example_index"
)

# Perform hybrid search
docs, scores = retriever.hybrid_search(query_emb, query_text, top_k=3)

# Fallback retrieve (lexical/semantic)
retrieved_docs, other_scores = retriever.retrieve(query_text, top_k=3)
```

---

## 💬 Feedback

We’re currently running a pilot and looking for feedback! Try it out and let us know how it performs on your real-world workloads.
