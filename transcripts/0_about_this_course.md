Introducing AI Coding Workflows: From Cloud to Local, a short course built in partnership with JetBrains and taught by Paul Everitt, Developer Advocate at JetBrains.

Many developers build their AI coding workflow around tools like Claude Code and Codex. These tools give you a ready-made way to work, which is what makes them convenient. The tradeoff is control: over which models run, what you spend, what leaves your machine, and how the work gets split.

This course hands that control back, one layer at a time. You'll use the same Python app to put each setup to the test: first from a Claude Code baseline, then with subagents that break the job into focused tasks, then with a cheaper model doing the routine work. From there you'll switch to an open-source coding agent, connect it to different inference providers, and finally run models locally. At each step you'll see how the change shifts cost, speed, and usage, and what it means for what leaves your machine.

By the end, you’ll know how to evaluate different AI coding workflows and choose one whose tradeoffs fit your work.

In detail, you'll:

Map the path from a familiar cloud-based workflow to hybrid and fully local setups, then set up your workspace and the spec-driven process you'll use to rebuild the project at every stage.
Build a baseline version of the app in Claude Code: one prompt, one frontier model, one big job.
Break that same job across subagents with focused context, then move the implementation work onto Haiku and explore the tradeoffs of using a cheaper model.
Swap Claude Code for OpenCode, connect it through OpenRouter to a different cloud model, and rebuild the app from the same specs.
Repeat the subagent and cheaper-model moves in OpenCode, this time defining a custom implementer subagent that runs on a smaller model.
Run your first local model with LM Studio, connect it to OpenCode, and put it to work as that implementer.
Put a local model behind the main agent too, and find out how far a fully local setup can take you.
The tools will keep changing. Once you know the layers, every new model, harness, and provider becomes a choice you can make instead of a default you inherit.


Who should join?
Developers who already use AI coding agents like Claude Code or Codex and want more say in what they cost, where they run, and how they behave. You should be comfortable with Python and working in the terminal. The lessons on local models run best on a reasonably capable machine.