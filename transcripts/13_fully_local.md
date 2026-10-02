0:00
You now have your implementer sub-agent running on a local model.
0:03
The main agent is still using a cloud model.
0:06
But can you go fully local
0:08
and bring the big brain local too?
0:10
You have been running the big brain on a hosted inference provider.
0:16
You moved the little brain to your local computer
0:19
using Gemma 4 as the model.
0:21
Now you're going to move the big brain role local too.
0:25
That role asks more of the model.
0:27
It has to plan the work, prepare handoffs for the implementer,
0:31
and review the results, so you'll need to choose a model
0:35
that can handle the work while still running on your computer.
0:38
There are a number of things
0:40
you should consider when choosing a model,
0:42
including the number of parameters.
0:44
Larger models can often handle more demanding work,
0:46
but they also require more memory.
0:49
I won't cover every facet of that decision here,
0:52
but the Qwen family of models
0:54
is a leading choice for agentic coding.
0:56
They have models ranging from local sized
0:59
up to large hosted frontier class models.
1:03
Running a larger model locally requires more memory.
1:06
So this lesson is aimed at a computer
1:08
with 32 gigabytes.
1:10
If your computer has less, you can
1:12
still follow along without running the model yourself
1:15
or try a smaller one if you're feeling adventurous.
1:18
Just don't be surprised if it falls flat on its face.
1:22
For the local big brain, you'll be using Qwen 3.5 27B.
1:27
As its name implies, it has 27 billion parameters,
1:31
more than twice Gemma 4's 12 billion.
1:34
Models like Qwen are often available in different variations.
1:38
Some are prepared for particular hardware or compressed to use less memory.
1:42
Hugging Face is a useful resource for finding these variations.
1:46
The user Brooooooklyn is a well-known and respected contributor.
1:51
In LM Studio, let's find the model page for his MLX variants.
1:55
I'm recording on a Mac, so for my use,
1:58
I want the MLX version when available.
2:01
For non-Mac, find a variant for the GGUF version.
2:05
This lesson targets a 32 gigabyte budget.
2:08
And Gemma 4 already uses around 11 gigabytes.
2:11
For Qwen, you'll use the Q4 quantization
2:14
of the open source Qwen 3.5
2:17
27B model.
2:20
Q4 makes a model smaller at the expense of some accuracy.
2:25
Obviously, this doesn't leave available memory for anything else.
2:28
That's okay for demo purposes, but as you move to local,
2:32
you'll be making a number of decisions and tradeoffs.
2:35
Start downloading the model. It's big.
2:38
The Q4 is almost 21 gigabytes.
2:41
Now that it is downloaded,
2:43
let's do the same kind of model tuning that we did before.
2:47
We're only changing one parameter.
2:49
We'll set the context size to 80k.
2:52
And if you struggle with memory, lower this. It'll probably be fine.
2:57
Go to the LM Studio server
2:59
and tell it you want to
3:00
load this model and make it available.
3:04
We'll do a quick chat to load the model into memory
3:06
and warm things up. Head to the LM Studio chat.
3:09
Make sure you are using Qwen 3.5 as the model.
3:13
Ask your normal prompt. What is Python?
3:22
You can now serve this model through LM Studio.
3:25
Next, you need to go to OpenCode
3:28
to let it know about and in fact default to
3:31
this new Qwen model. As you did in lesson 10,
3:34
let's use a prompt to edit the global OpenCode configuration file.
3:39
Let's confirm this works. Start a new chat
3:41
in the OpenCode model picker, you should see Qwen
3:44
3.5 27b.
3:46
Choose it and enter the same prompt that you used above.
3:53
Want to prove that it worked? Go to LM Studio
3:56
and look at the server activity. There you'll see
3:58
that some requests just came in for Qwen 3.5.
4:02
Before coding, did we clean up after the last lesson? Let's confirm.
4:06
No, I committed changes
4:08
and no Python files in your project.
4:11
As a reminder, this barely fits in 32 gigabytes.
4:14
If you have a smaller computer,
4:16
there are choices, but they take more work.
4:18
And finally, even at 32 gigabytes,
4:21
things can be unpredictable.
4:23
Hopefully your experience is close to what I'm showing.
4:26
Using Qwen 3.5 27B
4:29
as the model for the main agent.
4:31
Let's repeat the sequence from lesson 11.
4:34
How will a local model do as the big brain?
4:37
We will use the same long prompt.
4:40
Remember, you can copy this from the course resources.
4:43
And yes, the long text shows
4:45
how agents or plugin developers can ship
4:48
pre-packaged help for small local models.
4:51
As the results go by, the moment of truth arrives.
4:54
How did the local big brain do at writing the handoff packet?
4:59
A moment of surprise. This hand-off packet looks better
5:03
than the much bigger Deepseek Flash brain. Very promising.
5:11
Local? Check. Cheaper? Check. Fast enough? Uh, maybe.
5:15
But how's the quality? Let's start by looking at the reported issues.
5:20
This is a double whammy, a small
5:23
brain implementer with a small brain main agent.
5:26
Surprisingly, huh, no reported issues.
5:29
All good. Sure, this is a toy example.
5:32
But if you use a very
5:34
big brain to make your road map,
5:36
its phases can be shaped to fit.
5:39
Let's repeat this process for phase two.
5:41
The main agent sends the same prompt
5:44
with phase two instead of phase one.
5:46
As the results go by, let's look again at the hand-off packet.
5:58
Did the main agent help the small model succeed? Results look good.
6:03
Again, no critical issues in the results
6:06
and in fact, the execution time was reasonably fast.
6:10
We can repeat for Phase 3 by reusing the same prompt.
6:23
Ah, this time a critical issue.
6:27
Actually, not so critical.
6:29
This is a common minor issue about HTTP redirects,
6:33
but it did cause a test to fail.
6:35
Let's have the main agent send repair work
6:38
to the implementer sub-agent.
6:40
The main agent has the context about the mistakes.
6:43
As usual, let's look at the handoff packet.
6:46
It looks good with the right details.
6:49
Progress continues and all the tests pass.
6:52
And at the perfect moment, why yes, my agent friend,
6:55
you are truly doing excellent.
6:57
You are now fully local for both brains.
7:01
Do you trust it? Let's do some human in the loop.
7:04
We'll start by running the tests manually
7:07
rather than trusting the models
7:09
to run and interpret the output.
7:11
Of course, the part we really want, how does the app look?
7:15
Start the server. How are your two pages?
7:19
The homepage seems fine
7:21
as does the complaints page.
7:23
Last test, adding a complaint.
7:27
It works.
7:29
You're here, fully local. How do the numbers look?
7:33
Lesson 12 shifts the workload from main
7:35
agent to sub-agent compared to lesson 11.
7:38
Main agent context fell from 260K to 178K,
7:42
while sub-agent context rose from 117K to 158K.
7:47
Total context still fell 11%,
7:50
showing that the local Qwen main agent
7:52
used less context overall,
7:55
while the Gemma implementers did more iterative work.
7:58
Turns changed far more than tool calls.
8:01
45 turns versus lesson 11's 6.
8:05
but only 57 tool calls versus 51.
8:08
This is an important model behavior result.
8:11
The lesson 12 models used many more assistant turns
8:14
to achieve nearly the same amount of tool activity.
8:17
So turns should be interpreted as an interaction style,
8:22
not simply as work completed.
8:24
The all local execution
8:27
correctly has zero attributable usage cost.
8:30
Phase three was the largest sub-agent task at 12 turns, 11 calls
8:35
and 69000 context tokens,
8:38
which fits its form, post, redirect, and test requirements.
8:42
We are just at the beginning of agents with local models.
8:45
Very few agent harnesses have been written
8:48
to specifically help these small models succeed.
8:51
But the first experiments are proving successful.
8:54
By the end of the year, I expect new harness approaches
8:58
to put local agent coding
9:00
for routine work that doesn't need the big brain within reach.
9:04
One last note. If you're on a smaller computer
9:07
and couldn't run this, hope is not lost.
9:10
It will take work, but you can experiment with models
9:13
that very aggressively reduce the size.
9:15
You can then judge the quality tradeoff.
9:18
Most of all, keep an eye on new agent harnesses
9:21
rather than focusing on models.
9:23
You made it, the end of the road.
9:26
You've taken your AI coding setup all the way from the cloud
9:29
to models running on your own machine
9:32
and you've seen what it takes to push toward fully local.
9:36
In the final video, you'll look back at what you've learned
9:39
and ahead to where hybrid and local AI goes from here.
9:43
I'll see you there.