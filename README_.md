# Context Engineering Course: Quiz Visuals & Case Study Trajectories

This repository contains the interactive visual applications accompanying the graded and ungraded quizzes for the **Context Engineering Course** by DeepLearning.AI.

## Course Summary

The Context Engineering Course explores the art and science of providing AI agents with the right information, in the right format, at the right time to successfully execute complex, multi-turn tasks. As agentic systems run for extended periods with minimal human intervention, they generate voluminous traces of user prompts, reasoning chains, tool schemas, and environment outputs that quickly saturate million-token context windows and trigger "context rot"—a degradation in reasoning power as context length balloons. Rather than relying on massive context windows alone, context engineering equips developers with systematic architectures for agentic search, context formatting, dynamic compaction, external memory, and deterministic harnesses to keep context tidy, accurate, and high-performing.

## Trajectories Included in this Repository

The interactive visual apps located in [`Quiz_Visuals/`](./Quiz_Visuals/) map directly to the four course modules:

- **Module 1 – Customer Service Agent (Failure Modes in Multi-Turn Agents):**
  - **Trajectory 1:** *Context Poisoning* – Ingestion of unindexed legacy policy documents leading to wrongful exchange rejection.
  - **Trajectory 2:** *Rapid Context Window Saturation* – Multi-hub freight dispatch queries with unpruned payloads exploding context usage.
- **Module 2 – FreshCart Coding Agent (Agentic Search & Retrieval):**
  - **Trajectory 1:** *Unrecovered Search Strategy Mismatches* – Natural language vector search attempting exact token matches and failing to recover.
  - **Trajectory 2:** *Severed Structural Boundaries* – Naive fixed character chunking breaking class schemas and validation logic.
- **Module 3 – Cinema Research Agent (Context Formatting & Compaction):**
  - **Trajectory 1:** *Progressive Degradation in Repeated Compaction* – Successive compaction iterations eroding critical childhood movie clues.
  - **Trajectory 2:** *Silent Externalization (Missing Pointer)* – Offloading document text to a scratchpad without supplying the external lookup pointer.
- **Module 4 – Doctor’s Appointment Assistant (Agent Memory & State Persistence):**
  - **Trajectory 1:** *Memory Writing and Semantic Duplication* – Extracting, deduplicating, and reconciling paraphrased user rules into long-term vector storage.
  - **Trajectory 2:** *Flat-File Search and Forgotten Rules* – Stateless flat-file message lookups failing to resolve semantic synonyms for appointment cancellations.

For full technical details, turn-by-turn breakdowns, and interactive links, please see the primary [README.md](./README.md).
