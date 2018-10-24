Install Git for Windows
=======================

Find the executable at https://git-scm.com/download/win

Starting Command
================

Starting a new git project:

    mkdir my_folder
    cd my_folder
    git init

Pulling existing git  project from the web:

    git clone https://github.com/robinchew/workshop_notes.git

Common Commands
===============

- git log (You can use gitk alternatively)
- git log (gitk and stuff)
- git status
- git diff

- git add file.py
- git commit -m "First Commit"
- git commit -a -m "Add and commit"

Less Common Commands
====================

Git reset 2 commits back without losing data:

    git reset HEAD^^

Git reset 5 commits back without losing data:

    git reset HEAD~5

Pulling other people's code
===========================

git pull (but only works if you have run `git clone` or used `git remote add`)
