# Product Requirements Document: Antigravity AEC Integrations

## 1. Introduction
The purpose of this project is to extend Google Antigravity with a suite of integrations tailored specifically for the Architecture, Engineering, and Construction (AEC) community. By providing configurations, skills, and tools, AEC professionals (starting with Architects) will be able to plug Antigravity directly into their existing toolstack (Revit, IFCs, standard documents, and semantic graphs) to reason over and interact with their project data.

## 2. Target Audience
- **Primary:** Architects and BIM Managers who need quick, intelligent access to project data, models, and documentation without manually opening and searching through multiple heavy applications.
- **Secondary:** Company owners and Management, Clients.

## 3. Product Goals & Vision
The ultimate vision is an autonomous agent that can access, reason over, report on, suggest modifications, and eventually implement changes across a project's entire data context.

To achieve this, the product will be released in phases:
- **Sprint 1 MVP (v0.1.0):** Read-only access to project data via Model Context Protocol (MCP) servers, browser tools, and a local semantic graph engine (Open Ontologies). Initiated via user chat.
- **Sprint 2 (v0.2.0):** Autonomous reasoning workflows, continuous data syncing (Cocoindex) for live project context, and cross-discipline data alignment.

## 4. MVP Scope (v0.1.0)
The MVP will focus on a "Read-Only" experience where the user initiates commands through the Antigravity chat interface. A key feature of the MVP is the introduction of a semantic graph to bridge different AEC data silos.

### 4.1. Core Tool Integrations
The following tools will be integrated via Antigravity configurations (and Python hooks where necessary):
1. **Open Ontologies MCP:** A local RDF/SPARQL graph engine. Structured data (from IFC or Revit) will be ingested here. It allows Antigravity to perform true logical reasoning (OWL2-DL) and query complex relationships (e.g., "What structural elements support this roof?") using standard AEC ontologies.
2. **IFC OpenShell MCP:** Allow Antigravity to read and extract data from IFC models. Extracted data can be fed into the Open Ontologies graph.
3. **RevitMCPBridge:** Allow Antigravity to interface with running Revit instances to read project data.
4. **OfficeMCP:** Allow Antigravity to read standard project documentation (Word, Excel, PDF).
5. **ifc-lite (Browser Tool):** Provide Antigravity the ability to visually inspect IFC models via browser automation.

### 4.2. Repository Structure & Configuration
The integration will be packaged as a repository that users can clone locally. It will contain:
- `configs/`: Antigravity configuration files defining the tools, MCP servers, and agent skills.
- `hooks/`: Python scripts leveraging the Antigravity SDK for custom logic or trigger events.
- `docs/`: Documentation for setup and usage.

### 4.3. Antigravity Configuration Structure
To standardize the deployment of these tools, the repository will adhere to the following structure expected by Antigravity:

```text
antigravity-tools-aec/
├── configs/
│   ├── plugins/
│   │   ├── open-ontologies-mcp.yaml # Config for the local semantic graph & reasoning engine
│   │   ├── ifcopenshell-mcp.yaml    # Config to start/connect to the IFC OpenShell MCP server
│   │   ├── revit-mcp.yaml           # Config to connect to the RevitMCPBridge
│   │   └── office-mcp.yaml          # Config for reading standard documents
│   ├── skills/
│   │   ├── aec_reasoning.yaml       # Instructions for using SPARQL and OWL reasoning
│   │   └── aec_general.yaml         # System prompts for standard AEC workflows
│   └── workflows/
│       └── project_summary.yaml     # Pre-defined routines (e.g., checking IFC vs PDF requirements)
├── hooks/
│   ├── ingest_to_ontology.py        # Python SDK hook to pipe IFC/Revit data into Open Ontologies
│   └── preprocess_ifc.py            # Python SDK hook for formatting data before it hits the LLM
├── sidecars/                        # Any necessary daemon processes
└── docs/
    ├── PRD.md
    └── USER_STORIES.md
```

## 5. Future Architecture: Continuous Sync & RAG (Phase 2)
While the MVP establishes the semantic graph (Open Ontologies) for structured data and reasoning, Phase 2 will introduce **Cocoindex** to handle the continuous ingestion of unstructured data.

### 5.1. The Dual Backend Strategy
- **Open Ontologies (Structured):** Manages the "Digital Twin" graph. It holds the relationships between walls, doors, spaces, and materials, allowing for exact SPARQL queries and logical inference.
- **Cocoindex (Unstructured):** An incremental indexing engine for documents, PDFs, meeting minutes, and emails. It watches project directories and updates a vector database in real-time.
- **Integration:** Antigravity will be able to cross-reference data. For example, querying Cocoindex for "What did the client say about the lobby doors?", and then querying Open Ontologies for "Show me the current fire rating of all doors located in the Lobby space."

## 6. Non-Goals (For MVP)
- Writing data back to models (modifying IFCs or Revit files).
- Autonomous agent triggers (e.g., waking the agent automatically on file save).
- Cloud deployment (The solution is strictly local/Windows native).
