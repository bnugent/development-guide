---
permalink: /code-collaboration/
title: Collaborating on Code
---

**WORK IN PROGRESS**
Initial content borrowed from:
https://github.com/thoughtbot/guides/blob/master/protocol/git/README.md

Collaborating on Code
=====================

A guide for programming within version control.

Maintain a Repo on GitHub
-------------------------

* Make all new repos public by default unless there's a compelling reason not
  to.
* Avoid including files in source control that are specific to your
  development machine or process.
* Delete local and remote feature branches after merging.
* Perform work in a feature branch.
* Rebase frequently to incorporate upstream changes.
* Use a [pull request] for code reviews.

[pull request]: https://help.github.com/articles/using-pull-requests/

Write a Feature
---------------

Create a local feature branch based off master or your main development branch.

    git checkout master
    git pull
    git checkout -b <branch-name>

Rebase frequently to incorporate upstream changes.

    git fetch origin
    git rebase origin/master

Resolve conflicts. When feature is complete and tests pass, stage the changes.

    git add --all

When you've staged the changes, commit them.

    git status
    git commit --verbose

Write a [good commit message]. Example format:

    Present-tense summary under 50 characters

    * More information about commit (under 72 characters).
    * More information about commit (under 72 characters).

    http://project.management-system.com/ticket/123

If you've created more than one commit, use a rebase to squash them into
cohesive commits with good messages:

    git rebase -i origin/master

Share your branch.

    git push origin <branch-name>

Submit a [GitHub pull request].

Ask for a code review in the project's chat room and add a "ready to review"
label on the PR in GitHub to make it easy to see all PRs that are ready
to be reviewed.

[good commit message]: http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
[GitHub pull request]: https://help.github.com/articles/using-pull-requests/

Review Code
-----------

A team member other than the author reviews the pull request. They follow
[Code Review guidelines](https://pages.18f.gov/development-guide/code-review/)
to avoid miscommunication.

They make comments and ask questions directly on lines of code in the GitHub
web interface or in the project's chat room.

If comments need to be addressed, the pull request author makes changes and
lets the reviewer know it's ready to be reviewed again.

Repeat until all comments have been addressed. The reviewer then merges the PR
and deletes the branch.

[Code Review guideline]: {{ site.baseurl }}/code-review/
Merge
-----

Rebase interactively. Squash commits like "Fix whitespace" into one or a
small number of valuable commit(s). Edit commit messages to reveal intent. Run
tests.

    git fetch origin
    git rebase -i origin/master

Force push your branch. This allows GitHub to automatically close your pull
request and mark it as merged when your commit(s) are pushed to master. It also
 makes it possible to [find the pull request] that brought in your changes.

    git push --force origin <branch-name>

View a list of new commits. View changed files. Merge branch into master.

    git log origin/master..<branch-name>
    git diff --stat origin/master
    git checkout master
    git merge <branch-name> --ff-only
    git push

Delete your remote feature branch.

    git push origin --delete <branch-name>

Delete your local feature branch.

    git branch --delete <branch-name>

[find the pull request]: http://stackoverflow.com/a/17819027