# antigravity-tools-aec
Tools to extend Google Antigravity specifically for AEC scenarios

Antigravity 2.0 shipped, and it's the first (to my knowledge) agent harness that bends well to the toolstack the AEC community uses.

1. It's Windows native.
2. It has all the hooks and sdk's that are needed for wiring up the connections to tools the AEC pros use.
3. It's able to shell out to WSL for wider compatibility.

The basic integration building block is the [Antigravity SDK](https://github.com/google-antigravity/antigravity-sdk-python)

## Goal

The goal is to create a set of configs and executables which you can simply clone to a local drive, plug in to Antigravity, and go do business as usual.

In general, the whole point is, in priority order, to give Antigravity the ability to:
1. Access your project context
2. Reason over your project context
3. Report based on your project context
4. Publish and deploy your project files (the deliverables)
5. Suggest modifications to your project
6. Implement modifications to your project

So, the basic MVP is an agent that cam actually see the same data as the designer sees. Meaning, able to read with MCP and browser tools, without any particular skills or reasoning.

If that's 0.1.0, 0.2.0 becomes the release that can actually reason over the data sources and documents, e.g. "live annualised CO2 prediction" or "Allways up to date visualisations" and so on.

First step is thus the ability to ragify project data. Cocoindex seems like a plausible candidate for that.

## References

For reference, tools to integrate or use, in random order:
- [solibri-toolkit](https://github.com/EdvardGK/solibri-toolkit), for integrating with Solibri.
- [IFC OpenShell](https://github.com/IfcOpenShell/IfcOpenShell), includes an MCP server.
- [ifc-lite](https://github.com/LTplus-AG/ifc-lite), for viewing IFC's inside a browser - give eyes to Antigravity.
- [RevitMCPBridge](https://github.com/WeberG619/RevitMCPBridge2026), for working with Revit.
- [speckle-server](https://github.com/specklesystems/speckle-server), for when you actually want a CDE.
- [OfficeMCP](https://github.com/OfficeMCP/OfficeMCP), for the other documents.
- [kreuzberg](https://github.com/kreuzberg-dev/kreuzberg), for when someone sends that pesky weird document format.

For the full tech stack, potential candidates:
- cocoindex
- elastic search
