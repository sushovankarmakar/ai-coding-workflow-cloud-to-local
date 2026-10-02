0:00
In the last lesson, you built the baseline version
0:02
of agent complaints, the easy way.
0:04
You gave Claude Code the specs,
0:06
sent it one prompt and let it do its thing.
0:10
In this lesson, you'll use subagents
0:12
to break that same job into smaller,
0:15
more focused tasks.
0:18
The reason comes down to context.
0:21
When Claude Code runs one continuous job,
0:23
a single context window generates every response
0:26
and keeps filling up with material.
0:29
So each new response comes from a longer, messier input.
0:34
As that input grows, performance can degrade.
0:37
As you can see in this
0:39
graph from a study on context length,
0:41
as the context grew, quality dropped.
0:44
And when that happens, the model might
0:47
lose track of earlier instructions,
0:49
miss details, or make more mistakes.
0:52
And there's a word for this, context rot.
0:56
Now with a small app like agent complaints and a Frontier model,
1:00
context rot is barely a problem.
1:03
Frontier models can have huge windows and tolerate a lot of mess.
1:08
But smaller models don't have that luxury.
1:10
Their context windows are literally
1:13
smaller. So a big context may not even fit.
1:16
And even a context that fits
1:18
can be too messy for them to handle.
1:20
This matters because smaller local models
1:23
are exactly where this course is headed.
1:25
And to get there, you're going to need Sub-Agents
1:29
with small, focused contexts.
1:31
This will no longer be a nice to have, it's a requirement.
1:35
So, how do we get smaller, more focused contexts?
1:39
by doing one thing at a time.
1:42
Our roadmap has phases with tasks.
1:46
In fact, in richer spec-driven development systems,
1:49
each feature loop has more detail.
1:52
Here's a feature in one of my projects. That's plenty of context.
1:55
So instead of using one context window to carry the entire build,
2:00
you can delegate pieces of the work to sub-agents.
2:03
Each sub-agent gets a fresh, focused context for its part,
2:08
then returns the result to the main agent.
2:11
And Claude Code already uses sub-agents this way.
2:14
For example, when it needs to search through a large code base,
2:17
it can send that work to separate helpers.
2:20
Let each helper work in its own context
2:22
and bring back only what it found.
2:25
Let's get started.
2:27
First, make sure you have no uncommitted changes
2:29
and that you cleaned up the last lesson.
2:32
You should have no Python files in your project.
2:36
Let's also do that for the main agent.
2:38
Each lesson should start with a nice clean context.
2:42
So make sure you start a new chat.
2:44
You're now ready for subagents.
2:47
You'll use these same one-shot prompts as before
2:50
where a single prompt builds the whole app.
2:53
This time though, the prompt will tell the Main Agent
2:57
to use a new subagent to implement each phase.
3:01
Claude Code, by default, will use the same
3:03
model in the subagent as the Main Agent.
3:06
In this case, Sonnet.
3:07
As the results come by, you will see something new.
3:10
The chat window shows that the Phase 1 implementation work
3:14
was sent to a subagent. What does that work look like?
3:19
Here's what the subagent was told to do.
3:24
Same for phase two. The main chat shows work was handed off,
3:29
and here's what the handoff conversation looked like.
3:36
The work is now finished with a similar result.
3:39
You can now go to the agent blocks in the chat
3:42
to see the result of each agent
3:45
for phase one and for phase two.
3:49
Not only did our subagent conserve context,
3:52
so did our main agent, which had less work to do.
3:55
Now it's finished. Let's do validation.
3:58
First, the agent did its review
4:01
and reported its findings.
4:03
We'll do some light validation ourselves.
4:05
Let's look at one of the files, the main application.
4:09
Did implementation by subagent work okay?
4:11
Looks pretty good.
4:14
Let's run the server and look at agent complaints in the browser.
4:18
Give a quick look at the homepage and make sure it's okay,
4:22
then review the complaints page,
4:25
and submit a new complaint. It shows up in the list.
4:31
Veredict, subagent for implementation worked fine.
4:35
Now it's time for end of lesson cleanup.
4:39
First, shut down the FastAPI server.
4:44
Then remove the files and changes done during this lesson.
4:50
This means we're ready for starting the next lesson.
4:53
What did this lesson show? It's an important one.
4:56
Work in small steps with fresh context using sub-agents.
5:01
You didn't do anything fancy yet
5:03
and we are still 100% in the cloud with the same model.
5:06
This does though put work on you
5:09
and how you prompt to get
5:11
the main agent to steer the sub-agent.
5:14
Looking at the numbers, main agent effort fell slightly
5:17
from seven to six turns
5:20
and from 217K to 192K context,
5:23
showing that the main agent became a leaner coordinator.
5:28
Subagent context and turns nearly doubled
5:31
from 257K to
5:34
511K. Total context and turns increased around 50%
5:38
in tool calls around 20%.
5:41
And the cost actually went up a bit.
5:44
The cleaner phase boundary therefore carried
5:47
a measurable coordination and context cost.
5:49
You did the work but you
5:52
haven't yet gotten the benefit. That's next.
5:54
Now that you have better context management by using subagents,
5:58
do you even need your most expensive model doing that work?
6:03
Maybe you also can save money by using cheaper models for implementation.
6:08
So in the next lesson, we'll start adjusting the model itself.