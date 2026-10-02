# Evaluation Metrics

- How each workflow in the course is measured and compared. The same project is built repeatedly with different combinations of coding agents and models, and these are the measures used to compare the runs.

---

- **Turns** A single cycle in an agent's work where it takes an action — plans a step, calls a tool, and processes the result — before moving to the next cycle. A higher turn count for similar output can indicate a less efficient interaction style rather than more work actually completed, since some models take many small turns to accomplish what another model does in fewer.

- **Tool Calls** The number of times an agent invokes an external action — such as reading a file, running a command, or executing a test — during a session. Distinct from turns: a single turn may involve zero, one, or multiple tool calls.

- **Context Processed** The total number of tokens an agent (or its subagents) consumed across a session, combining everything read, generated, and passed between turns. Used as a proxy for both cost (on metered cloud models) and the risk of context rot.

- **Wall-Clock Time** The real-world elapsed time a session takes from start to finish, as opposed to a count of turns or tool calls. Useful as a rough practical reference, but sensitive to factors outside the agent/model setup itself, such as local hardware load or network conditions.

- **Metered Cost** The billed cost of a session on cloud-based, pay-per-token models. Sessions that run entirely on local models have no metered cost, since there is no per-token billing for compute running on the user's own hardware.