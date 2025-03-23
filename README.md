# Product Query Assistant

A smart assistant designed to help yoy quickly find, compare, and retrieve accurate product information from your catalog. 

## 🧠 Product Intelligence Agent – Technical Summary

The Product Intelligence Agent is a LangGraph-based workflow that enables semantic search and querying over structured product catalogs. It supports two modes:

1. **Product Ingestion** – Parses Excel files, extracts product data, and embeds it using OpenAI’s `text-embedding-3-large` into a persistent ChromaDB vector store.
2. **Product Search & Answering** – Accepts natural language queries, performs similarity search over embedded data, and uses GPT-4o to filter and return relevant product matches via structured tool-calling.

### 🔧 Technical Highlights
- **Frameworks**: [LangGraph](https://github.com/langchain-ai/langgraph), [LangChain](https://github.com/langchain-ai/langchain)
- **LLM**: OpenAI `gpt-4o` for answer generation and tool-based reasoning
- **Embeddings**: OpenAI `text-embedding-3-large`
- **Vector Store**: ChromaDB with persistent storage
- **Workflow Control**: State machine with conditional routing (file processing vs. search)
- **Output**: Structured JSON response containing relevant product entries, easily renderable as a table or API response

This agent is ideal for building intelligent product assistants that support catalog search, product comparison, and natural language interaction.

