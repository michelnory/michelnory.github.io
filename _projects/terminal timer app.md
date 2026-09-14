---
title: "Terminal Timer"
excerpt: "Terminal-based countdown timer for Windows built with Python and Textual"
header:
  image: /assets/images/terminaltimer_header.png
  teaser: /assets/images/terminaltimer_teaser.png
---

Terminal-based countdown timer for Windows built with Python and Textual

*While Textual is cross-platform, making the app work on Linux/macOS requires replacing Windows-specific features (`winsound` audio alerts and `os.startfile`) with cross-platform equivalents.*

| Property         | Details                                            |
|:---------------- |:-------------------------------------------------- |
| **Stack**        | Python, Textual, UV, winsound, argparse, Git       |
| **Focus Area**   | Terminal User Interface (TUI) utility              | 
| **Source Code**  | [GitHub Repository](https://github.com/michelnory) |

# Motivation
Traditional GUI timers require breaking focus to navigate menus or click buttons.  This project provides a fast, keyboard-centric timer that starts directly from a terminal command like `timer -m 10`.

# Stack
- **Textual :** TUI framework used to render the interface right in the terminal.
- **uv :** Used for project dependency management and global command installation via `uv tool install .`
- **argparse :** Standard library package used to parse command-line flags (`-m` / `--minutes`).
- **winsound and json:** Standard library packages used for playing alarm sounds and persisting audio settings to JSON.
- **Git :** Version control.

# UI Design and Features

<video controls width="100%" preload="metadata">
  <source src="{{ '/assets/videos/terminaltimer_demo.mp4' | relative_url }}" type="video/mp4">
  Your browser does not support the video tag.
</video>

For this project, I wanted a clean and minimal aesthetic. Only a large digital countdown display appears on launch.

-  **Custom Alarm Sounds:** Supports standard beeps and custom `.wav` audio files stored in a local `sounds/` directory. 
-  **Interactive Command Palette:** Allows searching and executing reset, pause, resume, change timer, and sound settings.
-  **Modal Overlay:** Pressing `c` pops up an inline input modal to dynamically change timer duration on the fly.

# Installation and Usage
1. Clone the repo and `cd`  into the folder
2. Sync environment and install as system-wide tool
	- `uv sync`
	- `uv tool install .`

Now you should be able to run `timer` to get a default 3-second countdown

Start a countdown for `n` minutes:
``` bash
timer -m n
# or
timer --minutes n
```
**Tip:** Set up a Raycast shortcut to run the timer directly, without opening a terminal window.

<video controls width="100%" preload="metadata">
  <source src="{{ '/assets/videos/terminaltimer_raycast.mp4' | relative_url }}" type="video/mp4">
  Your browser does not support the video tag.
</video>
## Keyboard Shortcuts

- **`r`**: Reset the timer back to its initial starting time.
- **`P`** (Shift + P): Pause the active timer and stop any playing alarm sound.
- **`R`** (Shift + R): Resume a paused timer.
- **`c`**: Open the modal screen to change the timer duration.
- **`Escape`**: Dismiss/close the time-changing modal screen.
- **`Ctrl + P`**: Open command palette
- **`Ctrl + Q`**: Quit the app

**Tip:** To view al available commands search *keys* directly inside the command palette
