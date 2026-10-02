# AI Coding Workflows: Cloud to Local — Revision Notes

**Instructor:** Paul Everitt (JetBrains) + DeepLearning.AI  
**App built throughout:** Agent Complaints (FastAPI + Bootstrap)  
**Core philosophy:** Three control points — model choice, privacy/data control, workflow customization

**Companion reference docs:**

- [Course Glossary](/docs/course_glossary.md) — key terms for coding agents, SDD, context management, and local deployment
- [Evaluation Metrics](/docs/evaluation_metrics.md) — how each workflow is measured and compared

---

## The Big Idea

Convenience (one model, one tool, no setup) vs. control (choose models, providers, workflow). Tools change; understanding the layers lets you make informed choices.

**Progression:** Cloud-only → subagents → hybrid cloud/local → fully local

**Key levers:**

1. **Specs** — divide work into achievable steps
2. **Subagents** — right work on right context
3. **Agents** — Claude Code, OpenCode, etc.
4. **Providers** — OpenRouter, LM Studio
5. **Model roles** — big brain plans, little brain implements

---

## Spec-Driven Development (SDD)

Project structure:

- `specs/mission.md` — what Agent Complaints is meant to do | Describes the app, its purpose, and the experience it should provide
- `specs/tech-stack.md` — records the technologies it should use | Records the required technologies and implementation constraints
- `specs/roadmap.md` —  lays out what needs to be built | Breaks the app into phases that coding agents can plan and implement
- `requirements.txt` — dependencies

**This course uses lightweight SDD:** one-shot builds with fixed specs (not iterative planning/building/reviewing). Clear roadmap becomes critical as models shrink. Each lesson starts fresh with the same specs to compare setups fairly.

Coding Agent — Claude Code, OpenCode
Model Source — Anthropic API, OpenRouter, LM Studio

### Anthropic API

- Pros: low effort, fast results, high quality
- Cons: less control, more money

- Opus — use for Roadmap
- Sonnet — use for Planning & Orchestration
- Haiku — use for Implementation
- Model options — Sonnet, Haiku, GPT 5.5, Deepseek V4 Pro, Deepseek V4 Flash, Gemini Pro, Llama 4

---

## OpenCode stack

1. OpenCode (Main Agent) → OpenRouter (API Connection) → Sonnet, Haiku, GPT 5.5, Deepseek… (Model)
2. OpenRouter — catalog of models hosted at inference providers, single account and API key, charges per-token

---

## Key Concepts

- **3 Control Levers** — Model choice, Privacy/data control, Workflow customization.
- **Spec-Driven Development (SDD)** — Define mission.md, tech-stack.md, and roadmap.md. Clear specs are a force multiplier for smaller models.
- **Context rot** — performance degrades as context grows; frontier models tolerate mess, small models can't
  - Large context windows degrade model performance. Solution: Use subagents with fresh, narrow contexts per task.
- **Subagent** — focused task in isolated context; main agent coordinates
- **Handoff packet** — main agent's detailed spec for a subagent; quality determines success
  - A tight, scoped spec with explicit guardrails prepared by the main agent for the subagent.
- **Big-brain/little-brain** — frontier model plans/reviews, smaller model implements
  - Frontier models (planning/review) + Smaller models (implementation).
- **Three-phase workflow** (lessons 12–13) — serialize work; main agent reviews between phases before next delegation

---

## Lesson Progression (Setups)

| # | Setup | Agent | Main Model | Subagent Model | Key change |
| --- | ------- | ------- | ----------- | ---------------- | ------------ |
| 4 | Baseline | Claude Code | Sonnet | — | One model, one job |
| 5 | Subagents | Claude Code | Sonnet | Sonnet | Phase isolation |
| 6 | Cheaper subagents | Claude Code | Sonnet | Haiku | Big/little brain |
| 7 | OpenCode setup | OpenCode | — | — | + OpenRouter, model choice |
| 8 | OpenCode baseline | OpenCode | Deepseek Pro | — | New stack, one-shot |
| 9 | OpenCode subagents | OpenCode | Deepseek Pro | Deepseek Pro | Reapply pattern |
| 10 | Cheaper subagents | OpenCode | Deepseek Pro | Deepseek Flash | Custom implementer.md |
| 11 | Local setup | OpenCode | — | Gemma 4 (local) | First local model |
| 12 | Hybrid | OpenCode | Deepseek Flash | Gemma 4 (local) | Local implementer |
| 13 | Fully local | OpenCode | Qwen 3.5 27B (local) | Gemma 4 (local) | Zero cost |

