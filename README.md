# Intelligent Document RAG System

A Retrieval-Augmented Generation (RAG) system that allows you to query PDF documents using natural language. The system uses LangChain, ChromaDB for vector storage, and Ollama/AWS Bedrock for embeddings and text generation.

## Features

- PDF document ingestion and chunking
- Vector storage using ChromaDB
- Semantic search capabilities
- Natural language querying of document contents
- Support for multiple embedding providers (Ollama and AWS Bedrock)
- Automated testing framework for response validation

## Prerequisites

- Python 3.x
- Ollama installed locally (for local embedding and LLM options)
- AWS account with Bedrock access (for AWS embedding option)

## Installation

1. Clone the repository:

```bash
git clone <repository-url>
cd Intelligent_Document_RAG_System
```

2. Install the required dependencies:

```bash
pip install langchain langchain-community chromadb pypdf
```

## Project Structure

- `populate_database.py` - Script to ingest PDF documents and create/update the vector store
- `query_data.py` - Main script for querying the document database
- `get_embedding_function.py` - Configuration for embedding models (Ollama/AWS Bedrock)
- `test_rag.py` - Test suite for validating RAG responses
- `data/` - Directory for storing PDF documents
- `chroma/` - Directory where the vector database is stored

## Usage

1. Place your PDF documents in the `data/` directory.

2. Populate the vector database:

```bash
python populate_database.py
```

To reset the database, use:

```bash
python populate_database.py --reset
```

3. Query the documents:

```bash
python query_data.py "Your question here"
```

4. Run tests:

```bash
python -m pytest test_rag.py
```

## Configuration

### Embedding Models

The system supports two embedding providers:

1. AWS Bedrock (default)
2. Ollama (local option)

To switch between providers, modify `get_embedding_function.py`:

```python
# For AWS Bedrock
embeddings = BedrockEmbeddings(
    credentials_profile_name="default",
    region_name="us-east-1"
)

# For Ollama (uncomment to use)
# embeddings = OllamaEmbeddings(model="nomic-embed-text")
```

## Testing

The testing framework in `test_rag.py` validates responses against expected answers. Tests use the Mistral model through Ollama for response validation.

## Contributing

Feel free to submit issues, fork the repository, and create pull requests for any improvements.
