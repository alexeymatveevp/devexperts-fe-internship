---
---
Assuming you're already familiar with the project and want to contribute code changes - how to do that? 👀

Standard process:
1. create a new development branch from JIRA
2. commit code changes to this branch and push
3. create PR from JIRA
4. monitor PR for comments, merge check and tasks
5. (optional) write changelogs and update docs

## Create new branch
Go to your ticket in JIRA and click "Create branch" button

![[create branch.png]]
Now select branch from which you want to fork (it depends on your project)

![[Pasted image 20220824224155.png]]
> Default branch name is OK, but if it's too long - cut the tail

### Affected version and Fix version
**Affected version** - the version in which the bug was found  
**Fix version** - the target branch / version into which the fix / feature should be pushed

![[Pasted image 20220824224909.png]]

So when creating a dev. branch - look into fix version to understand what branch to fork ☝

## Commit and push
Make sure everything is correct, there are no `console.log`'s or `//commented code`, check that the project is compiling, eslint and code formatting rules are ok

### Commit message
Copy-paste the **whole row from JIRA ticket** as *commit message*

![[Pasted image 20220824225606.png]]

This is important for our [[Release Process]] and for stash to have links to JIRA tickets.

You may also add something else to commit message - no problem, like this
```
[DXCF-3515] Yellow accessibility borders // also fixed the checkbox styles
```

## Create Pull Request (PR)
PR's are created from JIRA as well. Because we've created branch from JIRA - it remembers the original branch - very convenient 🌻

![[Pasted image 20220824230312.png]]

Then on the PR screen:
- write small **description** - help reviewers maybe pointint out specific places / describe your changes
- add **reviewers** - our policy is "*at least 1 reviewer*", but you may add more

![[Pasted image 20220824230217.png]]

Ok now your PR is created 👍  
You can also notify reviewers in *DM* in slack if you want quick feedback.

## Monitor your PR
Reviewers will eventually review the PR and eiter accept it or leave comments / tasks.

PR won't merge until **all conditions** are met:
1. at least 1 reviewer accepted PR
2. merge check successful
3. all tasks are completed

![[Pasted image 20220825083632.png]]

## PR's assigned on you
Other developers may also assign you as reviewer

How to review:
1. click the JIRA ticket link (better with mouse wheel) - read about the reason of changes
2. click the "*Diff*" tab - read the code
	- make *shallow* review - comments, console.log's
	- deep review - try to find bad code practices, find logical errors 
	- checkout branch localy - test on your computer
	- merge checks usually checks the `eslint` and other routine checks for you 
3. write comments or create tasks - task is a good instrument when the change requires no discussion (just need to be done)
> unfinished tasks will prevent PR from merging
4. when ready - click Accept or Needs Work buttons at the top-right ⚠✔

![[Pasted image 20220825085041.png]]

## Changelogs and docs
Some projects do have changelogs and solid documentation

Always a good idea is to keep the docs up to date - so please consider doing it (ask your [[Team Lead]] about the culture here) 🙏


