---
title: Setup Git and GitHub
description: Install Git on your computer and create an account with Github.
date: 2021-11-12

layout: layouts/post.njk
---

## Preparation

Make sure you read through the Prepare section for this topic.

## Using GitHub Pages to host our website

<div class="bigSteps">

1.  ## Install Git

    <figure class="video-container">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/c42Z2mlJyis" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </figure>

    Click on and Follow only the Windows, Mac, or Linux Instructions.

    <details>
    <summary>For Windows users:</summary>

    1. Before downloading, check to make sure you don't already have Git installed on your computer

       - Click on the 'Start' window icon on your computer in the bottom left of your screen.
       - Type 'cmd' to open the Command Prompt app. You should get the Command Prompt terminal to open. It doesn't matter what your prompt path is.
       - Type in `git --version` and hit enter.
         You should now either see a git version number come up or a message that says something about how 'git' is not recognized. If you have a version number come up, you already have git installed and you don't need to install it. If you get the message that git is not recognized then you need to install it.

    2. To install Git for Windows. Go to git-scm.com/downloads and click on 'Windows' under Downloads. An .exe file should be downloaded.

    3. Click that .exe file to open it and it will begin the process of installing Git.
    4. Allow it to make changes to your device.
    5. Click 'Next' through all of the setup windows leaving all the defaults as they are. There will be quite a few windows.
    6. The last window will let you click 'Install' and click 'Finish'.
    7. Open up a new Command Prompt window by closing the first Command Prompt window and start a new one by typing 'cmd' at the Windows start button in the bottom left of your screen again. At the prompt, type: `git --version` again if you want to see that it installed. You should now see the version number. (If you don't use a new Command Prompt window, you could get the same message you had before you installed Git.)
       While we are still in the Command Prompt we will type in two more commands to set up our username and email that will be used with our GitHub account. Use a professional username since this username will show up in the domain of your web projects. Again it doesn't matter what the path prompt is. These are global settings so you can type them from any path prompt.

    8. The command is listed below, but make sure you use your own username and email between the "" quotes. Use the username and your email you used for the GitHub account. It will be different for everyone. Type:

    ```bash
    git config --global user.name "yourusername"
    ```

    and then hit enter. Nothing will happen if you did it right. And then type:

    ```bash
      git config --global user.email "youremail@byui.edu"
    ```

    and then hit enter again.
    Now you have configured your Git to recognize your GitHub later.

    <figure class="video-container">

     <iframe width="560" height="315" src="https://www.youtube.com/embed/3KpzB3ZZCZ4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

    </figure>
    </details>
    <details>
    <summary>For Mac Users:</summary>

    1. Before downloading, check to make sure you don't already have Git installed on your computer

       - Click 'Search' icon (looks like an magnifying glass) on your near the top right of your screen.
       - Type in "terminal" and open the Terminal app.
       - Type in `git --version` at the prompt and hit enter.
         You should now either see a git version number come up, a message that says something about 'command not found', or a prompt asking you to install the command line developer tools. If you have a version number come up, you already have git installed and you don't need to install it. If you get the command line tools message click yes and install them then skip to step 12, if you get the message that the command is not found, then you need to install it. Continue below.

    2. To install Git for Mac. Go to git-scm.com/downloads and click on 'macOS' under Downloads. It will take you to a page with a few options.
    3. Click the 'installer' link under the Binary installer section next to the Tim Harper text. This will take you to a sourceforge.net page.
    4. Don't sign up for anything or click anything except the 'Download' button. This will start a download of a .dmg file. Double-click the file to open it.
    5. You will see a few files, double-click the .pkg file. You should get a message saying it is coming from 'an unidentified developer'. This is a great warning but we will trust this one. Click 'OK'
    6. To allow our system to install Git we will need to go to our System Preferences (gear icon or type System Preferences from our Search magnifying icon).
    7. From System Preferences click the 'Security & Privacy' icon.
    8. Now you should see the App listed under the 'Allow apps downloaded from:' section and you can click 'Open Anyway'.
    9. A similar window will pop up like before but you can now click 'Open'.
    10. You can now use all the defaults for the installation with 'Continue' on the first screen. Install on the next (it will have you enter your Mac password again), and click Close. It might ask if you want to send the file you downloaded to the Trash and you can keep it with 'Keep' or delete it with 'Move to Trash'. We shouldn't need it again.
    11. Open up the Terminal again. At the prompt, type: `git --version` again if you want to see that it installed. You should now see the version number. (If you don't use a new Terminal window, you could get the same message you had before you installed Git.)
        While we are still in Terminal we will type two more commands to set up our username and email that will be used with our GitHub account. Use a professional username since this username will show up in the domain of your web projects. Again it doesn't matter what the path prompt is. These are global settings so you can type them from any path prompt.

    12. The command is listed below, but make sure you use your own username and email between the "" quotes. Use the username and your email you will use or did use for the GitHub account. It will be different for everyone. Type:

    ```bash
    git config --global user.name "yourusername"
    ```

    and then hit enter. Nothing will happen if you did it right. And then type:

    ```bash
      git config --global user.email "youremail@byui.edu"
    ```

    and then hit enter again.
    Now you have configured your Git to recognize your GitHub later.

    </details>
    <details>
    <summary>For Linux Users:</summary>

    [Linux Git Install](https://github.com/git-guides/install-git#install-git-on-linux)
    Install Git with the link above and then follow the last few steps from the Windows or Mac instructions to set up your global config username and email settings to match your GitHub account.

    </details>

2.  ## Sign up for a GitHub Account

    1. Visit the [Github.com](https://github.com/) website and click the 'Sign Up' button.
    2. You'll enter an email. Use the email you use in the git config global settings. Then click 'Continue'.
    3. Create a password that has to be at least 15 characters or 8 characters with a number and lowercase letter. Then click 'Continue'.
    4. Enter a username, the same username you used when setting up your git config global settings. It should be a professional name since this username will show up in the domain of your web projects. You might show these links to future prospective employers. If you get a red 'X' to the left of your username, then someone else has already used that username and you need to choose a different one. Don't forget the email, password, and username you used for this new GitHub account. We will need them later.
    5. Enter 'n' for the next step unless you want email from them.
    6. At this point it wants to make sure you are human and it has you solve a few simple puzzles. Click 'Start puzzle' and follow the directions. Click 'Create account'.
    7. It will send a launch code to the email you listed. Use that launch code and enter it.

    The following video demonstrates the steps above.

    <figure class="video-container">
     <iframe width="560" height="315" src="https://www.youtube.com/embed/B0-WyDcOAls" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </figure>

</div>
