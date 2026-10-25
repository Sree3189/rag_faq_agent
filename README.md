# RAG FAQ Agent

This project is a simple Retrieval-Augmented Generation (RAG) chatbot built to answer customer support questions from a FAQ knowledge base.

## Overview

The agent reads questions and answers from `faq.txt`, splits the text into searchable chunks, embeds those chunks using Azure OpenAI embeddings, and retrieves the most relevant passages before generating a response with Azure OpenAI chat models.

## Files

- `faq.txt` – FAQ source data used as the knowledge base
- `main.ipynb` – Jupyter notebook containing the full RAG pipeline
- `README.md` – project documentation

## How it works

1. The FAQ file is loaded into the notebook.
2. The text is split into smaller chunks for efficient retrieval.
3. Each chunk is converted into embeddings using Azure OpenAI embeddings.
4. The embeddings are stored in a FAISS vector store.
5. A user question is matched against the vector store and the most relevant FAQ entries are retrieved.
6. The retrieved context is passed to Azure OpenAI chat model to generate a grounded answer.

## Tech stack

- Python
- LangChain
- FAISS
- Azure OpenAI
- Jupyter Notebook

## Setup

1. Install the required dependencies:

```bash
pip install -U langchain langchain-openai langchain-community langchain-classic faiss-cpu tiktoken
```

2. Set up your Azure OpenAI credentials in the notebook:

- `AZURE_OPENAI_API_KEY`
- `azure_endpoint`
- `api_version`
- embedding deployment name
- chat deployment name

3. Run all cells in `main.ipynb`.

## Example query

```python
query = "What is the return policy?"
result = qa_chain.invoke({"query": query})
print(result["result"])
```

## Notes

- Add or update new FAQ entries in `faq.txt` to expand the knowledge base.
- Keep API keys and secrets in environment variables instead of hardcoding them in source files.
- This is a lightweight demo RAG implementation intended for learning and experimentation.

## Example use case

This project is useful for small business support systems where answers can be retrieved from a FAQ document and answered conversationally without building a full custom backend.
