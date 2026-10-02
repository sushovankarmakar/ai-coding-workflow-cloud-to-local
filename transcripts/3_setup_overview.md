0:00
Before you jump in, let's setup your workspace
0:02
and your way of working.
0:04
This course builds a simple Python application,
0:07
and in this lesson, you'll get your tool setup,
0:11
start a Python workspace and do the project kickoff.
0:14
The application you'll build is titled Agent Clinic.
0:17
It's a simple app where overworked AI agents can complain about their humans,
0:22
which is why will refer to it throughout the course as the Agent Complaints app.
0:28
It has a homepage and a complaints page.
0:31
On the complaints page, you can read their complaints
0:33
and use a form to add a new one to the list.
0:36
Agent complaints originally appeared in another course, Spec-Driven Development.
0:40
And we're borrowing more than the app.
0:42
You'll also use a lightweight version of the Spec-Driven Development
0:46
process taught there.
0:48
Now, you don't need to have
0:50
taken that course to follow this one.
0:52
I'll cover all the basics you need in this video.
0:54
But if you want to explore Spec-Driven Development in more depth,
0:58
I encourage you to check it out.
1:00
So, at its simplest, the goal of Spec-Driven Development
1:03
is to record the goals and decisions
1:06
that should guide each build in a
1:08
project Constitution. The Constitution is organized into three files.
1:13
The Mission explains what Agent Complaints is meant to do.
1:16
The Tech stack records the technologies it should use.
1:19
And the Roadmap lays out what needs to be built.
1:22
In the full Spec Driven Development process,
1:25
the Constitution is only the starting point.
1:28
From there, you would normally plan, build, and review
1:31
one feature at a time, updating the specs,
1:33
as the project evolves. This course keeps that process lighter.
1:37
The specs are already written for you,
1:40
and each time you try a new coding setup,
1:42
you'll give it the same specs and ask it to build
1:45
the entire app in a single request.
1:48
In other words, you'll one-shot the app
1:50
rather than guide the agent through separate rounds
1:53
of planning, building, and revising each feature,
1:56
as you would in the Spec Driven Development course.
1:59
That keeps the focus on comparing how
2:02
different coding setups handle the same project.
2:05
Along the way, you'll use Claude
2:07
Code, Open Code, OpenRouter, and LM Studio.
2:11
You don't need to setup
2:12
or understand all of those tools now.
2:14
You'll learn about each one when
2:16
it becomes relevant. One quick heads up.
2:18
Claude Code requires paid access
2:21
either through a subscription or API billing.
2:24
Not all Claude models are free,
2:26
so you'll also need to purchase a small amount
2:29
of OpenRouter credit later in the course.
2:32
I'll walk you through that when the time comes.
2:35
You can find all the files used in this setup
2:38
including the mission, tech stack, and roadmap in the course repo.
2:43
As a start, let's make a new Python project
2:45
named agent complaints
2:47
in whatever way you prefer.
2:50
command line or in an editor.
2:52
I'm showing this in an IDE which will also initialize
2:56
a Git repository and make a virtual environment.
2:59
You can do those two parts manually if you'd like.
3:03
As a note, I'm using Python 3.14.
3:05
Anything after 3.11, the currently supported version is fine.
3:10
Let's proceed. First, enter your project mission in specs/mission.md
3:17
This file says what the project is
3:19
about and helps keep us on track.
3:21
Remember, you can also find these files in the course repo.
3:26
Next, enter your project's tech stack
3:28
in specs/tech-stack.md.
3:32
This file really helps steer our agent
3:34
for the software choices. Finally, the agent complaints roadmap.
3:40
Enter this in specs/roadmap.md
3:43
As you move towards local AI, getting the roadmap right
3:47
has a big impact on success.
3:50
This tech stack means our Python virtual environment needs some dependencies.
3:55
Let's ask the agent to help. Read the tech-stack,
3:58
create a Python requirements.txt
4:01
and update the virtual environment.
4:05
As the agent works, it will ask you to accept changes.
4:09
You can do this manually each time
4:11
or change your agent settings to accept edits.
4:19
The agent is finished.
4:21
You now have a requirements.txt file and installed dependencies.
4:26
You are now set up.
4:27
This is a good place to do a commit
4:30
to have a known good starting point.
4:34
That wraps the setup.
4:36
In the next lesson, you'll build the first version of the app
4:39
with a basic Claude Code setup.
4:41
The workflow many developers are already using.
4:44
That setup becomes your baseline for everything that follows.