# User Stories: Antigravity AEC Integrations

## MVP (v0.1.0) - Read-Only Chat & Semantic Reasoning

### Semantic Graph & Ontology Reasoning (Open Ontologies)
1. **As a BIM Manager**, I want Antigravity to ingest my architectural IFC model into the Open Ontologies graph, so that the data is represented in a standard, queryable RDF format.
2. **As an Architect**, I want to ask Antigravity complex relational questions like "Which load-bearing walls are directly supporting the roof structure?", so that the Open Ontologies OWL2-DL reasoner can infer the answer even if it wasn't explicitly modeled that way in Revit.

### IFC & Model Data
4. **As an Architect**, I want to ask Antigravity "How many doors are in the current IFC model?", so that I don't have to manually open Navisworks or Solibri to count them.
5. **As an Architect**, I want to ask Antigravity to list the fire ratings of all load-bearing walls in the IFC, so that I can quickly verify compliance against the project brief.
6. **As a BIM Manager**, I want Antigravity to use `ifc-lite` in the browser to "look" at the model and describe the general layout of the ground floor, so that the agent has visual context of the project.

### Revit Integration
7. **As an Architect**, I want to ask Antigravity "What is the total sqm of the rooms currently selected in my open Revit session?", so that I can quickly generate area reports without creating new Revit schedules.
8. **As an Architect**, I want to query Antigravity about the warnings generated in my current Revit file, so that I can get suggestions on how to resolve them.

### Document & Context Integration
9. **As an Architect**, I want to ask Antigravity to check my current model against the requirements listed in the `Project_Brief.pdf` (read via OfficeMCP), so that I can ensure the design meets client specifications.
10. **As a Project Manager**, I want to ask Antigravity to summarize the latest meeting minutes from `Client_Meeting.docx`, so that I can quickly recall the requested design changes.

---

## Phase 2 (v0.2.0) - Continuous Sync & Autonomous Triggers

### Live RAG & Incremental Indexing (Cocoindex)
11. **As an Architect**, I want my unstructured project files (PDFs, Docx) to be continuously indexed by Cocoindex in the background, so that Antigravity always has sub-second access to the absolute latest project context.
12. **As an Architect**, I want Antigravity to seamlessly cross-reference unstructured data ("What did the client want for the lobby floor?") with structured ontology data ("What is the current material assigned to the lobby floor in the graph?"), so that I get comprehensive answers.

### Autonomous Triggers & Reporting
13. **As an Architect**, I want Antigravity to automatically wake up and analyze the model whenever I save a new version of the IFC, so that it can preemptively alert me to clashing elements or code violations.
14. **As an Architect**, I want the agent to automatically generate a "Live Annualised CO2 Prediction" report based on the materials currently in the model, so that I have real-time feedback on the sustainability of my design choices.
15. **As a BIM Manager**, I want Antigravity to autonomously cross-reference newly received consultant models (e.g., Structural IFC) with the Architectural IFC and summarize the major semantic discrepancies in my chat window.
