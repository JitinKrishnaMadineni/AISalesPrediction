## Project Structure

```
sales_prediction_app/
│
├── app.py                     # FastAPI backend (prediction + RAG APIs)
├── requirements.txt           # Python dependencies
├── xgboost_sales_model.json   # Trained XGBoost model
├── model_features.json        # Feature schema for inference consistency
│
├── templates/
│   └── index.html             # Frontend UI 
│
├── static/
│   └── style.css              # UI styling (Bootstrap)
│
├── docs/
│   ├── field_guide.md         # RAG knowledge base (feature definitions)
│   └── model_notes.md         # Model & pipeline documentation
│
├── vector_store/
│   ├── rossmann_docs.index    # FAISS vector index
│   └── chunks.pkl             # Embedded document chunks
│
└── logs/
    └── prediction_logs.xlsx   # Logged predictions for monitoring & analysis
```

---

## Directory Overview

- **app.py** → Main FastAPI application (serves UI, prediction API, and chatbot)  
- **templates/** → HTML templates rendered via FastAPI  
- **static/** → CSS and frontend assets  
- **docs/** → Source documents used for RAG pipeline  
- **vector_store/** → Precomputed embeddings and FAISS index  
- **logs/** → Stores prediction logs for auditing and analysis  

---
