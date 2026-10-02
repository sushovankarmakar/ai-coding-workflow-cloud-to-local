0:00
At this point in the course, you've
0:01
changed the coding agent and the models,
0:03
but the models themselves still run in the cloud.
0:07
In this lesson, you'll set up your first local model,
0:10
one that runs on your own hardware connected to OpenCode.
0:14
Running a local model takes some
0:16
software to serve it, an inference server.
0:19
Perhaps running on your very powerful desktop,
0:22
or perhaps on a computer in the corner of your room,
0:25
or on a server inside your company's data center.
0:29
or even in a private cloud.
0:31
All of these options share the same word, "your".
0:34
You make the choice based on your needs.
0:37
You have control of the setup.
0:39
When I say local, really, I mean your.
0:42
Local AI has taken off recently with many friendly options.
0:46
Command line and GUI, cross-platform, and high performance.
0:50
You'll go beginner friendly and use LM Studio.
0:54
It runs on both Windows and Mac,
0:56
well known and well supported.
0:58
LM Studio makes it easy to browse and download models,
1:02
start and stop servers,
1:03
and do all kinds of performance tuning.
1:06
First, download LM Studio for your platform.
1:09
I'm using Mac, but Windows should be familiar.
1:12
I won't show the entire installation process.
1:15
LM Studio has helpful instructions for this.
1:18
Once running, LM Studio gives the major areas that you'll need.
1:22
a chat to work with the server and a model,
1:25
the developer tab to start the server and see the logs,
1:29
My Models tab to work with the models you've downloaded,
1:32
and model search to find new models.
1:34
Let's talk about our choice of
1:36
local model and then get it set up.
1:38
In this first step, you are targeting a local model for coding
1:42
that can fit in a 16 gigabyte
1:44
desktop with room to spare for your work.
1:47
Turns out there are tons of choices and
1:49
the market is getting better all the time.
1:51
But equally, this is a hard problem.
1:54
Doing agentic coding is resource intensive,
1:56
16 gigabytes is a tough target. We did some testing
2:00
a measurement that also included the most
2:02
popular choice for a small language model,
2:04
Qwen 3.5 9B.
2:06
You're free to use that in the
2:08
course. Nearly everything will be the same.
2:10
For this course, you'll use Gemma 4,
2:12
a 12 billion parameter mixture of experts
2:16
open source model that is focused on coding.
2:19
It's available on Hugging Face,
2:21
the super popular hub for all things
2:24
AI. You'll need to get Gemma 4 downloaded and running.
2:27
Go to LM Studio, click on model search,
2:29
and search for Gemma 4, the 12 billion parameter version,
2:34
the IT variant.
2:36
I'm specifying MLX because I am on Apple Silicon.
2:40
Use GGUF, G-G-U-F, if you are not.
2:44
We are choosing the 8-bit quantization to get better results.
2:48
Start the download. It's around 12.77 gigabyte,
2:51
so it might take a while. It's now downloaded.
2:58
Next up, tuning.
3:00
Local AI folks love fiddling with knobs.
3:03
You're just going to set one.
3:05
Change the Context Length to 40960.
3:09
If you struggle with memory, lower this.
3:11
You might be tempted to do a huge context size.
3:15
Don't. One of the lessons learned,
3:17
keep your sub-agent small and focused.
3:21
Click the button to load the model.
3:24
And your LM Studio is now set up for local inference.
3:28
Let's start the server.
3:30
Before heading to OpenCode to set this up for our agent,
3:34
use the local model for simple chat.
3:37
Go to the LM Studio chat screen and enter something simple.
3:42
Don't get too excited. Chat is always faster than agent use.
3:47
Let's head over to OpenCode and set
3:49
up local Gemma 4 as your little brain.
3:53
Next, we need OpenCode to see LM
3:55
Studio and its Gemma 4 model endpoint.
3:59
We will need the local URL
4:00
and a model name in a moment.
4:02
Here you can get it. This will be the same idea.
4:05
An URL, this time for localhost,
4:08
to get to the provider, then a model ID
4:11
for the Gemma 4 model you just set up in LM Studio.
4:15
OpenCode knows about OpenRouter as a provider,
4:19
you need to teach it about
4:21
your local LM Studio as a provider,
4:24
and about Gemma 4 as a model,
4:26
want to edit the OpenCode json config file yourself? Neither do I.
4:31
Let's ask OpenCode to configure this by entering this prompt.
4:39
Let's confirm this works. Start a new chat.
4:42
In the OpenCode model picker,
4:45
you should see Gemma 4 as a choice.
4:47
Choose it and enter the same prompt that you used above.
4:51
The speed depends on your equipment.
4:57
You'll be disappointed.
4:59
The first request is slow as it has to load the model.
5:02
Try a variation of the same prompt
5:04
and you'll see it is really fast.
5:06
Skeptical that it really used LM Studio and Gemma 4?
5:10
Don't blame you. There are a bunch of moving parts.
5:14
Go to LM Studio and look at the server activity.
5:17
There you'll see some requests just came in for Gemma 4.
5:21
Before we wrap up, take another look at the big picture.
5:25
You can see how many parts
5:27
of the original setup have now changed.
5:30
Congratulations, you've taken your first step into local AI.
5:34
Your model is now running locally and connected to OpenCode.
5:37
In the next lesson, you'll put
5:39
it to work as your implementer sub-agent.