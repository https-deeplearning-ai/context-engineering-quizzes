# Context Engineering Course: Interactive Quiz Visuals

This repository contains the interactive visual web applications that accompany the quizzes and case studies in the **Context Engineering Course** by [DeepLearning.AI](https://www.deeplearning.ai/). These applications provide dynamic, turn-by-turn visualizations of agent trajectories, demonstrating how an agent's context window, token utilization, tool calls, and memory evolve during multi-step tasks—as well as the critical failure modes that occur when context is poorly managed.

🌐 **Live GitHub Pages Portal:** [https://https-deeplearning-ai.github.io/context-engineering-quizzes/](https://https-deeplearning-ai.github.io/context-engineering-quizzes/)

## Course Overview

The Context Engineering Course explores the art and science of providing AI agents with the right information, in the right format, at the right time to successfully execute complex, multi-turn tasks. As agentic systems run for extended periods with minimal human intervention, they generate voluminous traces of user prompts, reasoning chains, tool schemas, and environment outputs that quickly saturate million-token context windows and trigger "context rot"—a degradation in reasoning power as context length balloons. Rather than relying on massive context windows alone, context engineering equips developers with systematic architectures for agentic search, context formatting, dynamic compaction, external memory, and deterministic harnesses to keep context tidy, accurate, and high-performing.

---

## Interactive Trajectories & Case Studies

Each interactive visual application in [`Quiz_Visuals/`](./Quiz_Visuals/) models a real-world scenario from the course quizzes, allowing learners to step through turns and inspect context window growth, effective context limits, and specific context failure modes.

### Module 1: Failure Modes in Multi-Turn Agents

#### Trajectory 1: Customer Service Agent – Context Poisoning
* **Live Web App:** [Module 1 Trajectory 1 on GitHub Pages](https://https-deeplearning-ai.github.io/context-engineering-quizzes/Quiz_Visuals/Module_1_Trajectory_1.html)
* **Local Source:** [`Quiz_Visuals/Module_1_Trajectory_1.html`](./Quiz_Visuals/Module_1_Trajectory_1.html)
* **Description:** An online footwear retailer deploys an AI customer service agent to handle post-purchase inquiries and exchange requests. When a customer reaches out to exchange tight running shoes (Order #4412) under a newly expanded 60-day return policy, the agent queries internal documentation but inadvertently retrieves outdated, unindexed legacy files specifying a 30-day cutoff. Ingesting this contradictory, unpruned legacy policy into the context window "poisons" the agent's reasoning, causing it to erroneously reject a valid customer exchange despite having the correct facts elsewhere in its system.

#### Trajectory 2: Customer Service Agent – Rapid Context Window Saturation
* **Live Web App:** [Module 1 Trajectory 2 on GitHub Pages](https://https-deeplearning-ai.github.io/context-engineering-quizzes/Quiz_Visuals/Module_1_Trajectory_2.html)
* **Local Source:** [`Quiz_Visuals/Module_1_Trajectory_2.html`](./Quiz_Visuals/Module_1_Trajectory_2.html)
* **Description:** In a complex fulfillment exchange scenario, a customer requests same-day rerouting of footwear from any regional distribution hub with available stock. To resolve the inquiry, the customer service agent orchestrates multi-step tool calls across customer account history, nationwide warehouse inventory records, and regional freight dispatch manifests. Because tool payloads return raw, unpruned JSON containing extensive administrative metadata, the context window experiences explosive exponential growth across only a few turns, rapidly breaching the effective context limit and exhausting the model's operational budget.

---

### Module 2: Agentic Search & Retrieval

#### Trajectory 1: FreshCart Coding Agent – Unrecovered Search Strategy Mismatches
* **Live Web App:** [Module 2 Trajectory 1 on GitHub Pages](https://https-deeplearning-ai.github.io/context-engineering-quizzes/Quiz_Visuals/Module_2_Trajectory_1.html)
* **Local Source:** [`Quiz_Visuals/Module_2_Trajectory_1.html`](./Quiz_Visuals/Module_2_Trajectory_1.html)
* **Description:** A backend engineer asks an autonomous coding agent to investigate checkout latency issues by locating the exact constant `LOCK_RETRY_MAX_ATTEMPTS` in the codebase and confirming related policy limits. The agent attempts to locate the exact variable using natural language semantic vector search—which struggles with exact symbol matching—while attempting pure keyword searches for conceptual documentation. Because the agent lacks fallback heuristics or hybrid retrieval orchestration to recover from initial strategy mismatches, it wastes multiple turns and returns incomplete or irrelevant code snippets.

#### Trajectory 2: FreshCart Coding Agent – Severed Structural Boundaries (Naive Character Chunking)
* **Live Web App:** [Module 2 Trajectory 2 on GitHub Pages](https://https-deeplearning-ai.github.io/context-engineering-quizzes/Quiz_Visuals/Module_2_Trajectory_2.html)
* **Local Source:** [`Quiz_Visuals/Module_2_Trajectory_2.html`](./Quiz_Visuals/Module_2_Trajectory_2.html)
* **Description:** An autonomous coding agent is tasked with determining the permitted values and validation constraints for the `temperature_zone` attribute in an `InventoryItem` model class. However, the vector store index was built using arbitrary, fixed character-count chunking without language-aware syntax parsing. As a result, critical class definitions, decorators, and validation logic are cleaved across chunk boundaries mid-statement, depriving the agent of the syntactic context required to understand valid ranges and causing it to hallucinate unsupported attribute constraints.

---

### Module 3: Context Formatting & Compaction

#### Trajectory 1: Cinema Research Agent – Progressive Degradation in Repeated Compaction
* **Live Web App:** [Module 3 Trajectory 1 on GitHub Pages](https://https-deeplearning-ai.github.io/context-engineering-quizzes/Quiz_Visuals/Module_3_Trajectory_1.html)
* **Local Source:** [`Quiz_Visuals/Module_3_Trajectory_1.html`](./Quiz_Visuals/Module_3_Trajectory_1.html)
* **Description:** An autonomous research agent searches a comprehensive cinema database to identify an obscure animated film based on four distinct childhood memory clues provided by the user. To preserve space, the agent harness implements an automated compaction hook that triggers whenever the context window exceeds 3,500 tokens; however, rather than summarizing from original raw logs, each cycle summarizes the preceding summary alongside recent steps. Over multiple successive compaction iterations, nuanced identifiers—such as a specific jazz trumpeter score and a European jury award—are progressively diluted and lost, leaving the agent unable to isolate the target film.

#### Trajectory 2: Cinema Research Agent – Silent Externalization (Missing Pointer)
* **Live Web App:** [Module 3 Trajectory 2 on GitHub Pages](https://https-deeplearning-ai.github.io/context-engineering-quizzes/Quiz_Visuals/Module_3_Trajectory_2.html)
* **Local Source:** [`Quiz_Visuals/Module_3_Trajectory_2.html`](./Quiz_Visuals/Module_3_Trajectory_2.html)
* **Description:** While investigating fragmented cinema clues, the agent's harness attempts to preserve active context by intercepting large database query returns, offloading full document bodies to an external scratchpad store, and injecting only compressed synopsis snippets into the prompt. Crucially, the harness fails to inject the corresponding document ID or reference pointer alongside the snippet into the context window. Without this external pointer, the agent is completely blind to where the source file resides, rendering its scratchpad retrieval tool useless and stranding the evidence outside the agent's reach.

---

### Module 4: Agent Memory & State Persistence

#### Trajectory 1: Doctor’s Appointment Assistant – Memory Writing and Semantic Duplication
* **Live Web App:** [Module 4 Trajectory 1 on GitHub Pages](https://https-deeplearning-ai.github.io/context-engineering-quizzes/Quiz_Visuals/Module_4_Trajectory_1.html)
* **Local Source:** [`Quiz_Visuals/Module_4_Trajectory_1.html`](./Quiz_Visuals/Module_4_Trajectory_1.html)
* **Description:** A personal medical appointment assistant manages incoming patient portal messages and already retains a long-term vector rule to priority-flag communications from the user's primary care physician. In a new conversation, the user re-states this preference using slightly altered phrasing. The assistant's background memory extraction pipeline attempts to reconcile and deduplicate candidate rules against long-term storage, demonstrating the subtle challenges of semantic threshold tuning, duplicate entry proliferation, and conflict resolution during memory write operations.

#### Trajectory 2: Doctor’s Appointment Assistant – Flat-File Search and Forgotten Rules
* **Live Web App:** [Module 4 Trajectory 2 on GitHub Pages](https://https-deeplearning-ai.github.io/context-engineering-quizzes/Quiz_Visuals/Module_4_Trajectory_2.html)
* **Local Source:** [`Quiz_Visuals/Module_4_Trajectory_2.html`](./Quiz_Visuals/Module_4_Trajectory_2.html)
* **Description:** An AI appointment assistant operates without a dedicated vector memory store, relying instead on a stateless architecture coupled with a flat-file log of past session messages queried via literal keyword search. In an earlier session, the patient instructed the assistant to dismiss notices for "end-of-week" appointments; when a new notice arrives for a "Friday" appointment, the agent's lexical query fails to match the semantic equivalent, causing the system to forget established user preferences and forcing the patient to repetitively clarify instructions.

---

## Repository Structure

```
context-engineering-quizzes/
│
├── index.html                     # GitHub Pages interactive portal & dashboard
├── README.md                      # Repository overview, course summary, and trajectory index
├── README_.md                     # Course documentation reference
└── Quiz_Visuals/                  # Standalone interactive HTML apps for quiz case studies
    ├── Module_1_Trajectory_1.html # Customer Service: Context Poisoning
    ├── Module_1_Trajectory_2.html # Customer Service: Rapid Context Saturation
    ├── Module_2_Trajectory_1.html # Coding Agent: Search Strategy Mismatches
    ├── Module_2_Trajectory_2.html # Coding Agent: Severed Structural Boundaries
    ├── Module_3_Trajectory_1.html # Research Agent: Repeated Compaction Degradation
    ├── Module_3_Trajectory_2.html # Research Agent: Silent Externalization (Missing Pointer)
    ├── Module_4_Trajectory_1.html # Appointment Assistant: Memory Writing & Semantic Duplication
    └── Module_4_Trajectory_2.html # Appointment Assistant: Flat-File Search & Forgotten Rules
```

## How to View the Interactive Apps

1. **Online via GitHub Pages:** Visit the [Live Interactive Portal](https://https-deeplearning-ai.github.io/context-engineering-quizzes/) or click any trajectory link above.
2. **Local Viewing:** Open [`index.html`](./index.html) or any file in [`Quiz_Visuals/`](./Quiz_Visuals/) directly in your web browser.
3. **Local HTTP Server:** Start a lightweight server from the repository root:
   ```bash
   python -m http.server 8000
   ```
   Then navigate to `http://localhost:8000` in your browser.
