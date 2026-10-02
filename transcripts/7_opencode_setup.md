0:00
So far you've been working in Claude Code,
0:01
but choosing Claude Code as a coding agent means
0:04
you're locked into the Claude ecosystem.
0:06
And as you move toward local AI,
0:09
you'll need more flexibility than that.
0:12
So in this lesson, you'll start taking back control,
0:15
starting with the coding agent itself.
0:18
You saw in the last lesson that Claude Code
0:20
can run Sub-Agents on different models.
0:23
But these models are hosted and they are from one vendor.
0:27
Claude Code wasn't built to go far from this approach.
0:31
Fortunately, there are many coding agents
0:33
to choose from, including open source options.
0:36
For this lesson, we'll use OpenCode.
0:39
It is a popular, powerful, and mature choice.
0:42
OpenCode also comes in several flavors:
0:45
a command line version, a desktop
0:47
app, a web version, and IDE integrations.
0:51
In this lesson, we'll use the IDE version through ACP,
0:54
which is just the connection which lets the coding agent
0:57
work directly inside your editor.
1:00
But you should try the different options and
1:02
find the one that fits your workflow best.
1:06
You'll click New Chat to start a new chat window.
1:10
It defaults to the Claude Agent.
1:12
That menu though, lets us install from the ACP Registry.
1:17
There you'll find a long list of agents.
1:20
Scroll down to OpenCode and click Install.
1:23
Then click Apply and click OK to close those settings.
1:27
Back in the chat window, OpenCode is now the agent.
1:31
You'll then see a listing of models that OpenCode themselves host.
1:36
Let's make sure to choose Big Pickle,
1:39
one of OpenCode's currently free hosted demo models.
1:42
It's a quick, low-stakes way to
1:45
test that OpenCode is installed and working.
1:48
You'll enter a simple prompt just to confirm OpenCode is set up.
1:52
The engine changed from Claude, but the AI chat should be similar.
1:57
Changing the coding agent was the first layer.
2:00
But the agent still needs a model to talk to.
2:04
Now that you've moved away from Claude Code,
2:07
you're no longer restricted to Anthropic models.
2:10
OpenCode can connect to many different models,
2:13
but setting each one up separately means
2:16
juggling accounts, keys, and billing.
2:19
That's where OpenRouter comes in.
2:21
It gives OpenCode one API connection
2:24
to a catalog of models
2:25
so you can choose the model
2:27
while OpenRouter handles the rest.
2:30
OpenRouter charges based on token usage,
2:33
so later you'll add a small amount of credits for this course.
2:36
Now, the models are still running in the cloud, but
2:40
You now control which model your coding agent uses.
2:44
First, go to the OpenRouter site and create a login.
2:51
Once you've created the account, this
2:53
is what the dashboard will look like.
2:56
Once logged in, you have a two-step process.
3:00
You first add some credits to your account.
3:03
For this course, you can add the
3:05
equivalent of $10 and that should be plenty.
3:08
I already have an account with credits.
3:11
For your account, click Add Credits
3:12
and follow the screen to provide $10.
3:16
Next, you need to make an API key.
3:19
This is how you will connect your OpenCode
3:22
into the use of OpenRouter.
3:27
Finally, copy this API key to the clipboard.
3:30
It's important to do this now as
3:32
you can't come back later and get it.
3:35
Also, API keys are a secret.
3:37
Don't share this with anyone. Back in the IDE, you
3:41
can configure OpenCode
3:43
to add OpenRouter as a provider.
3:46
You can choose to edit the obscure OpenCode JSON file yourself,
3:51
but hey, you have OpenCode.
3:53
Just tell it to set up OpenRouter.
3:57
Once done, you start a new OpenCode chat.
4:01
After a couple of seconds, voila,
4:03
you have the OpenRouter models.
4:06
What does OpenRouter give you? Access to lots of models
4:10
hosted at inference providers,
4:12
all through a single account and API key.
4:16
You now have OpenCode connected to OpenRouter
4:19
as both a router and inference provider.
4:22
Now select the model you want to use.
4:25
Deepseek V4 Pro in particular
4:27
is a good fit for what you're doing.
4:29
At the time of this recording,
4:31
compared to Anthropic models, Deepseek Pro
4:34
is cheaper than Haiku, but more powerful than Sonnet.
4:38
OpenRouter gives you access to Deepseek V4 Pro and Flash
4:42
through the credits you just added.
4:44
You'll start with Pro and now let's get OpenCode to use it.
4:49
First, you change the current chat to use DeepSeek Pro.
4:53
Click the model picker, find DeepSeek V4
4:55
Pro in the long list and select it.
4:58
You can now do a prompt
5:00
confirming OpenCode works with OpenRouter
5:03
using our target model.
5:11
That long model list is cumbersome. Let's do a bonus track.
5:17
You'll use a prompt to configure
5:19
OpenCode to only show what you want.
5:23
You'll be using DeepSeek Flash, so you include that as well.
5:27
OpenCode will then edit its configuration file.
5:32
Your prompt also defaults the model reasoning level to medium.
5:37
Let's confirm this works.
5:39
Start a new chat and the model picker should default
5:42
to your last used model, Deepseek Pro,
5:46
and the list should only include two models
5:49
at the default reasoning.
5:52
Send a hello prompt and confirm
5:54
we're using one of our two models.
5:57
You're now ready to return to development.
6:00
Looking back again at your matrix,
6:01
this lesson changed quite a bit,
6:04
agent, provider, and model.
6:06
This provides control, but this choice shifts responsibility to you.
6:10
Let's face it, the choice can be overwhelming.
6:12
So many good agents to choose from.
6:15
So many models, each with variations in size.
6:18
And you haven't even started yet on running these things
6:22
semi-locally or locally.
6:24
As you split up the monolith,
6:26
you'll find multiple places to have different
6:28
model choices for parts of the workflow.
6:31
The hope in this course isn't to say, do this.
6:33
It's to teach you how to think about these choices.
6:36
Again, everything is changing quickly.
6:39
Changing from Claude Code to another agent is a big step.
6:42
But so far, it's just a setup.
6:45
In the next lesson, you'll put it to work,
6:47
building the same project again,
6:49
this time with your new agent and model.