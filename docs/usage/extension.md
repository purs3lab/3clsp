---
layout: default
title: Extension Usage
parent: Usage
nav_order: 1
---

# [](#header-1)Using the Extension

After setting up the editor and the extension. Open up VSCode and open your project by pressing `Ctrl+K & Ctrl+O` and selecting your project folder. Make sure your project has a compile database as mentioned earlier(`compile_commands.json`).

## [](#header-2) Starting the Conversion Process

Once you open up the project, just navigate to the first seen `C file` so that the `clangd` server starts up. Once the server starts up, head to the command palette using `Ctrl+Shift+P`. A pop-up on Top-Center appears to give you choices for commands to run. 
![](../../assets/images/command-palette.png)

"[Command Palette]"

Try to search for `Run 3C on this project`, run the command which will start the conversion process on your project. Depending on the size of the project, the conversion might take anywhere from 5-15 seconds to finish. The info boxes on the bottom right will serve as a guide to the progress of the conversion.


