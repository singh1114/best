---
layout: post
title: Basic git commands that you need to know as a Software Engineer
date: 2016-06-09T20:31:50.000Z
published: true
tags:
  - git
  - github
  - version-control
categories:
  - git
  - github
  - version-control
---
Git is the open source distributed version control system that facilitates GitHub activities on your laptop or desktop. The commonly used Git command line instructions are:-

## Create Repositories: Basic git initialization commands

**Start a new repository or obtain from an existing URL**

`$ git init [ project-name ]`

Creates a new local repository with the specified name

`$ git clone [ url ]`

Downloads a project and its entire version history

## Make Changes

**Review edits and craft a commit transaction.**

`$ git status`

Lists all new or modified files to be committed

`$ git diff`

Shows file differences not yet staged

`$ git add [ file ]`

to add all the files

`$ git add .`

Snapshots the file in preparation for versioning

`$ git commit -m "[descriptive message]"`

To add all files and commit them together

`$ git commit -am "[descriptive message]"`

Records file snapshots permanently in version history

## Group Changes

**Name a series of commits and combine completed efforts.**

`$ git branch`

Lists all local branches in the current repository

`$ git branch [ branch-name ]`

Creates a new branch

`$ git checkout [ branch-name ]`

Switches to the specified branch and updates the working directory

`$ git branch -d [ branch-name ]`

Deletes the specified branch

## Synchronize Changes

**Register a repository bookmark and exchange version history.**

`$ git fetch [ bookmark/ branch ]`

Downloads all history from the repository `bookmark/branch`

`$ git merge [bookmark /[branch]]`

Combines bookmarks branch into current local branch

`$ git push [alias [branch]]`

Uploads all local branch commits to GitHub

`$ git pull`

Downloads bookmark history and incorporate changes

## Some advanced git commands

Now let's talk about some of the advanced commands. So lately I have been working on some of the open source projects. Which gave me a lot of idea about the way the things happen in the open source industry. As much time you spend in this part, more will you learn about the things happening.

From a long time, I was working on a single user project where all the development is done by the single user. So your code remains intact and no damage is done to your commits. But the case is totally different when it comes to the big projects. There are constant commits that are happening in each second. So by the time you are ready to push the code to a repository for merging you are behind the main repository by at least three to four commits.

So the idea is to get the code from the main branch merge the commits into your code and then push the changes back into the main repository. Also in the case big repository you can't give the excuses like that you are new to the GitHub. If you don't evolve early, get ready to be ignored by the open-source industry.

## Stash commands

So whenever you want to commit a change that someone have done to the remote repository and you want to merge them to your local, put the changes into the stash by using these commands and then pull the latest remote.

```bash   
$ git stash 

# read more about git stash by using the following command
$ git stash --help

# The following command will list the saved data in the stash
$ git stash list
```

Stash is the part where you can store the things in the temporary mode they can be brought back to their earlier position when other changes are committed. It is the time to fetch the data that had been changed the main repository.

But before fetching it is great to make a remote of the forked repository so that we can directly fetch the changes from the terminal else we have to type the link of the forked repository again and again. Obviously, it is not necessary but it will make our work easier.

    
`$ git remote add upstream http://github.com/remote_link_to_the_repository`

The command tells us to add a new remote to the local repository by the name of upstream which is linked to the link provided as the next parameter. Now, whenever we want to know about the changes made in the particular branch we can simply type the name of the branch and we will get the code given by it. Then finally we will use the merge command to merge the code into the local repository. See the example code snippets for more information.

```bash 
$ git fetch upstream/branch_name
    
$ git merge upstream
```

Finally, you directly pull the code from the upstream using the following command.

`$ git pull --rebase origin [ branch_name ]`

Once all the changes are done, you can reapply the top stash.

```bash
$ git stash pop
# Apply the stash and delete the stash from stash list

$ git stash apply
# Apply the stash but keep in the history

$ git stash apply stash@{0}
# Apply the particular stash, can be found using the list command
```

Rest of the information will be shared in the follow-ups.
