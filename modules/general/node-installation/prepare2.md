---
title: Node NVM Installation - Windows
description: Installing Node JS with the NVM utility on a Mac
date: 2021-10-15

layout: layouts/post.njk
---


>Always use "Run as Administrator" when star5ng the Command Prompt (terminal) in Windows!

## 01 – Check if Node is already installed

1. Open Command Prompt (a.k.a. terminal) as an administrator.
2. Type `node -v` OR `node -- version`, press Enter.
3. If a value is returned, e.g. v18.8.0, then node is already installed.
4. If node is present, move to step 01a.
5. If not, move to step 02.

### 01a – If node is installed, clear the node cache

1. The node cache must be cleared before uninstalling node.
2. In the terminal, type `npm cache clear --force`, press Enter.
3. You will receive a warning using –force, it is okay.
4. This may happen quickly or take a minute, be pa5ent.
5. Check to make sure it has been cleared.
6. Type `npm cache verify`, press Enter.
7. You should see a report indica5ng the cache is 0 bytes and has 0 index entries.

### 01b – When node cache is empty, uninstall node

1. In the windows search tool, type "uninstall", press Enter.
2. Using the system tool, locate "Nodejs" in the applica5ons list, single click to select it, then click
"Uninstall".
3. Wait for the uninstall process to conclude.

### 01c – Confirm the uninstall

1. Return to terminal, as an administrator, and type "where node", press Enter.
2. The message "Could not find files..." should be returned.

## 02 – Installing Node Version Manager Windows (e.g. NVM Windows)

1. Go to https://github.com/coreybutler/nvm-windows/releases
2. Scroll down and find the nvm-setup.exe link and click it.
3. Once the download is complete, double-click to start the installation.
4. During installation, accept all default options.

### 02a – Confirm Installation

1. Open the terminal, if closed, as administrator.
2. Type `nvm`, press Enter.
3. A message like "Running version 1.1.12" should appear.

## 03 – Install the Long Term Support (LTS) version of NodeJS

1. In the terminal, type `nvm install --lts`, press Enter.
2. A message should appear indica5ng the version number of node being downloaded.
3. When done a message will appear indica5ng the npm (Node Package Manager) version
number that was installed as part of the node installa5on (e.g. npm v8.19.3 installed successfully).

## 04 – Use the LTS version of Node

1. In the terminal type "nvm use version number" (e.g. `nvm use 20.11.0`), press Enter.

## 05 – Installing and using a different Node version

With NVM Windows installed, if you need to download and use a different version of Nodejs, do the following:

1. Open the terminal as an administrator.
2. Type "nvm install version number" (e.g. nvm install 14.4.2), press Enter.
3. When the installa5on is done, type "nvm use version number" (e.g. nvm use 14.4.2), press Enter.

## 06 - List Node Versions Installed on your computer

1. Open the terminal as an administrator.
2. Type `nvm ls`, press Enter.
3. A list of all installed versions of Node, that NVM is tracking, appears.
4. To see the current version of Node, type `node -v`, press Enter.

## 07 - Switch Node Versions

If you find yourself needing different Node versions for different projects, just switch afer opening the project.

1. In VS Code, or any tool, open the project.
2. Open the terminal and type, "nvm use version number" (appropriate to your required node version), press "Enter".
3. You should now be switched to that version of Node.
