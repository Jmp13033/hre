# 🌍 Hybrid Retriever API


### 🚀 The *Fastest Engine in the World*

```bash
pip install hre-tools --verbose
```

A blazing-fast, lightweight API for real-time hybrid document retrieval using both sparse (TF-IDF + BM25) and dense (embedding-based + cross-encoder) methods.  
Powered by Rust under the hood, HRE delivers unmatched speed and precision perfect for AI agents, enterprise search, internal tools, chat-based QA, and more.

---

## Features

<<<<<<< HEAD
- Hybrid search using precomputed document embeddings + query text
- Cross-encoder reranking support
- BM25 + TF-IDF lexical fallback
- CORS-enabled and API-ready
=======
- ⚡ **Real-time hybrid search** combining dense & sparse signals
- 🧠 Optional **cross-encoder reranking** for precision
- 🔎 **Lexical fallback** with BM25 + TF-IDF
- 🌐 **CORS-enabled** and API-ready
- 🏢 Designed for business-critical applications
>>>>>>> d38cefed0ce62bc363be911d156f8d7bd58a1518

---

## Requirements

- Python 3.8+
- `numpy`
- PyO3-bound `hre` module (Rust-backed)
- A compatible cross-encoder model (e.g., `cross-encoder/ms-marco-MiniLM-L-6-v2`)
- **Rust toolchain:** [Rust & Cargo](https://www.rust-lang.org/tools/install) (needed to build the Rust extension)

<<<<<<< HEAD
=======
---

## 🧪 Example Usage

>>>>>>> d38cefed0ce62bc363be911d156f8d7bd58a1518
```python
import numpy as np
from hre_tools import HybridRetriever

documents = [
    "Doc one",
    "Doc two",
<<<<<<< HEAD
    "Another doc"
=======
    "Another doc",
>>>>>>> d38cefed0ce62bc363be911d156f8d7bd58a1518
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
<<<<<<< HEAD
```
=======

# Fallback retrieve (lexical/semantic)
retrieved_docs, other_scores = retriever.retrieve(query_text, top_k=3)
```

---



## ⚠️ Hardware Compatibility Note

This package includes optimized implementations that may use CPU-specific features when available. 
Key considerations:
- **x86_64 Systems**: Automatic AVX2 acceleration will be used if detected

For maximum performance on x86, ensure:
- CPU supports AVX2 instructions

*Note: The package will automatically use the fastest available implementation for your hardware.*



## 💬 Feedback

We’re currently running a pilot and looking for feedback! Try it out and let us know how it performs on your real-world workloads.




>>>>>>> d38cefed0ce62bc363be911d156f8d7bd58a1518
