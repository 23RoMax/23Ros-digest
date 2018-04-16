---
title: "A Second Day With Hugo"
date: 2018-04-09T00:43:36+02:00
draft: false
categories: ["hugo", "tutorials"]
tags: ["computer", "product", "software", "hugo", "development", "gohugo", "golang"]
description: Second steps with hugo - migrating to another OS
keywords: ["computer", "product", "software", "hugo", "development", "gohugo", "win10", "windows"]
---

## Second entry - first commit
After setting things up initially in a Mac environment and creating a new post, why not doing the same for windows?
--> Bad idead
### Still, I'm getting it and slowly things are coming together
Setting Hugo up on a windows machine is not utterly complex, but also not as fluent of an experience as on linux, or mac. One might wonder why I have to deal with three different environments at all? It's just a habit of mine, to have all the tools I use at hand on every possible machine in my possesion. Which also includes a i7 XMG Schenker Gaming machine (which I barely use for gaming, but which indeed has win10 for this exact purpose installed) on which I'm in fact writing this entry now. 

As in my former post about hugo and how I setup the environment for it, I will divide this into several sections like an tutorial.

**1st Step: Setting up a git repo**

This step can be skipped, but makes life easier for myself working on several different machines. However, even if you are the only person working on that blog, it is recommended to use a version/subversioning control 'insert wikipedia quote here:' 

>... for tracking changes in computer files and coordinating work on those files among multiple people.

![GIT merge conflict joke](/images/onlydev.jpg)

If you want to read up more on this subject, there is plenty of documentation available, but git is pretty much self explanatory and only gets complicated when using different branches with multiple developers etc.

As I already had a hugo project on my mac, I initiated a new git repo on the mac machine and pushed into the master of this repository. Later on, I pulled all the information from there onto my local windows machine to continue editing the same project state as I have left on my mac.

**2nd Step: Installing golang in Windows**

Navigate to [the golang website](https://golang.org/) and download the binary distribution package for windows. Installing go is just a matter of pressing continue as with most packages out there. Check the disclaimer. Be always aware of your surroundings, otherwise someone else will be aware of yours. After succesfully installing go, you might need to set your environmental variables to `C:\Go\bin` and the default path of the package will be `C:\Go`. Follow the steps of testing your installation [here](https://golang.org/doc/install).

**3rd Step: Installing chocolatey package manager**

The installation process of choclatey is very well documented and can be found [here](https://chocolatey.org/install). I haven't been aware of the fact that there is a package manager for windows like this - quite awesome!

**4th Step: Installing hugo with chocolatey**

Open the terminal and enter:
````choco install hugo -confirm````
this will let chocolatey install the hugo package onto your windows system.

Et voilà! Now you can use hugo on your windows machine.

**5th Step: Dealing with the git submodule**

When trying to run my `hugo server -D` command to checkout my hugo pages on the local server instance, I ran into some serious troubles. The theme was not properly initiated and pulled into the repo. Therefore I had to readd the submodule. But this time, I edited it straight away and added a froked version of the theme as submodule, so that I can easily commit my changes made to my fork and thus never need to worry about it anymore, but can easily merge the updates from the master of the original project and fix potential conflicts.

**6th Step: Debugging my windows local hugo server**

Also `hugo server` leaves me with a blank page on localhost:1313 - I do not know yet why and need to investigate this issue further. So far I have figured out, that 127.0.0.1:1313 works. This is also the reason, why I mentioned that setting things up on windows was a bad idea: I spent easily two hours looking for the issue of getting blank pages on localhost:1313 even though the static projects are created just fine. 

![Fuck you win10](/images/stick_fuckyou.png)

I blame it on windows.