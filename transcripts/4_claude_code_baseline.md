0:00
You've now seen the agent complaints app
0:02
that you'll rebuild across the course
0:04
and the simplified spec-driven process
0:07
you'll use to one-shot it in different AI coding setups.
0:11
But before you can start comparing the tradeoffs
0:14
between different approaches, you need a first version.
0:18
So in this lesson, you'll build your first agent complaints app
0:22
using a basic Claude Code setup.
0:24
This means that you have a
0:26
Coding Agent running locally on your machine,
0:29
in this case, Claude Code.
0:31
Now, the Coding Agent needs to orchestrate its work with a model,
0:35
and the model will act kind
0:36
of like the brain of the agent.
0:38
So Claude Code is going to plug in that brain for you
0:42
through Anthropic's cloud-based API.
0:45
Giving you a choice between different Anthropic models
0:49
to act as the brain. And
0:50
in this lesson, you'll be choosing Sonnet
0:52
because it has a nice balance of cost and power.
0:56
Throughout this course, you'll explore other AI coding setups
0:59
that gradually move from cloud-based models
1:02
towards models running locally on your own machine.
1:06
But this first approach is a useful baseline for comparison.
1:09
So, let's start coding. In the specs
1:12
folder, you will find the project constitution.
1:16
The three files that tell Claude Code
1:18
what it's building and how to build it.
1:20
The mission says what Agent Complaints is and who it is for.
1:24
The tech stack describes the tools, language, and constraints for the project.
1:30
And the roadmap breaks the work
1:32
into small ordered steps.
1:35
Also, pay special attention
1:37
to the roadmap as you go through the course.
1:39
As you move towards local AI, the models get less forgiving.
1:44
So, a clear road map will become increasingly important.
1:48
Each lesson starts with a new chat with a nice clean context.
1:53
Now here's the prompt to create the app in one shot.
1:57
You will get it to look at the roadmap,
1:59
do each phase in an unit,
2:01
run tests, and so on.
2:04
For this course, I'm setting the agent to Accept Edits.
2:08
Your style might be different for real work.
2:11
Submit the prompt, and Claude Code then works
2:14
with a model to do all the thinking.
2:21
Now it's finished. Let's validate what it built.
2:24
First, scroll through the agent's validation.
2:27
See any showstoppers?
2:30
The agent reported critical mistakes.
2:33
Turns out, these could be better but won't stop the application.
2:37
Next, let's use the IDE to do our review
2:40
of some of the newly created files.
2:42
For example, models might generate an HTML link
2:47
with an invalid integrity attribute which breaks your layout.
2:51
Agent complaints is a FastAPI application.
2:55
Let's run it using either the command line
2:59
or any editor integration.
3:02
When the server starts up,
3:04
go to the local URL to see the app.
3:07
You start on the homepage.
3:09
As you can see, it's pretty minimal.
3:12
Styled with Bootstrap, as you requested.
3:14
If you see good styling, that means
3:16
the Bootstrap link in the template worked,
3:19
which means the integrity attribute mentioned before was okay.
3:23
You also have a link to the complaints.
3:26
You can see there are already
3:28
some entered and they're kind of funny.
3:31
At the bottom there's a form to submit a new complaint.
3:35
When you do, it appears in the list.
3:39
Remember, you're not using a database,
3:41
so anything you save is lost on restart.
3:45
Since validation passed, let's put the project back in the starting state.
3:49
First, let's shut down the FastAPI server.
3:54
Let's delete all the new files and directories that were created.
3:58
You're going to repeat this same lesson structure
4:00
throughout the course, each introducing an architecture piece
4:04
towards local AI. Thus, you'll finish each lesson
4:08
by reverting to a clean slate.
4:11
You now have the results of this baseline standard low effort setup.
4:16
With Claude Code and the standard Anthropic Sonnet model,
4:19
you get low effort, fast results, and high quality.,
4:23
but with less control and more money.
4:26
At each step in this course, I will show you some metrics
4:29
to see how each step changes.
4:31
Here you see the baseline.
4:34
These metrics separate the work done by the main agent
4:36
from the work done by the subagents.
4:38
In this run, Claude Code spawned one
4:41
subagent on its own. You didn't explicitly
4:43
at least set it up. Turns shows a single cycle of action
4:47
where the agent plans, calls a tool, then processes the result.
4:52
Context processed shows how many tokens were used.
4:56
Tool calls show how many times the agent needed to go look
4:59
at the outside world by running a program.
5:03
We have a baseline for the cost,
5:05
and wall clock shows how long it took.
5:08
And it's useful as a rough reference,
5:10
but it can be affected by things outside of the setup.
5:14
So, don't put too much weight on this number.
5:16
As you can see, the subagent consumed
5:19
54% of context and made 61% of tool calls,
5:23
while the main agent retained a substantial orchestration role.
5:26
Remember, this was just one run.
5:28
If you run it again, you'll get different results.
5:31
But this gives us our first rough baseline for comparison.
5:35
Different setups will come and go.
5:37
What matters most in this course is
5:40
learning how to compare their tradeoffs
5:42
and decide what works best for you.
5:45
So that wraps your first implementation of agent complaints.
5:49
Claude Code with a powerful cloud model.
5:52
But this course is moving towards setups where
5:55
you take more control over the work
5:57
instead of relying on a frontier model
6:00
to handle one big messy job for you.
6:03
So before you change any models,
6:05
the next lesson is about optimizing context for subagents.
6:10
Because if you want smaller local models to succeed,
6:13
you need to first learn how to break the work
6:16
into smaller, more precise tasks. I'll see you there.