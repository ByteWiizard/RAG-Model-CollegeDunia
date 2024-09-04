# RAG-based System with Persisted Vector Store

## Project Overview

This project implements a Retrieval-Augmented Generation (RAG) system that loads a persisted vector database containing embeddings from a PDF document and uses it to answer user queries. The system leverages embeddings, multi-query retrieval, and an LLM (Language Learning Model) to generate responses based on document content.

## Features

- **PDF Embedding Generation**: The system creates embeddings from the content of PDF documents and stores them in a persisted vector database.
- **Query Answering**: Users can input a query, and the system retrieves relevant document chunks and generates answers using an LLM.
- **Persistence**: The vector database is persisted to disk, allowing for reloading without the need to reprocess the document.

## Requirements

### Prerequisites

- Python 3.8+
- Required libraries listed in `requirements.txt`

### Libraries

- `langchain_community`
- `transformers`
- `Chroma`
- `nltk`
- `joblib`

### To install the required libraries, run:

```bash
pip install -r requirements.txt