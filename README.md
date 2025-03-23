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

## How-to

## Intallation

<b>Prerequisites</b>

* Access to <b>JupyterLab, Google Colab</b>, or another interactive computing environment to run this Jupyter Notebook.

### Step 1: Clone the Repository

Clone this repository to your local machine:
```
git clone <REPOSITORY_URL>
cd <PROJECT_FOLDER>
```

### Step 2: Open Jupyter Notebook in JupyterLab

Ensure that ```<PROJECT_FOLDER>``` is accessible in JupyterLab by setting it as your working directory in JupyterLab.
 * In JupyterLab, use the "Open from Path" option to load ```ProductQueryAssistant.ipynb```.
 * Similarly, load ```.env``` and populate the variable keys with appropriate values.
 * The first cell in the Notebook installs the required libraries: **%pip install langchain langgraph pandas openai langchain-openai langchain-core chromadb python-dotenv pydantic**

### Step 3: Run the Jupyter Notebook

To execute the notebook, select each cell and press ```Shift + Enter```.

