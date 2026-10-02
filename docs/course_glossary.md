# Course Glossary

- Key terms for working with AI coding agents across cloud, hybrid, and local model setups: spec-driven planning, subagent architecture, context management, and the infrastructure that connects agents to models.

---

## Foundations

- **Coding Agent** - The software that orchestrates an AI-assisted coding session: it reads instructions, calls tools (reading/writing files, running commands), and manages the back-and-forth with a model. Distinct from the model itself — a coding agent is the harness around the model, not the "brain" doing the reasoning. Examples include Claude Code and OpenCode.

- **Model (LLM)** - The large language model that a coding agent consults to decide what to do next — often described as the agent's "brain." The same coding agent can typically be pointed at different models, and the same model can be reached through different coding agents.

- **Coding Harness** - A general term for the surrounding software (coding agent, its configuration, and its tool integrations) that wraps a model to make it useful for software development tasks, as opposed to the raw model itself.

- **Inference Provider** - A service that hosts a model and runs it on demand in response to API requests. Distinct from a coding agent (which decides what to ask) and a model (which produces the answer) — the inference provider is the infrastructure that actually executes the model.

- **Cloud-Based Model vs. Local Model** - A cloud-based model runs on infrastructure operated by an inference provider and is reached over the internet, usually billed per token. A local model runs on the user's own hardware via a local inference server, keeping code and prompts on that machine and avoiding per-token cloud billing, at the cost of being limited by that machine's memory and compute.

- **Frontier Model** - A large, highly capable model near the current state of the art. Frontier models tend to tolerate messier, longer inputs better than smaller models, but usually cost more per token and are often only available via cloud inference.

- **Open-Weight Model** - A model whose trained parameters are published for anyone to download and run, as opposed to being accessible only through a provider's hosted API. Open-weight models are what make running a model locally possible.

---

## Spec-Driven Development

- **Spec-Driven Development (SDD)** - A workflow for AI-assisted coding in which the goals, constraints, and planned work for a project are written down in advance as structured specification documents, which then guide the coding agent's work — rather than describing everything freeform in a single prompt.

- **Project Constitution** - The set of foundational specification documents for a project under spec-driven development, typically covering what the project is for, what technologies it should use, and what needs to be built. It establishes the ground rules an agent should follow throughout the build.

- **Mission (spec file)** - The specification document that states what a project is meant to do and who it's for. It answers "what are we building and why," which grounds every other planning decision.

- **Tech Stack (spec file)** - The specification document that records the languages, frameworks, libraries, and technical constraints a project should use. It steers an agent's technology choices so they're consistent rather than improvised per task.

- **Roadmap (spec file)** - The specification document that breaks a project's work into ordered phases and tasks. A clear, well-scoped roadmap becomes more important as work is delegated to smaller models, since they need explicit, bounded units of work to succeed.

- **One-Shot Prompting** - Asking an agent to complete an entire build (or a full phase of it) from a single prompt, rather than guiding it through separate rounds of planning, implementation, and review for each feature. Useful for quickly comparing different agent/model setups against the same task, but offers less opportunity for course-correction along the way than an iterative feature loop.

- **Feature Loop** - The full spec-driven cycle for a single feature: plan the change, implement it, review the result, and update the specs before moving to the next feature. Contrasts with one-shot prompting, which skips the incremental checkpoints in favor of building everything at once.

---

## Context Management

- **Context Window** - The total amount of text (measured in tokens) a model can take into account at once when generating a response. Everything a coding agent has read, written, or been told so far in a session competes for space inside this window.

- **Context Rot** - The tendency for a model's output quality to degrade as the amount of input in its context window grows, even when the context window is technically large enough to hold everything and the needed information is still present. It happens because attention gets spread across more content, so relevant details — especially ones in the middle of a long context — get less effective weight. Larger frontier models tend to tolerate this better than smaller models, whose limited context windows make it a much bigger risk.

- **Clean Context** - Starting a new working session with an empty context window rather than continuing to build on an already-long one. Used as a discipline to avoid context rot: beginning each new unit of work fresh, instead of letting context accumulate indefinitely across unrelated tasks.

---

## Agents and Subagents

- **Main Agent** - The coordinating agent in a multi-agent setup: it holds the overall plan, decides how to break work into pieces, delegates pieces to subagents, and reviews their results. Distinct from a subagent, which handles one delegated piece rather than the overall coordination.

- **Subagent** - A secondary agent invoked by a main agent to handle one bounded piece of work in its own fresh, focused context, then return the result. Using subagents keeps any single context window from growing large enough to trigger context rot, and lets different pieces of work be assigned to different models.

- **Implementer Subagent** - A subagent whose role is narrowly scoped to executing a well-specified unit of work handed to it by the main agent — as opposed to planning, reviewing, or deciding what to build next. Implementer subagents are typically the role assigned to smaller, cheaper, or local models, since the scope of the task is kept small enough for a less capable model to handle reliably.

- **Big Brain / Little Brain Pattern** - A division of labor where a more capable (and typically more expensive) model handles planning, delegation, and reviewing results, the "big brain", while a smaller, cheaper, or local model handles the bounded implementation work handed to it, the "little brain." The pattern only works well when the big brain gives the little brain a tightly scoped, well-specified task; a vague or oversized handoff causes the smaller model to make mistakes that cost more time and money to fix than using a single capable model would have.

- **Handoff Packet** - The specific instructions, context, and constraints a main agent prepares for a subagent before delegating a task to it. A well-built handoff packet scopes the work to fit the subagent's model capacity (especially for smaller or local models) and is the main lever for making the big brain/little brain pattern succeed; a poorly built one is a common source of subagent errors.

- **Agent Definition File** - A configuration file (commonly Markdown with structured front matter) that defines a custom subagent's role, instructions, model choice, tool permissions, and limits such as a maximum number of steps. Used to give a subagent a persistent, reusable identity instead of specifying its model and instructions inline in every prompt.

---

## Connecting Agents to Models

- **Agent Client Protocol (ACP)** - An open protocol that standardizes communication between code editors/IDEs and coding agents, so that any ACP-compatible agent can run inside any ACP-compatible editor without custom, one-off integration work between each specific pairing.

- **Inference Server** - Software that loads a model and exposes it through an API so that a coding agent (or any other client) can send it requests and receive generated output. A local inference server performs this role on the user's own machine, in place of a cloud-based inference provider.

- **Model Router** - A service that provides a single API connection to a catalog of models from multiple underlying inference providers, so a coding agent can switch between models and providers without managing separate accounts, credentials, and billing for each one. Usage is typically billed per token to a shared account balance regardless of which underlying model handled a given request.

---

## Local Model Deployment

- **Quantization** A technique for reducing a model's memory footprint by storing its parameters at lower numeric precision (for example, 4-bit instead of 16-bit). Lower-bit quantization (e.g., Q4) makes a model smaller and faster to run locally at some cost to output accuracy, while higher-bit quantization (e.g., 8-bit) preserves more accuracy at the cost of a larger memory footprint.

- **Mixture of Experts (MoE)** A model architecture in which only a subset of the model's total parameters ("experts") are activated for any given input, rather than the whole network running on every request. This lets a model have a large total parameter count while keeping the compute cost of each individual request lower than a same-sized "dense" model would require.

- **GGUF / MLX** Two file formats for distributing quantized model weights for local inference. GGUF (GPT-Generated Unified Format) is a widely supported format usable across many platforms, while MLX is a format optimized specifically for Apple Silicon hardware; which one to use depends on the hardware running the local inference server.
