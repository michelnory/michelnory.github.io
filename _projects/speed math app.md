---
title: "Speed Math app"
excerpt: "A mobile first app/website to practice mental arithmetic skills (addition, substraction, multiplication and division)"
header:
  image: /assets/images/thumbnail_speedmathYT.png
  teaser: /assets/images/teaser_speedmath.png
---

[speed math app.](https://8f73439c.speed-math.pages.dev/) is a mobile first app/website to practice mental arithmetic skills (addition, subtraction, multiplication and division).

*To run it on PC click the link and press `Ctrl + Shift + M` to use the proper scaling*

| Property         | Details                                            |
|:---------------- |:-------------------------------------------------- |
| **Stack**        | Python, Flet                                       |
| **Design tools** | Figma (UI Prototyping)                             |
| **Focus Area**   | Cross-platform mobile UX                           | 
| **Source Code**  | [GitHub Repository](https://github.com/michelnory) |

## Motivation
A couple of years ago I got into a mental arithmetic game. At first the game was totally free but over time the app shifted to a yearly subscription model.

Instead of paying for features I didn't want, I decided to build my own arithmetic game. Having previously used desktop GUI frameworks, this project offered the perfect opportunity to evaluate **Flet** and test its performance and responsiveness for mobile applications (even though technically every flet app is cross platform).

## UI Design

![Final UI prototype](/assets/images/prototype_speedmath.png)

The first thing I did was prototyping the full user interface in Figma. This step was crucial for two main reasons:

1. **Flet's Control Constraints :** Creating custom controls is always an option but aligning my ideas with Flet's native control set early on proved to be beneficial.
2. **Layout:** Establishing margins, paddings, and auto-layout rules in Figma made translating the designs into Flet's rows, columns ,and containers straightforward.



## Game Mechanics

<video controls width="100%" preload="metadata">
  <source src="{{ '/assets/videos/demo_speedmath.mp4' | relative_url }}" type="video/mp4">
  Your browser does not support the video tag.
</video>

### Game Generation

When a user starts the game the app randomly selects between 4 and 6 arithmetic problems based on the user's enabled operations and difficulty settings.  As the user completes each problem successfully the game advances to the next until there are no problems left.

### Answer Validation and Auto-leveling. 
Rather than requiring a manual button to submit your answer, the app evaluates user input in real time.

Every time a new problem appears on screen the app will record the time you spend solving that particular problem. When the game is finished users can review the total completion time and average speed per operation.

If auto-leveling is enabled, the app will use these times to adjuts the difficulty level automatically.

### Additional Settings

- Keyboard: The app comes with a custom keypad so that you don't have to rely on your phone's keypad. On PC disable this setting to use your keyboard.
- Operation toggling: users can specify what arithmetic operations are enabled.
- Operation leveling: users can level up or down the arithmetic operations via a slider.