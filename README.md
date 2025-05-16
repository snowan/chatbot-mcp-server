# Chatbot MCP Server

## Overview

This repository implements an MCP-compatible research assistant chatbot system. It consists of:
- An MCP server that exposes research tools for searching and extracting arXiv paper information.
- An MCP client chatbot that interacts with the server and uses an LLM (Anthropic Claude) to process user queries and call tools.
- Jupyter notebooks that provide educational lessons, demos, and development workflows.

## About This Project

This project follows the DeepLearning.AI course on understanding MCP (Model Context Protocol) and building a chatbot server as a demo. For more details and learning resources, see:

[MCP: Build Rich-Context AI Apps with Anthropic (DeepLearning.AI Short Course)](https://www.deeplearning.ai/short-courses/mcp-build-rich-context-ai-apps-with-anthropic/)

## Main Components

- **`research_server.py`**:  
  The MCP server, exposing two tools:
  - `search_papers(topic, max_results)`: Search arXiv and save paper metadata.
  - `extract_info(paper_id)`: Retrieve metadata for a specific paper.

- **`mcp_chatbot.py`**:  
  The MCP client chatbot, which:
  - Connects to the server via stdio.
  - Uses Anthropic Claude for LLM-based chat.
  - Handles tool-calling and interactive chat loop.

- **Jupyter Notebooks**:  
  - Provide step-by-step lessons on building the server, client, and integrating with MCP.
  - Include code examples, explanations, and environment setup instructions.

## Dependencies

- Python 3.13+
- `anthropic` (LLM API)
- `arxiv` (arXiv API)
- `mcp` (MCP protocol client/server)
- `nest-asyncio`, `python-dotenv`
- (See `pyproject.toml` for details)

## Installation

1. **Clone the repository:**
   ```bash
   git clone <repo-url>
   cd chatbot-mcp-server
   ```

2. **Set up a virtual environment:**
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   # or, if using uv:
   uv pip install -r requirements.txt
   ```

4. **Set up environment variables:**
   - Create a `.env` file with your Anthropic API key and any other required variables.

## Usage

### Running the MCP Server

```bash
uv run research_server.py
```
- This starts the server and exposes the research tools via MCP protocol.

### Running the Chatbot Client

```bash
python mcp_chatbot.py
```
- This launches the interactive chatbot, which connects to the server and allows you to query research papers.

## Example Workflow

1. Start the server (`uv run research_server.py`).
2. In another terminal, start the chatbot (`python mcp_chatbot.py`).
3. Type a research query (e.g., "Find recent papers on quantum computing").
4. The chatbot will use the LLM to process your query, call the appropriate tool, and return results.

## Notebooks and Demos

- **chatbot-mcp-client.ipynb**:  
  Lesson on building the MCP client chatbot.
- **chatbot-mcp-server-demo.ipynb**:  
  Lesson on building the MCP server.
- **chatbot-demo.ipynb**:  
  Standalone chatbot example.
- **chatbot-mcp-server.ipynb**:  
  Full example integrating server and client.

These notebooks are recommended for step-by-step learning and experimentation.

## Project Structure

```
chatbot-mcp-server/
├── mcp_chatbot.py
├── research_server.py
├── main.py
├── papers/
├── .venv/ or venv/
├── pyproject.toml
├── uv.lock
├── .python-version
├── README.md
├── *.ipynb (notebooks)
└── .gitignore
```

## Contributing

Contributions are welcome! Please open issues or submit pull requests for improvements, bug fixes, or new features.

