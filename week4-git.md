Starting Command
================

    cd my_folder1
    git init
    git clone folder1 my_folder1

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
