# AISalesPrediction
Phase 1: Machine Learning Prediction Pipeline

In the first phase, I built an end-to-end sales forecasting pipeline on the Rossmann dataset by integrating daily sales records with store-level metadata and preparing the data for time-aware supervised learning. I performed preprocessing by filtering closed stores, handling missing competition and promotion fields, and extracting temporal features such as Year, Month, Day, DayOfWeek, IsWeekend, and IsStateHoliday to better capture retail demand patterns.

I then designed a feature engineering pipeline that combined categorical encoding, lag-based historical signals, and store segmentation. This included one-hot encoding fields like StoreType, Assortment, and PromoInterval, generating Sales_lag1 and Sales_roll7_mean to capture short-term sales momentum, and applying KMeans clustering on store characteristics to introduce a store-level behavioral grouping feature.

To preserve realistic evaluation, I used a time-based train/test split instead of a random split, training on data before January 1, 2015 and testing on later records. I benchmarked multiple models, including Decision Tree, Random Forest, Linear Regression, Ridge, and Lasso, and selected XGBoost because it achieved the strongest overall predictive performance. Finally, I saved both the trained model and the exact feature schema so the deployment pipeline could maintain strict training-serving consistency during inference.
The system is served through a FastAPI backend, which exposes a prediction endpoint that accepts structured inputs from the UI.

Technologies used:
FastAPI, XGBoost, Pandas, NumPy, scikit-learn, KMeans, Bootstrap

Phase 2: AI RAG-based Assistant

In the second phase, I extended the system with an AI assistant using a Retrieval-Augmented Generation (RAG) architecture to help users understand model inputs and prediction logic.

Project-specific documentation (such as field definitions and feature engineering notes) is stored as text files, which are processed through a document chunking pipeline. Each chunk is converted into vector embeddings using a SentenceTransformer model, and stored in a FAISS vector database for efficient similarity search.

When a user asks a question, the system embeds the query, retrieves the most relevant document chunks using vector similarity search, and passes this context to a locally hosted LLM via Ollama (Llama 3.1). The LLM then generates a grounded, context-aware response. Guardrails are applied to ensure the assistant only answers domain-specific questions related to the project.

Technologies used:

SentenceTransformers (embeddings)

FAISS (vector similarity search)

Ollama + Llama 3.1 (local LLM)

FastAPI (chat API orchestration)

Custom prompt engineering (context grounding + guardrails)


Key Learnings:

Serving ML models via API

Designing feature engineering pipelines

Building RAG systems end-to-end

Vector similarity search with FAISS

Local LLM inference using Ollama

Prompt engineering + guardrails

Full-stack AI system design
