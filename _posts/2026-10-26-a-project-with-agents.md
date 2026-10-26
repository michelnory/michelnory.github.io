---
title: "Creating a game with Agents"
categories:
  - Blog
tags:
  - AI
  - Tinkering
---
Lately I’ve been learning about Agentic Coding. All about MCPs, Skills, SDD and other techniques for getting the most out of AI agents.

AI is nondeterministic. The same prompt can produce different answers, so you can't always predict what an AI model will generate. This happens mainly because the natural language we use is pretty imprecise. When we give an agent instructions, there's always room for misunderstanding.

Using AGENTS.md files, Skills and Spec-Driven Development (SDD) we narrow drastically the room for misconception by giving clearer instructions, more context and explicit requirements.

# Pymon

I’ve been playing around with these techniques, but not in meaningful projects. But the other day, checking my list of project ideas, I found the right project: A clone of the classic Simon game, written in a fully responsive Flet app (Python).

I decided to call Pymon.

I didn't want to rely entirely on an agent to do all the coding (as in a pure SDD-style workflow). Instead, I decided to implement the core logic myself and then I’d use an agent to fill in the gaps.

![pymon diagram](/assets/images/pymon_diagram.png){: .align-center}

## What I did

The core logic was easy to implement. We need four colored buttons, one button to start the game and a counter to display the current level.

When we start the game, Pymon will click the colored buttons in a sequence. The player must repeat the sequence in the same order to advance to the next level.

{% include video id="19sBFY2_jpDKLD0kjla3XzGODtz5jBG4z" provider="google-drive" %}

## What the agent did

For this project I used OpenCode with the free model  *Nemotron 3.5*. I wrote a good AGENTS.md file and integrated the official Flet MCP into the project.

At this point, I had a game that worked the way it was supposed to but it didn't quite look right. With a few prompts, I got the agent to build the board, and with a couple more I made the layout responsive.

{% include video id="1xvmJw4VPW8kc3ykW0vOmBFa-Bk1ZWFNR" provider="google-drive" %}

Adding the functionality to switch between dark and light-mode by long-pressing the Pymon button was easy as well. 

{% include video id="1u9_K2ACuc4SgfbScVMd3qQnowLTFZ1AV" provider="google-drive" %}


## What went wrong, and how I solved it

### The audio

The final step was to package the app in some way to use it in my iPhone. Since I don't own a Mac I had to make the app available online. I decided to self host the app on my ZimaOS server.

That meant putting my Docker knowledge to the test. I had to create a Dockerfile with the necessary requirements and then upload the image to DockerHub. 

I ran into a TON of problems. Why, you ask? 

Well... to make the game more fun I decided to play a sound every time a button was pressed. Unfortunately, the package I initially used to play the audio wouldn't load properly inside Docker. 

The agent pointed me to `flet-audio` , the supported way to play audio in Flet. Somehow, I'd never heard of it 🤦.

I ask the agent to rewrite the audio functionality using `flet-audio`. That didn't work and I had to rewrite it myself. 

Thinking about it now, it made total sense that the agent struggled with the task. My original implementation was incompatible with the way `flet-audio` works, so a one-to-one replacement was impossible.

Once I made the rewrite, I could finally run the game inside a Docker container on my machine.

### The server
After spending a couple hours trying to figure out why the game wouldn't work on my server, even though the container ran perfectly on my machine, I decided to change the approach and host it on Cloudflare. 

You can check the result here:  [Pymon](https://pymon.michelnory2000-9f0.workers.dev/)

### The audio (on phone)
The app runs smoothly, but only if you open it on a desktop browser. On a phone, the audio lags and sounds strange enough that I'd rather play without it.

I haven't figured out why this happens yet, but i'll update this post if I get to the bottom of it.

# Conclusion

If there's one thing I take away from building Pymon it's that getting the most out of AI requires proper planning. Thinking about the project as a whole from its structure and core logic to the visual design (if applicable).

Before touching a code editor it's worth asking yourself:
- What components is the project made up of? 
- What is the core functionality that all of these components rely on?
- How should each feature behave?
- Does the layout need to be responsive?
- What requirements or constraints should I consider?
- etc. 

In previous projects, I haven't paid enough attention to the planning phase.

After spending a couple of hours solving problems caused by poor design decisions, you realize quite quickly how taxing it is to plan a project while you're doing it. More often than not, you end up rewriting big portions of the code to fix bugs or accommodate new features.

The audio issue taught me something else: you need to know the tools you are working with. Agents are a powerful tools but when you need to fix something, you need enough knowledge to understand what went wrong and figure out how to fix it. You can't fix something you don't understand in the first place

Ultimately, I want to get better at using these tools. I think a reasonable next step is to revisit some of my previous projects and see how I can improve them using an agentic approach.

So stay tuned for that!
