# mcp_enabled_chatbot

This is a simple command-line chatbot I built that talks to AI models using the Anthropic API. On top of normal Q&A, it supports pulling in documents and running custom commands. Under the hood, it uses **MCP (Model Control Protocol)**, which makes it easy to plug in extra tools or extend the chatbot later.  

## What you need

- Python 3.9 or above  
- An Anthropic API key (from your Anthropic account)  

## Setup

### 1. Add your API key
Create a `.env` file in the root folder and put your key like this:

ANTHROPIC_API_KEY="your-secret-key"

### 2. Install dependencies

You can set it up in two ways:

#### Option A: With [uv](https://github.com/astral-sh/uv) (faster and cleaner)

pip install uv
uv venv
source .venv/bin/activate # (on Windows: .venv\Scripts\activate)
uv pip install -e .
uv run main.py

#### Option B: Classic Python venv

python -m venv .venv
source .venv/bin/activate # (on Windows: .venv\Scripts\activate)
pip install anthropic python-dotenv prompt-toolkit "mcp[cli]==1.8.0"
python main.py

## How to use

- **Chat normally:** just type something and hit Enter.  
- **Pull in a document:** use `@` followed by the file name:  

Tell me about @deposition.md

- **Run a command:** use `/` before your command:  

/summarize deposition.md

(press Tab to auto-complete available commands)  

## Hacking on it

- Add new documents → update the `docs` dictionary in `mcp_server.py`.  
- Add new features → check the TODOs in `mcp_server.py` and `mcp_client.py`.  

No linting or type checks yet - I kept it lightweight to focus on the features.  

---

⚡ Basically, this is a playground chatbot where I’ve tried out using MCP + Anthropic together. You can extend it however you like.
