---
title: "A New Day With Hugo"
date: 2018-04-06T23:23:04+02:00
draft: false
categories: ["hugo", "tutorials"]
tags: ["computer", "product", "software", "hugo", "development", "gohugo", "golang"]
description: First steps with Hugo - not a Hello World, but a Hello Universe
keywords: ["computer", "product", "software", "hugo", "development", "gohugo", "macos"]
---

# Initial Entry - no commit

Just doing the setup like described in the quickstart.

## I'm trying to figure out what I'm doing here

So setting up hugo was a smooth experience on my macbook.

**1st Step:**

Installing the depencie via
`brew install hugo`

**2nd Step:**

Installing the desired them as a submodule via `git add submodule <ADD_URI_TO_DESIRED_THEME_GIT> <PATH_IF_NECESSARY>;`

**3rd Step:**

Adding a first post via `hugo new posts/a-new-day-with-hugo.md`

Et voilà and here we are. Now I was able to write my first blogpost in writedown.

**4th Step:**

Having a look with `hugo server -D`. The param -D is used to let Hugo know, that it needs to compile the *.md file with draft set to true.

**5th Step:**

Enjoy!