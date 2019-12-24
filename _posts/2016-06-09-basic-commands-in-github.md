---
title: Basic commands in GitHub
date: 2016-06-09 20:31:50 Z
categories:
- Git
author: ranvirsingh1114
comments: true
layout: post
link: https://ranvirsinghprojects.wordpress.com/2016/06/10/basic-commands-in-github/
wordpress_id: 109
---

Git is the open source distributed version control system that facilitates GitHub activities on your laptop or desktop. The
commonly used Git command line instructions are:-

Create Repositories
Start a new repository or obtain from an existing URL
$ git init [ project-name ]
Creates a new local repository with the specified name
$ git clone [url ]
Downloads a project and its entire version history

Make Changes
Review edits and craft a commit transaction
$ git status
Lists all new or modified files to be committed
$ git diff
Shows file differences not yet staged
$ git add [file ]
Snapshots the file in preparation for versioning
$ git commit -m "[descriptive message "]
Records file snapshots permanently in version history

Group Changes
Name a series of commits and combine completed efforts
$ git branch
Lists all local branches in the current repository
$ git branch [branch-name ]
Creates a new branch
$ git checkout [branch-name ]
Switches to the specified branch and updates the working directory
$ git branch -d [branch-name ]
Deletes the specified branch

Synchronize Changes
Register a repository bookmark and exchange version history
$ git fetch [bookmark ]
Downloads all history from the repository bookmark
$ git merge [bookmark /[branch]]
Combines bookmarks branch into current local branch
$ git push [alias [branch]]
Uploads all local branch commits to GitHub
$ git pull
Downloads bookmark history and incorporate changes

**Some advanced commands**

Now let's talk about some of the advanced commands. So lately I have been working on many of the open source projects. Which gave me a lot of idea about the way the things happen in the open source industry. As much time you spend in this part, more will you learn about the things happening.

From a long time, I was working on a single user project where all the development is done by the single user. So your code remains intact and no damage is done to your commits. But the case is totally different when it comes to the big projects. There are constant commits that are happening in each second. So by the time you are ready to push the code to a repository for merging you are behind the main repository by at least three to four commits.

So the idea is to get the code from the main branch merge the commits into your code and then push the changes back into the main repository. Also in the case big repository you can't give the excuses like that you are new to the GitHub. If you don't evolve early, get ready to be ignored by the open-source industry.

So whenever you want to commit a change that you have done to the repository put the changes into the stash by using these commands.

    
    $ git stash 
    # read more about git stash by using the following command
    $ git stash --help
    # The following command will list the saved data in the stash
    $ git stash --list


stash is the part where you can store the things in the temporary mode they can be brought back to their earlier position when other changes are committed. It is the time to fetch the data that had been changed the main repository.

But before fetching it is great to make a remote of the forked repository so that we can directly fetch the changes from the terminal else we have to type the link of the forked repository again and again. Obviously, it is not necessary but it will make our work easier.

    
    $ git remote add upstream http://github.com/remote_link_to_the_repository


The command tells us to add a new remote to the local repository by the name of upstream which is linked to the link provided as the next parameter. Now, whenever we want to know about the changes made in the particular branch we can simply type the name of the branch and we will get the code given by it. Then finally we will use the merge command to merge the code into the local repository. See the example code snippets for more information.

    
    $ git fetch upstream/branch_name
    
    $ git merge upstream


Rest of the information will be shared in the follow-ups.
