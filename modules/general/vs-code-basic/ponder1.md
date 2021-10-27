---
title: Vs Code Basics - Ponder activities.
description: Practice using VS Code
date: 2021-10-15

layout: layouts/post.njk
---

## Learn your tools

Good tools can help you work more efficiently...but only if you spend the time to learn what they can do for you!

I once had to move a group of users off of the old main frame menu driven system they had used for years to a new shiny web based system...they hated it! Why? Keyboard driven interfaces are faster than mouse driven ones once you learn them. Everytime you have to take your hands off the keyboard and mouse it slows you way down...learn the keyboard shortcuts for the common tasks you do.

### Shortlist of useful keyboard shortcuts

- cmd/ctrl + shift + P: opens the command palette
- cmd/ctrl + B: Open/close the sidebar
- cmd/ctrl + P: Switch to another file in the project
- cmd/ctrl c,v,z,s: Copy/paste/undo/save
- cmd/ctrl + D: add selection to next Find match
- cmd/ctrl + /: toggle comment for current line (or selection)
- alt + Z: toggle soft-wrap
- alt + up or down arrow: move current line (or selection) up or down

## Projects

Make sure you are always working in a project instead of just random open files. How do you tell? Hint...if the bar at the bottom of your editor window is purple instead of blue you do NOT have a project open and some features of Code will not work.

The other way to tell is if you open at the Explorer sidebar (Icon that looks like two pages)...if you do not have a project (folder) open there will be a big button that says "Open folder"

Create folders for each of your projects and then don't be shy about switching project folders in VS Code.

VS Code also has the ability to create [Workspaces]

## Extensions

A good tool these days should be extensible. Here are a few extensions I like and recommend:

- **Beautify or Prettier**: These will automatically format your code for you...you (and I) will spend so much less energy reviewing well formatted code!
- **LiveServer** Live preview of html files in the browser of your choice.
  After installing the Live Server extension, you may need to do a small amount of configuration. We can set Live Server to use any browser. Do the following to set a custom browser for Live Server to use:

  1. Click on the Gear icon in the bottom left corner of the VS Code application window, then select 'Settings'.
  2. In the Search settings box at the top of the new tab that opened type "custom browser"
  3. Find the setting "Live Server > Settings: Custom Browser". In the drop down below that select the browser you would like. (Often this will be Chrome.)

  **A theme you love** (I'm currently using Cobalt2, but I also really like Hop Light and Night Owl Light)

- **Project Manager**
