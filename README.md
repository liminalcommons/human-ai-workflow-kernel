# README: A Self-Documenting Artifact

## Welcome to the Human-AI Workflow Kernel

This repository provides a **configuration kernel** for building self-documenting, Human-AI collaborative workflows. Instead of complex scripts, you define content generation and artifact assembly using structured JSON files, guided by the schemas in the `schemas/` directory.

This approach allows teams (including AI assistants) to reproducibly generate various artifacts like documentation, tests, or even code scaffolding.

**Key Documents:**

*   **This README:** Explains its own generation as an example.
*   **`KERNEL.md`:** Describes the core concepts, schemas, and how to extend the kernel.

## How This README is Generated (Example Workflow)

This `README.md` file serves as a simple demonstration of the workflow:

1.  **Content Definition (`configs/content/readme/readme-content.json`):** This file defines this introductory section and the section you are currently reading. It uses the `content-schema.json` schema and includes descriptions, example outputs (used for this demo), and fields for tracking Human-AI collaboration (`generation_source`, `review_status`).

2.  **Artifact Definition (`configs/artifacts/readme-artifact.json`):** This file, based on `artifact-schema.json`, orchestrates the assembly. It points to the `readme-content.json` above, specifies how to retrieve the content (`retrievalStrategy: latest`), how to combine sections (`compositionStrategy: concat`), and defines the final output file (`README.md`). It also marks the content as requiring review (`review_required: true`).

3.  **Generation Simulation:** In this repository (which focuses on the *kernel definition*), we simulate the generation by concatenating the `example_output` fields from the content config. A full implementation would involve a tool that reads the artifact config, resolves content based on the strategy, potentially uses AI based on `prompt_guidance` if no pre-generated content exists, performs validation based on schema rules, and writes the final `README.md`. 