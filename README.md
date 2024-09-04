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

- `ollama`
- `chromadb`
- `pdfplumber`
- `nltk`
- `langchain`
- `langchain-core`
- `langchain-community`
- `langchain_text_splitters`
- `unstructured`
- `unstructured[all-docs]`
 
### To install the required libraries, run:

```bash
pip install -r requirements.txt
```

## How It Works

- **Preprocess PDF**: The document is split into chunks, and embeddings are generated using the `OllamaEmbeddings` model. These embeddings are stored in a vector database using `Chroma`.
  
- **Persist Vector Store**: The vector store is automatically persisted to a specified directory during creation.

- **Load and Query**: The system loads the persisted vector database, retrieves relevant document chunks based on a user query, and answers the query using the LLM.

## How to Run the Project

### Step 1: Generate and Persist Vector Database

1. Open the python notebook where the document embeddings are created and persisted.

2. Run the code to generate the vector store and automatically persist it to the `models/vector_db` directory:

```python
# Specify the directory where the vector database will be persisted
persist_directory = "models"

# Create the Chroma vector database
vector_db = Chroma.from_documents(
    documents=chunks,
    embedding=OllamaEmbeddings(model="nomic-embed-text", show_progress=True),
    collection_name="local-rag",
    persist_directory=persist_directory  # Persistence is handled automatically
)
```

### Step 2: Load the Persisted Vector Database and Query It

1. Use the provided LoadedRag.ipynb script to load the persisted vector database and query it. Example query:

2. Run the code to generate the vector store and automatically persist it to the `models` directory:

3. Run the LoadedRag.ipynb cells one by one and query the model using following the command

```python
chain.invoke("How do I insert a Sim , Give me the name of the phone for which you are providing information?")
```

## Response of above query from Rag
- **answer**: The instructions provided seem to be for a Nokia 6310 phone. Here's how to insert a SIM card into it:\n\n1. Put your fingernail in the small slot at the top of the phone, lift and remove the cover.\n2. If the battery is in the phone, to remove it, lift it out.\n3. Slide the SIM card in the SIM card slot with the contact area face down. If you have a second SIM, slide it in the SIM2 slot. Both SIM cards are available at the same time when the device is not being used, but while one SIM card is active, for example, making a call, the other may be unavailable.\n4. If you have a memory card, slide the memory card holder to the left and open it up. Place the memory card in the slot.

## Project Files

- `main.ipynb`: The notebook used to preprocess and persist the vector database from a PDF document.
- `main.py`: The Python script to load the persisted vector database and query it.
- `requirements.txt`: Lists all dependencies required for the project.
- `LoadedRag.ipyng`: python notebook that demonstrated how to load the saved preprocessed document and run the model.
- `models`: Directory where the vector store is persisted.

## Challenges

- **Embedding Consistency**: Ensuring consistent and meaningful embeddings from document chunks required tuning the embedding model.
- **Vector Store Loading**: Efficiently loading the persisted vector database and ensuring it is optimized for query retrieval.
- **Gathering the required libraries**: It was tedious task to gather the Poppler, pdfinfo, tesssaract important libraries.
