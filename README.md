# demo-mcp-genai

> this is for demo

Demo Gen AI project showcasing MCP and LLM integration patterns.

## Architecture

```mermaid
flowchart TD
    User(["👤 User / Client"])

    subgraph MCP["MCP Layer (Model Context Protocol)"]
        MCPServer["MCP Server"]
        Tools["🔧 Tools\n(search, execute, retrieve)"]
        Resources["📦 Resources\n(data sources, APIs)"]
        Prompts["📝 Prompt Templates"]
    end

    subgraph LLM["LLM Integration"]
        LLMModel["🤖 LLM Model\n(OpenAI / Anthropic / etc.)"]
        Context["Context Window\nManagement"]
    end

    subgraph Project["Project Structure"]
        SRC["src/\nApplication Code"]
        DATA["data/\nraw & processed"]
        NB["notebooks/\nExploration"]
        MODELS["models/\nArtifacts"]
        TESTS["tests/\nUnit & Integration"]
        DOCS["docs/\nDocumentation"]
    end

    User -->|"sends request"| MCPServer
    MCPServer --> Tools
    MCPServer --> Resources
    MCPServer --> Prompts
    Tools -->|"augmented context"| LLMModel
    Resources -->|"data retrieval"| LLMModel
    Prompts -->|"structured prompts"| Context
    Context --> LLMModel
    LLMModel -->|"response"| MCPServer
    MCPServer -->|"final output"| User

    SRC --> MCPServer
    DATA --> Resources
    NB -.->|"experimentation"| LLMModel
    MODELS -.->|"local models"| LLMModel
```

## Project Structure

```
demo-mcp-genai/
├── src/            # Application source code
├── data/
│   ├── raw/        # Original, immutable data
│   └── processed/  # Cleaned and transformed data
├── notebooks/      # Jupyter notebooks for exploration
├── models/         # Trained / exported model artifacts
├── tests/          # Unit and integration tests
└── docs/           # Project documentation
```

## Getting Started

```bash
pip install -r requirements.txt
```
