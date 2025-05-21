# Hybrid Retriever API

A lightweight FastAPI-based API for performing hybrid document retrieval using lexical (TF-IDF + BM25) and semantic (embedding-based + cross-encoder) search. It wraps a Rust + PyO3-backed `HybridRetriever` for high performance and accurate search over small-to-medium datasets.

## 🔧 Features

- ⚡ Hybrid search using precomputed document embeddings + query text
- 🧠 Cross-encoder reranking support
- 🔎 BM25 + TF-IDF lexical fallback
- 🌐 CORS-enabled and API-ready

---

## 📦 Requirements

- Python 3.8+
- `numpy`
- PyO3-bound `hre` module (compiled from Rust)
- A compatible cross-encoder model (e.g., `cross-encoder/ms-marco-MiniLM-L-6-v2`)


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