---

## Model Selection

- **Frontier (Sonnet, Opus)** — complex planning, orchestration, full-app builds
- **Mid-tier (Haiku, Deepseek Flash)** — focused tasks, implementation subagents, budget-conscious
- **Local (Gemma 4 12B, Qwen 3.5 27B)** — implementer (12B), main agent (27B+), privacy-critical

**Memory:** 16GB → Gemma 4 only; 32GB → Qwen + Gemma side-by-side

**Rule of thumb:** ~80% of agent tokens are simple; don't need frontier models

---

## Guardrails for Small Models

- Tight, detailed handoff packet (main agent's job)
- Clear phase/task boundaries (not one big job)
- Explicit tool restrictions (no recursive listings)
- Prefer `write` over `edit` for Gemma/Qwen
- Test-driven validation (tests as guardrails)
- Human-in-loop review between phases
- Set `maxSteps` ceiling; prevent retry loops

---

## Custom Subagent Definition (OpenCode)

`.opencode/agents/implementer.md`

- **Front matter:** `model`, `maxSteps`, `allowedTools`, `disabledTools`, reasoning level
- **Body:** scope discipline, file verification, selective editing, tool choice, no recursive venv listing, run tests but don't fix/loop

---

## Cost/Performance/Privacy Tradeoffs

| Setup | Cost | Speed | Privacy | Effort |
| ------- | ------ | ------- | --------- | -------- |
| Claude + Sonnet | High | Fast | Low | Low |
| Claude + Sonnet→Haiku | Medium | Medium | Low | Medium |
| OpenCode + Deepseek Pro | Low | Medium | Low | Medium |
| OpenCode + Pro→Flash | Lower | Slower | Low | High |
| OpenCode + Flash + Gemma | Low | Slow | Medium | High |
| OpenCode + Qwen + Gemma | Zero | Slower | High | High |

---

## Metrics Interpretation

- **Turns** = interaction style/model personality, not work completed (Qwen uses many turns for same tool activity)
- **Tool calls** = actual work done
- **Context tokens** = affects latency and cost
- **More subagents** = cleaner contexts but more coordination overhead
- **Context per subagent** = indicator of task size; tighter is better for small models

---

## Tools & Commands Quick Ref

- **Run FastAPI:** `python -m uvicorn main:app --reload`
- **Run tests:** `pytest` or `python -m pytest tests/`
- **LM Studio:** context length 40K (Gemma) / 80K (Qwen); 8-bit quant (Gemma) / Q4 (Qwen); local endpoint `http://localhost:1234/v1`
- **OpenCode config:** via prompt ("Set up OpenRouter", "Add Qwen to OpenCode")
- **Fresh lesson:** clean repo, new chat, new context

---

## Key Takeaways

1. **Specs are the contract** between agent and human
2. **Subagents solve context rot** but add coordination cost
3. **Big/little brain works** with good SDD and clear handoffs
4. **Small models need guardrails** — tight specs, tool limits, tests, human review
5. **Fully local is possible** on 32GB but slow, tight, and experimental
6. **Familiarity alone isn't best** — match setup to priorities (cost, speed, privacy, control)
7. **Patterns outlast tools** — layers, handoff packets, SDD, model roles generalize

---

## Known Ambiguities

- LM Studio installation steps not shown (follow their docs)
- Exact OpenCode JSON config format not fully specified (prompt-based editing shown)
- Hardware variance affects local model results
- Q4 vs. full precision accuracy difference not quantified

---

**Goal:** Not "use this setup" — learn to think about choices. Evaluate your priorities and build accordingly.
