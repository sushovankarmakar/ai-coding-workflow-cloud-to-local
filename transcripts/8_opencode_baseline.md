0:00
You now have a new agent setup
0:02
with a new inference provider and model.
0:04
Let's go build something with this
0:06
by repeating what we did in lesson three.
0:08
With this new setup, the OpenCode agent will go through OpenRouter
0:12
to ask Deepseek V4 Pro to implement the project.
0:16
You're still running in the cloud,
0:18
so this isn't local yet.
0:20
But now more of this setup comes from your choice,
0:23
the agent, the model,
0:25
and the inference provider itself.
0:28
As before, this is a one-shot MVP,
0:31
both phases with a bit of validation at the end.
0:35
Then you'll see, what's the quality?
0:37
The speed, the cost. Do you trust the result?
0:40
Each lesson starts with a new chat with a nice clean context,
0:45
so make sure the chat is using OpenCode
0:47
with DeepSeek V4 Pro as the model
0:51
with medium reasoning.
0:53
Here's the prompt. It's the same as lesson three.
0:56
But since the chat, AKA the
0:58
main agent, is using Deepseek Pro,
1:01
it will run with both a different agent and a different model.
1:06
The prompt is now finished and the project is implemented.
1:10
The agent gives us a summary of the result.
1:13
You switch from something you trust,
1:15
Claude Code and its models to something new.
1:19
Do you trust these results? Let's do more validation this time.
1:23
First, let's look at the main FastAPI application code.
1:28
A quick review shows, it looks good.
1:32
How's your HTML template looking?
1:35
Let's open it, give a quick review, the result
1:38
You got what you wanted.
1:40
The main agent usually chooses to run the test.
1:43
As the human in the loop, let's do this ourselves.
1:46
Open a test file and run it.
1:48
Good news, all tests pass.
1:52
Next, let's run the FastAPI app
1:54
and see how the new setup did.
1:58
When the server starts up, go to
1:59
the local URL to see the app.
2:02
You start on the homepage, looks good,
2:05
you got the Bootstrap styling, same as before.
2:08
Next, the link to the complaints.
2:11
Same date listing.
2:14
Finally, submit a new complaint.
2:16
Then make sure it appears in the list.
2:21
We'll do the same cleanup as before.
2:24
First, let's shut down the FastAPI server.
2:27
Then, delete all the new files and directories
2:30
that were created during this lesson.
2:37
Let's do some reflection.
2:39
As you can see, you altered quite
2:41
a number of choices in the matrix.
2:43
And yet it felt quite normal.
2:45
Since spec-driven development had the plan
2:48
in place, the what was already captured.
2:50
You completely changed the how and got a similar result.
2:54
Let's return to the evidence.
2:55
The direct run used 25 turns,
2:58
38 tool calls, and 530k of context.
3:03
By comparison, lesson three used 19 turns,
3:07
28 tool calls, and 474k.
3:11
The two cent cost demonstrates the pricing advantage of Deepseek,
3:15
not necessarily a better orchestration strategy.
3:18
With that new OpenCode baseline in place, let's keep going.
3:22
You just implemented the Agent Complaints with your new setup.
3:25
And remember, back in lesson four, the next thing you did
3:29
was add subagents in Claude code.
3:31
So, in the next lesson, you'll make
3:34
the same move, this time in OpenCode.