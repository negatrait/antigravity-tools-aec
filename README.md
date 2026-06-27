# agentic-aec-tools
Tools and integrations to extend agent harnesses (like Google Antigravity, Claude Desktop, Hermes Agent, etc.) specifically for Architecture, Engineering, and Construction (AEC) scenarios.

While frameworks like Antigravity 2.0 shipped with great capabilities for the toolstack the AEC community uses, this repository aims to be **runtime-agnostic**. The goal is to provide a standardized set of tools, Model Context Protocol (MCP) servers, and runtime-agnostic Python hooks that can be plugged into any agentic runtime.

## Core Architect Needs

The modern Architect requires a synthetic coworker to assist with a variety of specialized tasks. This repository aims to provide agents with the capabilities to handle:

- **Compliance checking:** Automatically validating models and plans against building codes, client briefs, and environmental regulations.
- **Schedules and time tables:** Interfacing with project schedules to predict delays or optimize the timeline based on the current model state.
- **Project management:** Summarizing meeting minutes, tracking changes, and communicating constraints across the multi-disciplinary team.
- **Designs and plans in CAD/BIM:** Reading, visualizing, and reasoning over 3D models (IFC, Revit) and 2D plans.

## Goal

The goal is to create a set of MCP configurations, tools, and Python hooks which you can simply clone to a local drive, plug into your preferred Agent Harness, and go do business as usual.

In general, the whole point is, in priority order, to give agents the ability to:
1. Access your project context
2. Reason over your project context
3. Report based on your project context
4. Publish and deploy your project files (the deliverables)
5. Suggest modifications to your project
6. Implement modifications to your project

The basic MVP is an agent that can actually see the same data as the designer sees. Meaning, able to read with standard MCP servers and browser tools, without any particular skills or reasoning.

If that's 0.1.0, 0.2.0 becomes the release that can actually reason over the data sources and documents, e.g. "live annualised CO2 prediction" or "Always up to date visualisations" and so on.

The first step is the ability to ragify project data. [Cocoindex](https://github.com/cocoindex-io/cocoindex) seems like a plausible candidate for that.

## References

For reference, tools to integrate or use, in random order:
- [solibri-toolkit](https://github.com/EdvardGK/solibri-toolkit), for integrating with Solibri.
- [IFC OpenShell](https://github.com/IfcOpenShell/IfcOpenShell), includes an MCP server.
- [ifc-lite](https://github.com/LTplus-AG/ifc-lite), for viewing IFCs inside a browser - give eyes to the Agent.
- [RevitMCPBridge](https://github.com/WeberG619/RevitMCPBridge2026), for working with Revit.
- [speckle-server](https://github.com/specklesystems/speckle-server), for when you actually want a CDE.
- [OfficeMCP](https://github.com/OfficeMCP/OfficeMCP), for the other documents.
- [kreuzberg](https://github.com/kreuzberg-dev/kreuzberg), for when someone sends that pesky weird document format.

For the full tech stack, potential candidates:
- cocoindex
- elastic search
- https://github.com/jrastas/ifc-tarkistaja

Then, let's imagine we have the above set up. That means we have one unexplored opportunity: The LLM-Wiki pattern. What essentially emerges:
1. The structured and unstructured data is the `raw/` of the project.
2. The agent reasons over the ontologies to produce the `wiki/` of the project.
 - Claims, contradictions, linting
 - What ends up in that wiki when someone constantly maintains it?
 - Can you reason over "all the project wikis"? The company brain?
