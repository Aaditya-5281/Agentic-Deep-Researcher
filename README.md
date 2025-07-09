# Agentic Deep Researcher

## Project Introduction

**Agentic Deep Researcher** is an advanced, AI-powered research assistant designed to automate and enhance the process of gathering, analyzing, and synthesizing information from the web. By leveraging multi-agent orchestration, integration with external APIs, and a user-friendly web interface, this project demonstrates how modern AI tools can be combined to deliver deep, actionable insights with minimal human intervention.

### Key Features

1. **Multi-Agent Orchestration with CrewAI**
   - The core of the system is built on the CrewAI framework, which allows for the creation and management of multiple specialized AI agents.
   - Each agent is assigned a specific role (e.g., Web Searcher, Research Analyst, Technical Writer) and collaborates with others to break down complex research tasks into manageable steps.

2. **Web Search Integration via LinkUp API**
   - The project integrates the LinkUp API (using the `linkup-sdk`), enabling agents to perform both standard and deep web searches.
   - This allows the system to access a wide range of information sources, including those not easily found through traditional search engines.

3. **Interactive Web Interface with Streamlit**
   - Users interact with the system through a modern, intuitive web interface built with Streamlit.
   - The interface allows users to submit research queries, configure API keys, and view results in a conversational, chat-like format.

4. **MCP (Model Context Protocol) Server Capability**
   - The project exposes its research functionality as an MCP tool using the `mcp` package.
   - This means the research agent can be called programmatically by other systems or automation tools that support the Model Context Protocol, making it suitable for integration into larger workflows.

5. **Process Transparency and Visualization**
   - The system is designed to not only provide answers but also to show the process and sources used in generating those answers.
   - This transparency builds trust and allows users to verify the information provided.

### How It Works

1. **User Interaction**
   - The user enters a research question into the Streamlit web app.
   - The app collects the query and any necessary configuration (like API keys).

2. **Agentic Research Pipeline**
   - The query is passed to the `run_research` function in `agents.py`.
   - CrewAI orchestrates a team of agents:
     - **Web Searcher:** Finds relevant information and sources.
     - **Research Analyst:** Analyzes and synthesizes the raw data.
     - **Technical Writer:** Produces a clear, well-structured response with citations.

3. **External Data Access**
   - The agents use the LinkUp API to perform deep web searches, ensuring comprehensive coverage of the topic.

4. **Result Delivery**
   - The final, synthesized answer is displayed to the user in the web app.
   - Optionally, the same research process can be triggered programmatically via the MCP server interface.

### Technologies Used

- **Python 3.11+**
- **CrewAI:** Multi-agent orchestration framework.
- **LinkUp SDK:** For web search and data retrieval.
- **Streamlit:** For building the interactive web UI.
- **MCP:** For exposing the research agent as a programmable tool/server.
- **Pydantic, dotenv, and other modern Python libraries.**

### Typical Use Cases

- **Academic Research:** Quickly gather and synthesize information from diverse sources.
- **Business Intelligence:** Automate competitive analysis or market research.
- **Technical Writing:** Generate well-cited, structured reports on complex topics.
- **Personal Knowledge Management:** Use as a personal research assistant for any topic.

### Project Structure

- `app.py`: Streamlit web application for user interaction.
- `agents.py`: Defines the research agents and the orchestration logic.
- `server.py`: Exposes the research agent as an MCP tool/server.
- `pyproject.toml`: Project and dependency management.
- `README.md`: Documentation and setup instructions.

### Why Is This Project Important?

This project demonstrates the power of combining:
- Multi-agent AI systems,
- External data APIs,
- Modern web interfaces,
- Model Context Protocol (MCP).

It serves as a template for building intelligent, extensible research assistants and showcases best practices in modern Python project development.

---

### SetUp

Run these commands in project root

```
uv sync
```


### Run the Application

Run the application with:

```bash
streamlit run app.py
```

### Use as MCP server

```json
{
  "mcpServers": {
    "crew_research": {
      "command": "uv",
      "args": [
        "--directory",
        "./Multi-Agent-deep-researcher-mcp",
        "run",
        "server.py"
      ],
      "env": {
        "LINKUP_API_KEY": "your_linkup_api_key_here"
      }
    }
  }
}
```
[Get your Linkup API keys here](https://www.linkup.so/)


## Contribution

Contributions are welcome! Feel free to fork this repository and submit pull requests with your improvements.
