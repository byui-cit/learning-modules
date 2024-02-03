---
title: Node NVM Installation - Mac
description: Installing Node JS with the NVM utility on a Mac
date: 2021-10-15

layout: layouts/post.njk
---

## 01 Prerequisite - Install XCode tools

> Starting with MacOS 10.9, XCode command line tools must be installed, prior to installing NVM.

### 1a XCode Developer tools only

**Recommended for most!** If you don't want to download and install the full XCode, you can install just the developer tools (much smaller than the full install) by doing the following:

1. Open Spotlight with Command + spacebar.
2. Type "Terminal", press Enter.
3. Type `xcode-select -p`, press Enter. If this returns something like `/Library/Developer/CommandLineTools` then you already have the tools and you can move to step 02
4. Otherwise type `xcode-select --install`, press Enter and follow the prompts.

### 1b XCode Full Install (optional)

If you think you will ever want to build native MacOs or IOS apps download and install XCode. Apple’s XCode development software is used to build Mac and iOS apps, but it also includes the tools you need to compile software for use on your Mac. XCode is free and you can find it in the  [Apple App Store](https://apps.apple.com/us/app/xcode/id497799835?mt=12) but it is quite large (Over 3.5G!)  After you install it, open it at least once to accept the Terms.  Step 02 will not work, after doing the full Xcode install, unless you have accepted the terms.


## 02 - NVM GitHub Installation

1. Go to [https://github.com/nvm-sh/nvm](https://github.com/nvm-sh/nvm).
2. Scroll down to the "Installing and Updating" heading.
3. Locate the curl Install and update script and click the copy icon on the right. (Should look something like this: `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash`)
4. Open the terminal (Command + spacebar, type "terminal", press Enter).
5. Paste the script into the terminal, press Enter.
6. Expect the installation process to take ~ 15 seconds, depending on your Internet
connection.
7. When the process is complete, close and reopen the terminal.
8. Type `nvm -V`, press Enter. A long list of nvm commands will appear. This means nvm is installed and ready to be used.
9. If an error appears, return to the github location and scroll down to the
"Troubleshooting on macOS" section and see if you can identify your error and how to deal with it.

## 03 – Install the Long Term Support (LTS) version of NodeJS

1. In the terminal, type `nvm install --lts`, press Enter.
2. A message should appear indicating the version number of node being downloaded.
3. When done, a message will appear like "Now using node v20.11.0 (npm v10.2.4)".

## 04 – Installing and using a different Node version

If you need to download and use a different version of Nodejs, do the following:

1. Open the terminal.
2. Type "nvm install version number" (e.g. `nvm install 19`), press Enter.
3. When done, you will see a message like "Now using node v19.9.0 (npm v9.6.3)".

### 04a – List all versions of Node that are available to install

1. Open the terminal.
2. Type `nvm ls-remote`, press Enter.
3. The list will appear.
4. Repeat the installation steps, using the version number as needed.

## 05 - List Node Versions Installed on your computer

1. Open the terminal as an administrator.
2. Type `nvm ls`, press Enter.
3. A list of all installed versions of Node, that NVM is tracking, appears.
4. To see the current version of Node, type `node -v`, press Enter.

## 06 - Switch Node Versions

If needing a different Node version for another project, just switch after opening the project.

1. In VS Code, or any tool, open the project.
2. Open a terminal and type, "nvm use version number" (appropriate to your required
node version), press "Enter".
3. You should now be switched to that version of Node.
