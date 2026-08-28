# FinRAG – Financial Retrieval-Augmented Generation

A financial question-answering system based on Retrieval-Augmented Generation (RAG), combining vector search, document retrieval, reranking, and Large Language Models.

## Overview

FinRAG is designed to improve the quality of financial question answering by retrieving relevant information from a knowledge base before generating an answer with an LLM.

Instead of relying only on the model's internal knowledge, the system follows a retrieval-augmented workflow:

User Query
↓
Query Processing
↓
Vector Search
↓
Relevant Documents
↓
Reranking
↓
Context + Query
↓
LLM
↓
Final Answer

## Key Technologies

- Python
- FastAPI
- Milvus Vector Database
- PyMilvus
- LangChain
- Large Language Models (LLMs)
- BCE Embedding Model
- BCE Reranker Model
- Docker

## RAG Pipeline

The system combines several components:

### 1. Embedding

The user query and documents are converted into numerical vector representations.

These vectors allow the system to find information that is semantically similar to the user's question.

### 2. Vector Retrieval

Milvus is used as the vector database to store and retrieve relevant information efficiently.

### 3. Reranking

The retrieved results are passed through a reranking model to improve the relevance of the selected context.

### 4. Generation

The retrieved context is provided to an LLM, which generates the final response.

## Architecture

```text
                  User
                   |
                   v
             Financial Query
                   |
                   v
              FastAPI API
                   |
                   v
             Query Processing
                   |
                   v
              Embeddings
                   |
                   v
          +------------------+
          |      Milvus      |
          |  Vector Database |
          +------------------+
                   |
                   v
            Relevant Results
                   |
                   v
              Reranking
                   |
                   v
          Relevant Context
                   |
                   v
                 LLM
                   |
                   v
             Final Answer
