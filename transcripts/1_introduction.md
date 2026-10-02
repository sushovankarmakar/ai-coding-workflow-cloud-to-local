0:00
Welcome to this course on AI coding workflows
0:01
from cloud to local, built in partnership with JetBrains.
0:05
For many developers, AI coding has meant using tools
0:08
like Claude Code, or Codex where the agent and models
0:10
and the workflow are handled for you
0:13
but that's changing.
0:15
For example, I also regularly use
0:17
more open coding harnesses like OpenCode
0:19
and Pi Coding Agent with open-weight models.
0:23
So, you now have more choice in the coding agent you use
0:26
and the model that powers it,
0:28
as well as where the model runs,
0:30
including maybe occasionally running a local model.
0:33
And these choices can affect your effectiveness and how much you spend,
0:40
as well as how private your
0:42
code stays and how your tools behave.
0:44
In this course, you start with the familiar cloud-based coding workflow
0:49
and gradually take more control by introducing specialized sub-agents.
0:54
So you look at how to assign different models to different tasks
0:58
and choose your own inference provider.
1:00
And you also experiment with running some models in your own machine.
1:04
Along the way, you see how these different architectural choices
1:08
affect cost, privacy, and speed
1:10
and how this affects the quality of your code.
1:13
I'm delighted that the instructor of this course is Paul Everett,
1:16
who's developer advocate for JetBrains.
1:19
Thanks, Andrew. And yes, the goal here
1:21
is for you to take more control
1:22
over the setup behind your AI coding agent
1:26
by working directly with the pieces and
1:28
There are three that really matter.
1:31
First, you get smart choosing the right model for the right job.
1:35
With the default AI coding tool, the same model often handles everything,
1:39
usually the big one. But not every task needs a frontier model.
1:44
Without model choice, you can end up paying top tier prices
1:47
for routine work. Second, you get to decide what leaves your machine.
1:53
If you run models locally, your
1:55
code and prompts can stay with you
1:57
and for some teams, that's not just a preference,
2:00
it's a requirement. Third, you can shape the workflow itself.
2:04
You decide which agents run,
2:06
what instructions they follow, and how the work gets split between them.
2:10
That way AI supports the way you work
2:14
instead of bending your work around the tool.
2:17
I'll be honest, this space is still pretty raw.
2:20
You may need to spend some money on cloud-based models,
2:23
and if you want to run models locally,
2:26
you'll probably want a pretty capable machine,
2:29
ideally with a very enthusiastic CPU fan.
2:34
Learning how to code with AI assistants
2:37
should not be about learning how to use one tool.
2:40
It should be about learning skills that you can use with any tool
2:44
and look forward to Paul showing a lot else with you.
2:47
Many people have worked to create this course.
2:49
I'd like to thank Konstantin Chaika
2:52
and Zina Smirnova from JetBrains
2:54
and Nick Lewis from DeepLearning.AI.
2:57
In this first lesson, you'll set up the development environment
3:00
and the project that you'll use throughout the course.
3:03
You'll also see the overall workflow that you'll revisit
3:07
as your AI coding architecture becomes more capable
3:10
and more under your control.
3:13
So, let's go into the next video and start turning
3:16
AI coding defaults into choices that you can make.