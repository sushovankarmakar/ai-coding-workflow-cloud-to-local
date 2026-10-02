0:00
Subagents let you implement with a fresh context.
0:03
But they also open the door to something more.
0:06
Doing the detailed work on a cheaper model.
0:10
In this lesson, you'll get your subagents to operate on Haiku,
0:14
Claude Code's less expensive option.
0:17
The idea is simple. Once the work is split
0:19
into smaller tasks through subagents,
0:22
Maybe those tasks don't need to be on the most expensive model.
0:26
But cheaper models are cheaper for a reason.
0:30
If the work is too broad or too vague,
0:33
you might spend more time and money fixing mistakes
0:36
than you would have spent just using
0:38
the bigger model in the first place.
0:40
So the move here, use the bigger model as the big brain
0:44
that does the thinking, while the smaller model,
0:47
the little brain, is the doer or implementer.
0:50
There are lots of small, specialized tasks
0:53
that can use small, specialized Sub-Agents,
0:56
but only when managed by a Main Agent.
0:58
For example, you can also use the big brain
1:01
to judge the Implementer's results,
1:04
perhaps sending corrections back to fix.
1:06
Now, you can do all of this directly in the prompt.
1:09
For example, you could start a new chat
1:12
in your default model of Sonnet,
1:14
but in the prompt tell Claude Code to use
1:17
Haiku to answer the question.
1:27
This lets you choose the best price performance for each task.
1:32
You can even use Opus, an even more powerful model,
1:36
for example, at the kickoff to guide the architecture
1:39
and shape the overall roadmap,
1:42
as well as periodic full project reviews.
1:44
Then, in a feature loop,
1:46
use Sonnet for planning and orchestration and
1:50
Haiku for each implementer subagent.
1:53
This is a central point of this course.
1:55
Smaller models can be successful when guided with a small, tight spec.
2:00
Good planning and spec is important for success.
2:03
Bad plan leads to awful result.
2:06
As usual, let's start by making sure
2:08
we cleaned up after the last lesson.
2:11
No uncommitted changes and no Python files in your project.
2:17
Let's also repeat our mantra, clean context.
2:20
Starting a new chat to start this new lesson.
2:23
But make sure the model choice is Sonnet.
2:27
We're now ready for switching models for subagents.
2:31
As usual, you'll do a one-shot prompt for both phases.
2:35
In the last lesson, you routed the implementation to a subagent.
2:40
This time, you'll add an instruction to run the subagent
2:44
with Haiku as the model.
2:46
Pay attention to the end of the prompt.
2:49
You've been finishing each one-shot by asking for a review.
2:53
In this lesson, it's extra important.
2:56
You'll ask the big brain to review the little brain.
3:00
The results will again show the subagent box with the detail.
3:05
All finished and likely a bit quicker
3:07
as Haiku is a fast model that's also cheaper.
3:11
But how are the results? Let's take a look.
3:15
You're using a cheaper implementer, so let's do more validation.
3:20
First, take a look at what the main agent reported.
3:23
Did it find any issues with the final result?
3:27
Some points will be minor even if they're called critical.
3:31
You can clean them up now or group them into periodic cleanup.
3:35
You'll see more about this later.
3:37
Our prompt asks for tests, but
3:39
perhaps the main agent didn't run them.
3:42
Let's do some validation through test running.
3:46
The test passed which means our approach is passing basic validation.
3:52
Does the site run?
3:57
Run the server and check the two pages in the browser.
4:02
Is the homepage okay?
4:05
Do you still have complaints?
4:07
and can you submit new ones?
4:15
Everything works fine. The smaller model with help from the bigger model
4:19
was able to implement.
4:23
Let's do the end of lesson cleanup.
4:25
Shut down the FastAPI server
4:29
and clean up the files.
4:32
You have now entered the big part of the comparison,
4:36
Sub-Agents with a smaller model. This is always a tradeoff.
4:40
Smaller models are cheaper and faster, but make mistakes.
4:44
Too many mistakes leads to more turns, meaning more attempts.
4:48
And more turns and you'll pay more and take more time.
4:52
The trick, use Spec Driven Development
4:54
to give plans to the main agent and model
4:57
and get it to give small tasks and plans
5:00
to the smaller agent and model. Let's see the numbers this time.
5:04
Compared with the previous lesson, this setup uses 50% more turns
5:08
and 48% more tool calls,
5:11
but only 29% more context.
5:14
Most of that growth was in the subagents.
5:17
But also notice the subagent turns became lighter.
5:20
That is, the average context per subagent turn fell
5:24
from 21k in the previous setup
5:27
to 17k in this lesson.
5:29
Across all three setups, the main agent
5:31
stayed comparatively steady
5:34
while the subagent activity expanded dramatically.
5:37
Cost, however, dropped notably because the context
5:40
was largely in the subagents, which worked in the cheaper model.
5:44
This gives you another useful comparison, but
5:46
it also brings you to the limits
5:48
of what you can explore within this setup.
5:51
So far, you've used a fully hosted setup
5:53
as a familiar home to learn the key ideas
5:57
about specs and subagents and different models.
6:02
But if your coding agent keeps you inside one ecosystem,
6:06
your choices are pretty limited. So, in the next lesson,
6:10
you'll start opening up the path towards hybrid and local setups
6:15
by choosing the coding agent itself
6:18
and the models it connects to.