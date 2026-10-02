0:00
In the last lesson, you rebuilt Agent Complaints with a new setup:
0:03
OpenCode, OpenRouter, and Deepseek.
0:07
But the work still ran through a single agent.
0:10
In lesson four, you saw another approach:
0:12
split the work across subagents.
0:14
Now you'll use subagents in OpenCode,
0:17
just like you did in Claude Code.
0:19
So one long-running agent
0:22
doesn't have to carry the whole build.
0:24
Your spec-driven development roadmap already breaks the project
0:28
into smaller phases and tasks,
0:30
and those become the pieces
0:32
you can hand off to subagents.
0:34
And remember, this pattern becomes especially important later
0:38
when you move to smaller local models.
0:41
To start, make sure you have no uncommitted changes
0:44
and that you've cleaned up the last lesson.
0:47
You should have no Python files in your project.
0:49
This lesson is about making really good implementation context by using subagents.
0:56
Now, give your main agent the same fresh start.
0:59
Each lesson starts with a new chat with a nice clean context.
1:03
You're now ready for subagents.
1:05
Like lesson four, you'll do the same one-shot prompt.
1:09
As before, you are telling the main agent
1:12
to use a new context, new subagent
1:14
for each roadmap phase.
1:17
As with OpenCode, the chat window shows
1:19
that the phase implementation work was sent to a subagent.
1:23
You can explore the subagent section
1:26
in the chat results to get more detail.
1:29
The project is now implemented.
1:32
This time, the main OpenCode agent
1:33
doesn't have a lot of extra context.
1:36
Even better, the context in the implementation work
1:39
was focused on exactly what it needed.
1:43
As a reminder, you're doing less
1:44
human in the loop in this course
1:47
to focus on getting to local AI. You'll do some light validation.
1:51
Let's look at these same file you reviewed last time.
1:54
Did implementation by subagent work okay? Yeah, looks pretty good.
1:58
Let's run the server and look at agent complaints in the browser.
2:02
Give a quick look at the homepage and make sure it's okay.
2:05
Then review the complaints page
2:08
and submit a new complaint.
2:12
It shows up in the list of complaints.
2:14
Veredict, subagent for implementation worked fine.
2:18
Now it's time for end of lesson cleanup.
2:21
First, shut down the FastAPI server.
2:24
Then remove the files and changes done during this lesson.
2:28
You're now ready for next time.
2:31
This lesson reintroduces the lesson four pattern.
2:34
One fresh general subagent per phase.
2:38
The main agent became very small
2:40
using only six turns and 90k of context.
2:44
The subagents consumed 94% of all context
2:47
and made 85% of tool calls.
2:50
Compared with direct implementation in lesson seven,
2:53
total turns increased 120%,
2:56
context increased 179%,
2:58
and tool calls increased 139%.
3:02
Phase delegation
3:03
successfully protected the main agent's context,
3:06
but greatly increased total context processed.
3:10
Cost nearly tripled, although it remained low in absolute terms,
3:14
while wall clock increased 26%.
3:17
Just as with lesson four,
3:18
a step backward on the way to a step forward.
3:22
Now that the work is split into smaller focused handoffs,
3:25
you're ready for the next move,
3:27
choosing a different model for the subagent.
3:29
In the next lesson, Deepseek Pro will handle the main agent,
3:33
while Deepseek Flash handles the subagent.
3:36
I'll see you there.