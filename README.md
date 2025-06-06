# Product Query Assistant

A smart AI assistant that helps you quickly search, compare, and answer questions across product catalogs (spreadsheets or PDFs).

If you have any questions or would like to collaborate, feel free to reach out to me on [LinkedIn](https://www.linkedin.com/in/jenya-stoeva-60477249/). You're more than welcome!

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/19bQ3qQ9f5jrSQD_LZX09VMDxQ36szVrE?usp=sharing) <br>
▶️ Watch on [YouTube](https://youtu.be/642B-84-dJo) <br>


## How It Works

The Product Query Assistant is a LangGraph-based workflow that enables semantic search and querying over structured product catalogs. It supports two modes:

1. **Product Ingestion -> Product Search & Answering** – Parses Excel files, extracts product data, and embeds it using OpenAI’s `text-embedding-3-large` into a persistent ChromaDB vector store. It then proceeds to answer the user’s question based on the embedded data.
2. **Product Search & Answering** – Accepts natural language queries, performs similarity search over embedded data, and uses GPT-4o to filter and return relevant product matches via structured tool-calling.

## Technical Highlights
- **Frameworks**: [LangGraph](https://github.com/langchain-ai/langgraph), [LangChain](https://github.com/langchain-ai/langchain)
- **LLM**: OpenAI ```gpt-4o``` used for structured tool calls and reasoning over search results
- **Embeddings**: OpenAI ```text-embedding-3-large``` for high-quality vector representations of product data
- **Vector Store**: ChromaDB (persistent) for similarity search across all embedded product entries
- **Control Flow**: LangGraph state machine routes based on whether new files need processing
- **File Handling**: Automatically detects and embeds only unprocessed Excel files; avoids rework
- **Output**: Structured product matches returned as a clean DataFrame, one row per relevant product

This agent is ideal for building intelligent product assistants that support catalog search, product comparison, and natural language interaction.

![workflow_graph](https://github.com/user-attachments/assets/461230ac-bebc-4656-a808-c3cc7fc6f986)


## How-To

Find the ```run_agent``` at the end of the Notebook and configure the three fields as follows: 

1. Enter your question in the ```user_input``` field. See the execution output in the notebook for an example.
2. Pass to ```file_paths``` the list of all .xlsx files you would like to compare products from. Currently, only files with single spreadsheet are supported. Multi-sheet files support is coming in the next version.

```
state = run_agent(
    user_input="Show me some vegetable planter options.",
    file_paths=["Gardening_Products_1.xlsx","Gardening_Products_2.xlsx"], 
    search_results_count=15
)
```

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
 * In JupyterLab, use the "Open from Path" option to load ```ProductQueryAssistant.ipynb```
 * Similarly, load ```.env``` and populate the variable keys with appropriate values.
 * See requirements.txt for the needed libraries.
   
### Step 3: Run the Jupyter Notebook

To execute the notebook, select each cell and press ```Shift + Enter```.

