# Product Requirements Document: Agentic AEC Tools

## 1. Introduction
The purpose of this project is to provide a standardized, runtime-agnostic suite of tools, hooks, and integrations tailored specifically for the Architecture, Engineering, and Construction (AEC) community. By providing these MCP configurations and Python skills, AEC professionals (starting with Architects) will be able to plug any standard Agent Harness (e.g., Claude Desktop, Hermes Agent, Antigravity) directly into their existing toolstack (Revit, IFCs, standard documents, and semantic graphs) to reason over and interact with their project data.

## 2. Target Audience
- **Primary:** Architects and BIM Managers who need quick, intelligent access to project data, models, and documentation without manually opening and searching through multiple heavy applications.
- **Secondary:** Company owners and Management, Clients.

## 3. Product Goals & Vision
The ultimate vision is an autonomous agent that can access, reason over, report on, suggest modifications, and eventually implement changes across a project's entire data context.

Agents will act as synthetic coworkers that assist the Architect with:
- **Compliance checking:** Validating designs against codes and briefs.
- **Schedules and time tables:** Managing and analyzing project schedules.
- **Project management:** Tracking meeting minutes and communications.
- **Designs and plans in CAD/BIM:** Processing and visualizing BIM models.

To achieve this, the product will be released in phases:
- **Sprint 1 MVP (v0.1.0):** Read-only access to project data via Model Context Protocol (MCP) servers, browser tools, and a local semantic graph engine (Open Ontologies). Initiated via user chat.
- **Sprint 2 (v0.2.0):** Autonomous reasoning workflows, continuous data syncing (Cocoindex) for live project context, and cross-discipline data alignment.

## 4. MVP Scope (v0.1.0)
The MVP will focus on a "Read-Only" experience where the user initiates commands through their preferred Agent chat interface. A key feature of the MVP is the introduction of a semantic graph to bridge different AEC data silos.

### 4.1. Core Tool Integrations
The following tools will be integrated via standard MCP servers (and runtime-agnostic Python tools/hooks where necessary):
1. **Open Ontologies MCP:** A local RDF/SPARQL graph engine. Structured data (from IFC or Revit) will be ingested here. It allows the Agent to perform true logical reasoning (OWL2-DL) and query complex relationships (e.g., "What structural elements support this roof?") using standard AEC ontologies.
2. **IFC OpenShell MCP:** Allow the Agent to read and extract data from IFC models. Extracted data can be fed into the Open Ontologies graph.
3. **RevitMCPBridge:** Allow the Agent to interface with running Revit instances to read project data.
4. **OfficeMCP:** Allow the Agent to read standard project documentation (Word, Excel, PDF).
5. **ifc-lite (Browser Tool):** Provide the Agent the ability to visually inspect IFC models via browser automation.

### 4.2. Repository Structure & Configuration
The integration will be packaged as a repository that users can clone locally. To ensure compatibility with standard MCP clients (like Claude Desktop) and generic agent frameworks, the repository will adhere to the following structure:

```text
agentic-aec-tools/
├── mcp-servers/
│   ├── open-ontologies-mcp.json # Standard MCP config for the semantic graph
│   ├── ifcopenshell-mcp.json    # Standard MCP config for IFC OpenShell
│   ├── revit-mcp.json           # Standard MCP config for RevitMCPBridge
│   └── office-mcp.json          # Standard MCP config for standard documents
├── tools/
│   ├── aec_reasoning/           # Generic Python tools/skills for reasoning
│   ├── data_ingestion/          # Generic Python scripts for processing IFC/Revit
│   └── project_management/      # Generic Python tools for scheduling/compliance
├── docs/
│   ├── PRD.md
│   └── USER_STORIES.md
```

## 5. Future Architecture: Continuous Sync & RAG (Phase 2)
While the MVP establishes the semantic graph (Open Ontologies) for structured data and reasoning, Phase 2 will introduce **Cocoindex** to handle the continuous ingestion of unstructured data.

### 5.1. The Dual Backend Strategy
- **Open Ontologies (Structured):** Manages the "Digital Twin" graph. It holds the relationships between walls, doors, spaces, and materials, allowing for exact SPARQL queries and logical inference.
- **Cocoindex (Unstructured):** An incremental indexing engine for documents, PDFs, meeting minutes, and emails. It watches project directories and updates a vector database in real-time.
- **Integration:** The Agent will be able to cross-reference data. For example, querying Cocoindex for "What did the client say about the lobby doors?", and then querying Open Ontologies for "Show me the current fire rating of all doors located in the Lobby space."

## 6. Non-Goals (For MVP)
- Writing data back to models (modifying IFCs or Revit files).
- Autonomous agent triggers (e.g., waking the agent automatically on file save).
- Cloud deployment (The solution is primarily local/Windows native).
