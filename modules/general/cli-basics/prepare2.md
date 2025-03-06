---
title: Command Line basics - Windows
description: Getting started with the command line on Windows
date: 2021-10-15

layout: layouts/post.njk
---

## The command line

The command line on a Windows PC can be found by running the `cmd` app. The easiest way to do that is Start->Run->cmd. Cmd allows us to run special commands on the computer that cannot be found in the graphical user interface. These commands are usually short words that may be followed by one or more parameters...bits of other information that the command needs to run. These commands in the always run in the current directory. One of the most important tasks you can learn with the command line is changing working directories.

Powershell is another command line interface app on Windows. You can also use Powershell for these tasks as well.

## Changing directories

To change directories on a pc we first need to know where we currently are. The prompt will always show you this. If you have just opened up the cmd window you will probably see something like this:

```bash
C:\Users\username
```

If you didn't see something similar to that then type:

```bash
cd %userprofile%
```

That will take you back to your home directory. If I wanted to see what folders and files were in my current directory I could type:

```bash
dir
```

Try that now.

Lets assume that the directory I have my activity files in is at \Documents\web-stuff\scss-demo. When you did the list command earlier you probably saw that the Documents folder is inside the directory we are currently in. In fact the full path to the directory I want is C:\Users\username\Documents\web-stuff\scss-demo

To change directories in the command prompt we use the 'cd' (change directory) command. If I want to enter the Documents directory (and I see it when I type 'dir') I simply type:

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
cd Documents\web-stuff\scss-demo
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
cd Documents/web
```

hit 'tab' again and it should autocomplete to:

```bash
cd Documents/web-stuff
```

If you hit 'tab' and nothing happens then it means the computer either can't find a match or there is more than one match. The command line is also case sensitive...meaning 'doc' is different than 'Doc'. Remember that 'dir' is your friend. It will always show you the contents of whatever directory you are in.

One last tip. Microsoft has actually put a bit of work on making the command prompt aware of what is going on in the Explorer. Another way you can get to a specific folder in the command prompt would be to type

```bash
cd
```

then drag the folder you want from the Finder window onto the Terminal window. In the case of this example if you have done correctly it should show something like this:

```bash
cd C:\Users\username\Documents\web-stuff\scss-demo
```

The advantage of this is that it doesn't matter what directory you started in...it will always take you to the directory specified.

Here are a couple of additional resources to look over if you feel you need more help.

- [How to use the Windows command line](http://www.computerhope.com/issues/chusedos.htm)
- [Youtube: Command prompt basics](https://www.youtube.com/watch?v=OHeJRYgdyik)
- <iframe id="kaltura_player" src="https://cdnapisec.kaltura.com/p/1157612/sp/115761200/embedIframeJs/uiconf_id/42438272/partner_id/1157612?iframeembed=true&playerId=kaltura_player&entry_id=1_i6k9x1zs&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=1_woaa00hv" width="608" height="402" allowfullscreen webkitallowfullscreen mozAllowFullScreen allow="autoplay *; fullscreen *; encrypted-media *" sandbox="allow-downloads allow-forms allow-same-origin allow-scripts allow-top-navigation allow-pointer-lock allow-popups allow-modals allow-orientation-lock allow-popups-to-escape-sandbox allow-presentation allow-top-navigation-by-user-activation" frameborder="0" title="cli_win"></iframe>
