---
title: CLI basics - Mac
description: Getting started with the command line on Mac
date: 2021-10-15

layout: layouts/post.njk
---

## The Terminal

The command line on a Mac can be found by running the **Terminal** App in /Applications/Utilities. Terminal allows us to run special commands on the computer that cannot be found in the graphical user interface. These commands are usually short words that may be followed by one or more parameters...bits of other information that the command needs to run. Commands in the Terminal always run in the current directory. One of the most important tasks you can learn with the command line is changing working directories.

Open the Terminal app by either browsing to it in the Finder, or type `cmd + space` and then enter `Terminal` in the Spotlight search box that should pop up.

## Changing directories

To change directories on a mac we first need to know where we currently are. Type:

```bash
pwd
```

in the Terminal app. You will probably see something like this: `/Users/username`. If you didn't see something similar to that then type:

```bash
cd ~
```

'cd' is the command (change directory), '~' (tilde) is a parameter that means 'location of my home directory'. That command then will take you to your home directory. If I wanted to see what folders and files were in my current directory I could type:

```bash
ls
```

Try that now.

Let's assume that the directory I need to get to is at `Documents/school-stuff/project1`. when you did the list command earlier you probably saw that the Documents folder is inside the directory we are currently in. In fact the full path to the directory I want is `/Users/username/Documents/school-stuff/project1`

To change directories in the Terminal we use the `cd` (change directory) command. If I want to enter the Documents directory (and I see it when I type `ls`) I simply type:

```bash
cd Documents
```

If I want to go back to where I was I can type:

```bash
cd ..
```

('..' is a shortcut for parent directory)

I can also change multiple directories at once. like so:

```bash
cd Documents/school-stuff/project1
```

One trick that can help you as you are navigating with the Terminal is the 'tab' key. 'tab' autocompletes what you are typing if it can. So if I started typing

```bash
cd Doc
```

then hit 'tab' it would autocomplete to:

```bash
cd Documents
```

Then I could keep typing:

```bash
cd Documents/scho
```

hit 'tab' again and it should autocomplete to:

```bash
cd Documents/school-stuff
```

If you hit 'tab' and nothing happens then it means the computer either can't find a match or there is more than one match. The command line is also case sensitive...meaning 'doc' is different than 'Doc'. Remember that 'ls' is your friend. It will always show you the contents of whatever directory you are in.

One last tip. Apple has actually put a bit of work on making the Terminal aware of what is going on in the Finder. Another way you can get to a specific folder in Terminal would be to type

```bash
cd
```

then drag the folder you want from the Finder window onto the Terminal window. In the case of this example if you have done correctly it should show something like this:

```bash
cd /Users/username/Documents/school-stuff/project1
```

The advantage of this is that it doesn't matter what directory you started in...it will always take you to the directory specified.

Here are a couple of additional resources to look over if you feel you need more help.

- [Treehouse: Intro to Mac command line](http://blog.teamtreehouse.com/introduction-to-the-mac-os-x-command-line)
- [Youtube: How to use Mac Terminal](https://www.youtube.com/watch?v=I65C4ZXK4ek)
