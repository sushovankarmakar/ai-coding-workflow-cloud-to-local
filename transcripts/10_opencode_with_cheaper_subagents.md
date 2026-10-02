0:00
You've got subagents running in OpenCode.
0:02
So now you can bring back the move from lesson five,
0:05
use a smaller, cheaper, faster model for implementation.
0:09
This time though, the model choice won't just live in the prompt.
0:13
You'll define a custom subagent called the implementer.
0:17
Let's get started.
0:19
As a reminder, lesson five used Claude Code as the coding agent,
0:22
Sonnet as the big brain, and Haiku as the little brain
0:26
for smaller implementation tasks.
0:29
Now you're using OpenCode as the coding agent
0:32
with Deepseek V4 Pro as the big brain.
0:35
Let's add a model that can play the same role Haiku played.
0:38
before. Deepseek V4 Flash,
0:41
a smaller, cheaper, faster member of the V4 family.
0:45
Unlike lesson five, you can't assign the model directly in the prompt.
0:50
Instead, you're going to create a custom OpenCode subagent
0:54
called implementer using a Markdown file as definition,
0:58
and define the subagent model choice there.
1:02
The front matter has lots of interesting fields
1:04
to control the subagent that you'll explore later.
1:07
This keeps the same division of labor you've been using.
1:10
The big brain, pro, runs each feature loop.
1:14
It finds the roadmap entry
1:16
and crafts a well-specified work packet for the implementer.
1:20
The little brain, flash, takes that packet
1:23
and does the small specified unit of work.
1:26
and Pro stays on as the judge,
1:28
reviewing the implementer's results
1:30
and maybe sending corrections back for fixing.
1:33
As I've said before, good planning and spec is important for success.
1:37
Bad plan leads to awful result.
1:41
As usual, did you clean up after the last lesson?
1:44
No uncommitted changes and no Python files in your project.
1:49
Let's also repeat our mantra, clean context.
1:52
Start a new chat to start this new lesson,
1:55
but make sure the model choice is DeepSeek Pro.
1:59
In this lesson, your implementation starts with a different step.
2:03
Let's define your implementer subagent.
2:06
Know who is good at making subagents? OpenCode.
2:09
Enter this prompt and have OpenCode write its agent definition file.
2:19
You now have a new markdown file in implementer.md
2:22
in your project's .opencode/agents directory.
2:27
It has a fairly standard body and some interesting front matter.
2:31
Take a special look at the model definition,
2:34
Flash, just as you asked.
2:36
Let's give it a try with a prompt
2:38
that aims a simple question at the new implementer agent.
2:43
Your one-shot prompt steers a subagent,
2:46
but in this case a specialized custom implementer.
2:50
The model selection is in the agent.
2:52
definition. Users don't have to specify it
2:55
in the main agent prompt.
2:58
After the main agent surveys the project and reads the roadmap,
3:02
it sends work to subagents.
3:05
For Phase 1,
3:11
And then, phase two.
3:13
These write-ups are the key to success.
3:15
The main agent takes the roadmap spec,
3:18
thinks about how to guide the little brain
3:20
and should provide enough detail.
3:22
How are the results? Let's take a look.
3:25
You're again using a cheaper implementer.
3:27
Let's gain some trust by doing some more human in the loop.
3:32
First, what did Pro think of Flash's work?
3:35
You asked the main agent to give a review.
3:38
Most likely the points are minor,
3:40
even if Pro makes a big deal out of them.
3:43
In later lessons, you'll use a smaller subagent model.
3:47
That can lead to more serious problems with the subagent's results,
3:51
and the human in the loop will be left with cleanup.
3:55
You don't want that, so future lessons
3:58
will improve this main to subagent collaboration
4:01
to include review and fixing.
4:04
Let's also run the tests ourselves. The tests passed.
4:08
Our test writing and test checking did its job
4:11
helping small models stay on track.
4:13
Let's fire up the server and
4:15
check the two pages in the browser,
4:17
checking the homepage,
4:19
then the complaints page.
4:21
All seems well, including posting a new complaint.
4:27
Let's wrap up with our end of lesson cleanup.
4:30
Shut down the FastAPI server and clean up the files.
4:34
This time though, you'll commit the implementer.md file.
4:42
This lesson changes the subagent model to flash.
4:45
Eight small implementers replaced the two large
4:48
pro subagents used in the previous lesson.
4:52
Subagent context fell from 1.39 million to 882k
4:56
despite the higher subagent count.
5:00
Average context per subagent dropped from roughly 694k to 110k,
5:05
showing that smaller task packets materially constrict
5:08
individual implementer sessions.
5:10
The savings shifted rather than eliminated context.
5:14
Main agent context rose from 90k to 712k as the coordination expanded.
5:21
Total context increased 8%,
5:23
turns increased 56%,
5:25
and wall clock increased 50%.
5:28
But the cost fell 28%.
5:31
Conclusion, task-sized flash implementers reduced individual
5:36
Subagent burden and price, while increasing main agent orchestration
5:40
and overall interaction.
5:42
As you can see in our matrix,
5:44
you've made the final step in semi-local.
5:46
Specialized subagents that have a smaller model but do less work.
5:50
The key to success, the Handoff Packet
5:52
from the big brain agent to the little brain agent.
5:55
This scopes the subagent work to
5:57
fit the capacity of the implementer's model
6:00
and gives it the hints and guardrails it needs to succeed.
6:04
Here we are. You now choose the coding agent,
6:07
the provider, the models, and how the work splits between them.
6:10
But none of it runs yet on your machine.
6:14
The models are still in the cloud
6:16
and you still pay by the tokens.
6:18
So, in the next lesson, you'll get your first local model running
6:22
on your own machine and connected to OpenCode.
6:25
I'll see you there.