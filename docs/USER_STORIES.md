# User Stories: Agentic AEC Tools

## Sprint 1 MVP (v0.1.0) - Read-Only Chat & Semantic Reasoning

### Semantic Graph & Ontology Reasoning (Open Ontologies)
1. **As a BIM Manager**, I want the Agent to ingest my architectural IFC model into the Open Ontologies graph, so that the data is represented in a standard, queryable RDF format.
2. **As an Architect**, I want to ask the Agent complex relational questions like "Which load-bearing walls are directly supporting the roof structure?", so that the Open Ontologies OWL2-DL reasoner can infer the answer even if it wasn't explicitly modeled that way in Revit.

### IFC & Model Data
3. **As an Architect**, I want to ask the Agent "How many doors are in the current IFC model?", so that I don't have to manually open Navisworks or Solibri to count them.
4. **As an Architect**, I want to ask the Agent to list the fire ratings of all load-bearing walls in the IFC, so that I can quickly verify compliance against the project brief.
5. **As a BIM Manager**, I want the Agent to use `ifc-lite` in the browser to "look" at the model and describe the general layout of the ground floor, so that the agent has visual context of the project.

### Revit Integration
6. **As an Architect**, I want to ask the Agent "What is the total sqm of the rooms currently selected in my open Revit session?", so that I can quickly generate area reports without creating new Revit schedules.
7. **As an Architect**, I want to query the Agent about the warnings generated in my current Revit file, so that I can get suggestions on how to resolve them.

### Architect Workflows (Compliance, Schedules, PM)
8. **As an Architect**, I want to ask the Agent to check my current model against the requirements listed in the `Project_Brief.pdf` (read via OfficeMCP), so that I can ensure the design meets client specifications and building codes (Compliance checking).
9. **As a Project Manager**, I want to ask the Agent to summarize the latest meeting minutes from `Client_Meeting.docx`, so that I can quickly recall the requested design changes.
10. **As an Architect**, I want the Agent to analyze the current project schedule and compare it to the model's progress, so that I can identify potential delays in deliverables.

---

## Sprint 2 (v0.2.0) - Continuous Sync & Autonomous Triggers

### Live RAG & Incremental Indexing (Cocoindex)
11. **As an Architect**, I want my unstructured project files (PDFs, Docx) to be continuously indexed by Cocoindex in the background, so that the Agent always has sub-second access to the absolute latest project context.
12. **As an Architect**, I want the Agent to seamlessly cross-reference unstructured data ("What did the client want for the lobby floor?") with structured ontology data ("What is the current material assigned to the lobby floor in the graph?"), so that I get comprehensive answers.
13. **As an Architect**, I want the Agent to seamlessly reason over both the structured and unstructured data in a comprehensive manner, so that my project files form the `raw` layer and the Agent surfaces the `wiki` knowledge layer from my project files in a LLM-Wiki pattern.

### Autonomous Triggers & Reporting
14. **As an Architect**, I want the Agent to automatically wake up and analyze the model whenever I save a new version of the IFC, so that it can preemptively alert me to clashing elements or code violations.
15. **As an Architect**, I want the Agent to automatically generate a "Live Annualised CO2 Prediction" report based on the materials currently in the model, so that I have real-time feedback on the sustainability of my design choices.
16. **As a BIM Manager**, I want the Agent to autonomously cross-reference newly received consultant models (e.g., Structural IFC) with the Architectural IFC and summarize the major semantic discrepancies in my chat window.

---

## Sprint 3 (v0.3.0) - The Audit Trail and Self-service Reporting

### Audit Trail
17. **As an Architect**, I want to see what the Agent has done for my project, from one comprehensive dashboard, to explain the value of a synthetic coworker to our clients.

### Self-service Reporting
18. **As the CEO of my AEC company**, I want to know simply by looking at a dashboard, what is the status and state of the project the Agent is attached to, so that my employees can focus on working.
19. **As the Client**, I want to know the state and status of my project simply by looking at a dashboard, so that I don't need to rely on reporting.
20. **As the Architect**, I want to know the status and state of the project simply by looking at a dashboard, so that I don't need to research and search the structured and unstructured documents myself.
21. **As the Architect**, I want to know the alignment of the project on the goals and KPIs set, so that design becomes a proactive process instead of a reactive one.
