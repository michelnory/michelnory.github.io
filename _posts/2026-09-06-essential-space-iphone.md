---
title: "Nothing's Essential Space functionality in iPhone"
categories:
  - Blog
tags:
  - iPhone
  - Tinkering
---

# Intro
Throughout the day we are bombarded with new information and ideas. Not everything is important but every now and then you stumble upon a post, come up with an idea or even a picture that inspires you, other times you just need a place to write something down for later. If we don’t manage what we save we risk losing it.

In the past I’ve used the notes app of my phone, my own WhatsApp contact, Notion, a piece of paper lying around,… But there’s always friction capturing those things and even more friction reviewing them later.

Not only did I needed a system that allowed me to capture whatever was on my mind and on my screen but a system that made the reviewing process as easy as possible.

The moment I saw Nothing’s presentation of the Essential Space button I knew it was the tool I was looking for.

<iframe width="1041" height="586" src="https://www.youtube.com/embed/pAzJPmsWgKU" title="Essential Space: Your Second Memory" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


Pressing the extra button in Nothing's phones triggers the Essential Space app. This app allows you to quickly capture text, videos, pictures and audio from whatever is on your screen or supplied by you. it also allows you to organize the things you capture and finally it integrates AI to transcribe audios, summarise content, create tasks from your notes and much more.

![Essential space mind map](/assets/images/essential-space-mindmap.png)

The main problem was that I had an iPhone. So that idea stayed in the back of my mind for a couple of months.

#  The Shortcuts app

Developing an app for iOS was out of the question because a while back (trying to package the speed maths app I developed) I discovered that you need to get a certain license to use the apps you develop in your **own** iPhone, (and Google is trying to do something similar with Android… so we need a proper Linux phone, am I right?). Anyway, I turned my head to Shortcuts, the iOS and MacOS way to build extra functionality without code and more importantly without a developer subscription.

I’d already built several simple shortcuts to make my life easy so I had a little experience.

The idea is to create two shortcuts. Both of them will do the following:
1. Prompts the user for a title.
2. Asks the user to select from a set of tags.
3. Prompts for additional details/information.
4. Creates a Markdown file inside an Obsidian vault folder with the following properties. 

```yml
---
checked:
tags:
URL:
Date: 
---

```

- The *simple entry* shortcut is aimed at simple ideas/notes/tasks I want to remember so it'll follow the exact outline already explained
- The *share* shortcut in addition to all of that will copy the url (instagram posts, youtube videos, blog posts, etc) of the thing I wanted to share into the property `URL`



Since I don’t own a Mac I had to make these shortcuts with the iPhone app, and making something a little complex in that app is a bit of a pain. Regardless, I managed to create both shortcuts. I'm sure I could've moved the logic of the *simple entry* shortcut inside the other or added some other features but for now it gets the job done

<video controls width="50%" preload="metadata">
  <source src="{{ '/assets/videos/essential-space-shortcut.mp4' | relative_url }}" type="video/mp4">
  Your browser does not support the video tag.
</video>


I don’t have a spare button on my iPhone so I trigger the *simple entry* shortcut with a double tap on the back of the phone. And I acces the *share* shortcut in the iPhone's share sheet as seen in the video.

Of course it’s not the fully featured essential space from Nothing’s phones and I'm always changing things but I'm happy with the result for now
