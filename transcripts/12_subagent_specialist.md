0:00
Your local model is now running,
0:02
but can you use a local
0:03
model as part of your agentic coding
0:05
even without top-tier equipment? Yes, you can.
0:08
In this lesson, you'll carefully construct a setup
0:12
that gives a small local model a shot
0:14
as your implementer subagent.
0:17
You have a main agent using
0:19
a model in the cloud via OpenRouter.
0:21
You have an implementer subagent
0:24
that tackles a small, well-specified set of tasks.
0:26
And you now have a local Gemma 4 model
0:30
that your OpenCode agent can see and use.
0:33
You've now connected OpenCode to models in two places:
0:36
through OpenRouter in the cloud
0:39
and through LM Studio on your own machine.
0:41
Both use an OpenAI compatible API,
0:45
So OpenCode can communicate with them in the same general way.
0:49
That makes pointing the implementer at
0:51
your local Gemma 4 model relatively easy.
0:54
The harder part, which is the big idea of this lesson,
0:57
is shaping the work so that a small local model can succeed
1:01
within your resource constraints.
1:04
You're also going to change your big brain
1:06
from DeepSeek Pro to DeepSeek Flash,
1:09
while keeping it in the cloud through OpenRouter.
1:12
This starts a sequence of making the big brain smaller
1:16
on the way to a local big brain in the next lesson.
1:19
Let's start there.
1:22
As usual, did you clean up after the last lesson?
1:24
No uncommitted changes and no Python files in your project.
1:29
Let's also repeat our mantra: clean context.
1:32
Start a new chat to begin this new lesson.
1:34
But this time, change the model choice to DeepSeek V4 Flash.
1:40
You are moving to a smaller implementer model,
1:43
so you need to give it some help.
1:44
Let's split phase two in the road map.
1:46
It's a bit too complex for a small model.
1:49
Use a prompt to ask Deepseek Flash to move
1:52
everything in phase two that is related to adding a complaint,
1:56
starting with the roadmap line
1:58
a form at the bottom with
2:01
into a new phase with testing.
2:04
Splitting the roadmap gives Gemma 4 less work to handle at once.
2:08
But because it's a smaller model,
2:10
it also needs clearer instructions.
2:12
So, you'll update the implementer subagent definition.
2:16
As you can see, it's much longer,
2:18
reflecting the extra guidance the model needs.
2:21
First in the front matter, you see the major change.
2:24
You're using a local model for this subagent.
2:27
Also, you can see additions to help control the agent.
2:31
setting a ceiling of 12 for the steps to prevent a loop,
2:35
what the agent has permission to access,
2:38
and disabling access to some tools.
2:40
Without these settings, Small models can get into loops,
2:43
overwrite previous work, look in places it shouldn't,
2:46
and explode its context, and so on.
2:49
The implementer body also changed.
2:51
In the first paragraph, we make it clear,
2:54
only work on what you are told to work on.
2:57
The second paragraph makes sure the small model has the
3:00
right file content. rather than something from the context
3:05
and don't change content you aren't asked to change.
3:08
The third paragraph has a key point.
3:10
Use the write tool instead of edit.
3:13
Small models mess up on edit.
3:15
This continues in the fourth paragraph about new files.
3:18
The fifth paragraph is aimed at the Python virtual environment.
3:23
Don't do a recursive listing there which loads a lot of context.
3:27
The final paragraph handles the validation.
3:30
Run the tests with the provided command,
3:33
report the results, but do not try to fix anything
3:37
and don't get in a loop rerunning tests.
3:40
Of course, you're unlikely to edit this yourself.
3:43
Feel free to use the file from the resources section.
3:46
Changes to a subagent mean a new chat is needed.
3:50
Your one-shot prompt from lesson nine is like the implementer, now different.
3:54
It's no longer one-shot. You do each phase one at a time.
3:58
Both have less work for the small model per step
4:02
and also give you a chance to review and correct.
4:05
In this prompt, the main agent needs
4:07
to do its side of the bargain
4:09
to help the local model implementer succeed.
4:12
The first paragraph tells which phase to work on.
4:16
The second paragraph talks about the handoff packet
4:19
where the main agent very carefully prepares
4:21
the work to be done by the implementer.
4:24
This is the key success point.
4:26
This handoff packet is built to
4:28
fit the size of the small model,
4:31
the small context, the low power tool calling, etc.
4:35
The third paragraph reflects a common issue.
4:38
Small agents can mess up file contents.
4:41
The fourth paragraph helps the small agent find the correct pytest
4:45
from the virtual environment and persuades the implementer
4:47
to not get into a test failure loop.
4:50
The final paragraph talks more about
4:52
files and how to evaluate the work.
4:54
Again, this is a lot of text.
4:57
Copy it from the course resources
4:58
if you want to save some typing.
5:00
Also, the cumbersome nature points to an opportunity.
5:04
Developers will start to target small models
5:07
and share agent plugins which automate this.
5:10
Since the chat window selected Flash,
5:13
the main agent's model is already set.
5:16
You have small brain talking to really
5:18
small brain. The results will show the subagent.
5:22
At the moment of handoff, you can click
5:24
to take a look at the handoff packet
5:27
while the agent continues to work.
5:30
The handoff packet is a very interesting artifact.
5:33
Keep an eye on these to make
5:35
sure the work matches what you expect.
5:37
Remember, things you type in prompts
5:40
and enter in subagent definitions
5:43
are persuasion, not requirements.
5:45
Small models often have a mind of their own.
5:48
For example, in this case, the
5:50
admonition to not write full code was
5:53
partially obeyed. Flash wrote more code than it should.
5:56
Next time, it might do what you tried to persuade.
6:04
All finished, but perhaps not quicker
6:06
depending on how much power you have in your local system.
6:09
But this time, the smaller implementer
6:12
might not do as well.
6:14
The main agent might report some issues here.
6:16
Perhaps in your session, these are more severe sometimes.
6:21
Remember, small models need help,
6:23
including from you, the human.
6:25
Work in small steps, review, and correct.
6:29
Let's repeat this process for Phase 2.
6:32
The main agent sends the same prompt
6:34
with Phase 2 instead of phase one.
6:44
As the results go by, let's look again at the handoff packet.
6:48
Did the main agent help the small model succeed?
6:51
Also, I mentioned the phase one handoff packet
6:54
didn't totally follow our don't write the code instruction.
6:58
This time, Flash obeyed this guidance.
7:02
The lesson, it can be random. Results look good.
7:06
You can repeat for Phase 3 by reusing the same prompt.
7:11
You're now using a small language model, SLM,
7:15
as a local, free implementer.
7:17
Do you trust it? Let's do some human in the loop.
7:22
Best first step, run the test yourself.
7:25
Test writing becomes a really helpful way
7:27
to put in the guardrails needed
7:29
to keep small models from landing in the ditch.
7:32
Now start the server. How are your two pages?
7:39
The homepage seems fine,
7:42
as does the complaints page. All seems well,
7:46
including posting a new complaint.
7:52
Let's wrap up with our end of lesson cleanup.
7:55
Shut down the FastAPI server
7:58
and clean up the files.
8:01
But let's commit the changes to the implementer and the roadmap.
8:11
It's been said that 80% of agent tokens
8:14
are so simple, they don't need frontier models.
8:17
In this lesson, we showed how the simple, well-specified work
8:21
can fit into small units that a small local model can handle.
8:25
But for not simple,
8:27
you're starting to see that control comes with some headaches.
8:30
You have to put in some thinking, some engineering.
8:33
You're no longer in vibe coding,
8:36
hardware, model, tuning, prompt, agent definition, guardrails, roadmap size, etc
8:42
especially on average computers.
8:45
Looking at the numbers, the report groups the three subagent runs together.
8:49
Three turns, 21 tool calls,
8:51
and 117000 processed context in total.
8:56
Since the implementer was called once for each of the three phases,
9:00
that works out to be one turn
9:02
an average of seven tool calls and roughly 39k context per subagent.
9:07
They handled implementation directly,
9:09
while the main agent read the specifications,
9:12
reviewed each completed phase and composed the next delegation.
9:16
The main agent consumed 69% of context
9:19
and made 59% of tool calls,
9:22
largely through 25 read operations.
9:25
That is expected for this three-phase review and delegate workflow,
9:29
but it shows that Phase isolation moves context pressure
9:32
to the main agent rather than eliminating it.
9:36
The run was very inexpensive
9:38
because the three subagents used local Gemma inference,
9:42
leaving only like two cents of metered main agent cost.
9:47
It's 8 minute 52 second wall-clock
9:49
is mostly sequential main agent work rather than idle time.
9:53
It should be compared cautiously with earlier runs
9:55
because it includes all three roadmap phases.
9:59
Local AI arrives. Your implementer subagent
10:02
is now running on a local model.
10:04
But the main agent is still using a cloud model.
10:08
Can local models also handle the big brain?
10:11
You'll find out in the next lesson.