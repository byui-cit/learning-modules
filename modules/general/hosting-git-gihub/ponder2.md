---
title: Web Hosting with GitHub Pages.
description: Set up a way to host your web files on a server
date: 2021-11-12

layout: layouts/post.njk
---

## Preparation

Make sure you read through the Prepare section for this topic, have Git installed, and a GitHub account.

## Using GitHub Pages to host our website

<div class="bigSteps">

1. ## Create a GitHub repository

   1. Login to your GitHub account. Find the '+' sign in the upper right corner and click it and you should get a drop down menu. Choose 'New repository'.
   2. Enter a name for your Repository. The name should describe the project or course you are creating the repository for. (ie 'portfolio', or 'wdd130'). Use lowercase for the repository name.
   3. You can add a description if you want, but that is optional.
   4. Leave the the 'Public' clicked.
   5. Notice it will give us one main branch. We'll see that referenced later.
   6. Check the 'Add a README file' just so we don't have an empty repository to begin with.
   7. Click 'Create repository'
      It will take you to your repository and shows the one `README.md` file you have there. Later we will be coming back to this repository to use the green 'Code' button. So leave this tab open in your browser so we can come back to it later.

   <figure class="video-container">
   <iframe width="560" height="315" src="https://www.youtube.com/embed/kOYFDUYMt8w" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
   </figure>

2. ## Set up our project folder with Git and GitHub

   Our project folder will hold all our files and resources for our project and keep track of any changes we make. When we are ready, we can then transfer the local files to our remote GitHub account.

   Before you start, make sure you have [Git installed](../ponder1) and your git config username and email settings done.

   1. Open up Visual Studio Code, if it is not already open.
   2. Click on the View menu option and click on 'Command Palette'
   3. Type `git clone` into the input box that comes up. You should see a blue bar beneath that says 'Git: Clone'. If you don't see it, restart VSCode and try it again. It may not be recognizing that you've installed Git until it's restarted.
   4. Click the 'Git: Clone' blue bar. You will notice that your input box now says 'Provide repository URL or pick a repository source." We need the URL from our GitHub Account that we left open earlier in our browser.
   5. In the GitHub Account, there is the green button that says 'Code' we will copy the HTTPS URL from there and paste it back into that input box in VSCode.
   6. A window will open up that wants you to pick a location that your folder will be placed into. It will create a folder with the name of your repository (ie wdd130) in whatever location you want it to be in. Pick a location such as Documents or a class folder you might already have set up for this folder to be placed into.
   7. You will get a message saying 'Would you like to open the cloned repository, or add it to the current workspace?' You can click 'Open' there or, if you don't see the message or it disappears quickly, you can always open the folder with the File menu option and 'Add Folder to Workspace' and find the wdd130 folder that was just created and click 'Add'.
   8. You might be asked if you trust the authors of the files. Click 'Yes, I trust the authors'.
   9. If it asks about saving your workspace configuration as a file just click 'Cancel' or close that window out.
   10. Now in the Explorer panel on the left you should see the folder with the `README.md` file inside it. Click the `README.md` file and add a line of text to it and save the file with a Ctrl-S or Cmd-S and you will see your Source Control icon on the left will get a little blue circle with a number 1 inside it. This is Git, on your local computer, keeping track of the change you just made to the readme file. Git keeps track of any file inside the wdd130 folder and will create a number for each file changed or added to the folder. It has noticed that we changed the readme file.
   11. We want to now send that change we made to our remote GitHub server. So click the Source Control icon with the blue number 1. This will open the Source Control panel. You should see the `README.md` file with a few icons to the right of it.
   12. Click the + sign next to the `README.md` file. This adds it to the staging area ready to be committed to our local Git repository.
   13. Now commit the change to our local repository by adding a message to the 'Message' input box that describes what changes you've made. I might put something like 'Added text to the readme file'
   14. Click the check mark to the right of your repository name. This will actually commit the staged changes on your local computer.
   15. Now send those changes to the remote repository by clicking the 'More actions' ... (3 dots) which is two icons to the right of the check mark and choose 'Push' from the pop up menu. This will send your files to GitHub.
   16. The first time you push, and you look at your browser, it may have you authorize the Git Credential Manager. Just click the authorize button.
   17. In your GitHub account in the browser, check that the `README.md` file has changed with that new text added.

   <div class="callout">

   The following video does differ a bit from the steps this time. In this video, instead of creating an index.html, we will just be adding to our README.md file instead. Follow the written steps above closely and just watch (not following along) the video from 2:42 on to understand the Source Control process. But complete all the steps above to practice.

   <figure class="video-container">
   <iframe width="560" height="315" src="https://www.youtube.com/embed/SMunO3D0I0c" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
   </figure>
   </div>

3. ## Starting our Home Page and Setting up GitHub Pages

   Let's start a new index.html page (Home Page) inside our repository and then get that page to show up live on the Internet. We're almost there. Hang in there.

   1. In VSCode open the Explorer panel and add a file to the wdd130 folder called **index.html**.
   2. Open the file and start a new HTML document with an exclamation mark '!' and hit enter. This will start a new file for you.
   3. Change the default title text of 'Document' to something meaningful based on the purpose of the site, ie 'WDD 130 Home Page' or 'WDD 230 Home Page'
   4. **NOTE! If you are creating this specifically for WDD 130** then add the following code inside the body:

      ```html
      <h1>Welcome to WDD130 Web Projects</h1>
      <nav>
        <a href="wwr/index.html">White Water Rafting Website</a>
        <a href="wwr/site-plan-rafting.html">White Water Rafting Siteplan</a>
        <a href="#">Personal Website</a>
        <a href="#">Personal Siteplan</a>
      </nav>
      ```

   5. As you save this file you will notice another blue circle number show up on our Source Control icon. Our local Git noticed a new file in our repository.
   6. Click the + sign next to the index.html file.
   7. Now commit the change to our local repository by adding a message to the 'Message' input box that describes what changes we've made. Something like: 'Added the home page'.
   8. Click the check mark to the right of your repository name.
   9. Now send those changes to the remote repository by clicking the 'More actions' ... (3 dots) and choose 'Push' from the pop up menu. This will send the index.html to GitHub.
   10. When you go to your GitHub account you should now see the index.html file in the repository there.
   11. Let's see this page live on the Internet by setting up GitHub pages. Go back to the GitHub.com account. Click 'Settings' with the gear icon. In the submenu that appears to the left choose 'Pages'
   12. In the 'Source' section click the button that says 'None' and change it to the 'main' branch, leave the next one at 'root' and click 'Save'
   13. Above that a section opens that says 'Your site is ready to be published at ...' with the name of your URL that can be used by anyone to see your website. Woo Hoo! We did it.
   14. **Copy that URL** and paste it into the `README.md` file in your project. You will need to remember it. Do this in your editor. While GitHub will allow you to modify your files on GitHub.com, it is not recommended. Make all your edits to the repository files through your editor.
   15. Give it a few minutes for your home page to show up. You might need to refresh the page after a few minutes.

   The following video demonstrates the last few steps of GitHub Pages.

    <figure class="video-container">
   <iframe width="560" height="315" src="https://www.youtube.com/embed/auI1FqbZSfk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
   </figure>

</div>

See your instructor if you have any trouble.

We did it! That was a lot of set up but worth the price to have free hosting. And from here on out you just have to commit and push any changes you make in your new repo.
