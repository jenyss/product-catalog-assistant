# Product Query Assistant

A smart assistant designed to help yoy quickly find, compare, and retrieve accurate product information from your catalog. 

If you have any questions or would like to collaborate, feel free to reach out to me on [LinkedIn](https://www.linkedin.com/in/jenya-stoeva-60477249/). You're more than welcome!

## How-To

Find the ```run_agent``` at the end of the Notebook and configure the three fields as follows: 

2. Enter your question in the ```user_input``` field. See the execution output in the notebook for an example.
3. Pass to ```file_paths``` the list of all .xlsx files you would like to compare products from. Currently, only files with single spreadsheet are supported. Multi-sheet files support is coming in the next version.
4. If you have added new files for extraction then set ```file_processing=True```, else set it to ```file_processing=False```. **Important** Only embed data from a file once. Repeated embedding will pollute the database. If you do so then you can reset the DB and re-embed all documents. To do this, run the second cell to reset ChromaDB.

```
state = run_agent(
    user_input="Get all drill tools, including the german ones and their prices. Merge the table to list the german and the english name under Product.",
    file_processing=False,
    file_paths=["construction_products_english.xlsx", "construction_products_german.xlsx"]
)
```

## How It Works

The Product Query Assistant is a LangGraph-based workflow that enables semantic search and querying over structured product catalogs. It supports two modes:

1. **Product Ingestion -> Product Search & Answering** – Parses Excel files, extracts product data, and embeds it using OpenAI’s `text-embedding-3-large` into a persistent ChromaDB vector store. It then proceeds to answer the user’s question based on the embedded data.
2. **Product Search & Answering** – Accepts natural language queries, performs similarity search over embedded data, and uses GPT-4o to filter and return relevant product matches via structured tool-calling.

## Technical Highlights
- **Frameworks**: [LangGraph](https://github.com/langchain-ai/langgraph), [LangChain](https://github.com/langchain-ai/langchain)
- **LLM**: OpenAI `gpt-4o` for answer generation and tool-based reasoning
- **Embeddings**: OpenAI `text-embedding-3-large`
- **Vector Store**: ChromaDB with persistent storage
- **Workflow Control**: State machine with conditional routing (file processing vs. file processing & search)
- **Output**: Structured JSON response containing relevant product entries, easily renderable as a table or API response

This agent is ideal for building intelligent product assistants that support catalog search, product comparison, and natural language interaction.

![LangGraph Workflow](https://github.com/jenyss/ProductQueryAssistant/blob/main/workflow_graph.png)


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

