# Product Catalog Assistant

A smart AI assistant that helps you quickly search, compare, and answer questions across product catalogs (spreadsheets or PDFs).

If you have any questions or would like to collaborate, feel free to reach out to me on [LinkedIn](https://www.linkedin.com/in/jenya-stoeva-60477249/). You're more than welcome!

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/19bQ3qQ9f5jrSQD_LZX09VMDxQ36szVrE?usp=sharing) <br>
▶️ Watch on [YouTube](https://youtu.be/642B-84-dJo) <br>

[![Watch on YouTube](https://img.shields.io/badge/Watch%20on-YouTube-red?logo=youtube&style=for-the-badge)](https://www.youtube.com/watch?v=YOUR_VIDEO_ID)



## How It Works

The Product Query Assistant is a LangGraph-based workflow that enables semantic search and querying over structured product catalogs. It supports:

1. **Smart Product Ingestion (Conditional)** – Automatically checks if uploaded Excel files have already been processed. If not, it extracts structured product data and embeds it into a persistent ChromaDB vector store using OpenAI’s text-embedding-3-large. If already processed, it skips ingestion entirely.
2. **Product Search & Answering** – Accepts natural language queries, performs a similarity search over embedded product data, and uses GPT-4o with tool-calling to return only the most relevant matches in a structured, user-friendly format.

## Technical Highlights
- **Frameworks**: [LangGraph](https://github.com/langchain-ai/langgraph), [LangChain](https://github.com/langchain-ai/langchain)
- **LLM**: OpenAI ```gpt-4o``` used for structured tool calls and reasoning over search results
- **Embeddings**: OpenAI ```text-embedding-3-large``` for high-quality vector representations of product data
- **Vector Store**: ChromaDB (persistent) for similarity search across all embedded product entries
- **Control Flow**: LangGraph state machine routes based on whether new files need processing
- **File Handling**: Automatically detects and embeds only unprocessed Excel files; avoids rework
- **Output**: Structured product matches returned as a clean DataFrame, one row per relevant product

![workflow_graph](https://github.com/user-attachments/assets/461230ac-bebc-4656-a808-c3cc7fc6f986)


## How-To

Find the ```run_agent``` at the end of the Notebook and configure the three fields as follows: 

1. Enter your question in the ```user_input``` field. See the execution output in the notebook for an example.
2. Pass to ```file_paths``` the list of all .xlsx files you would like to compare products from. Currently, only files with single spreadsheet are supported. Multi-sheet files support is coming in the next version.
3. Specify seearch result number. It tells the agent how many product entries to retrieve from the database based on your question.

```
state = run_agent(
    user_input="Show me some vegetable planter options.",
    file_paths=["Gardening_Products_1.xlsx","Gardening_Products_2.xlsx"], 
    search_results_count=15
)
```

