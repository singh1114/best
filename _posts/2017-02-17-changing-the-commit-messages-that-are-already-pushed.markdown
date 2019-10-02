---
title: Changing the commit messages that are already pushed
date: 2017-02-17 09:45:33 Z
categories:
- Git
author: ranvirsingh1114
comments: true
layout: post
link: https://ranvirsinghprojects.wordpress.com/2017/02/17/changing-the-commit-messages-that-are-already-pushed/
wordpress_id: 633
---

So in this post, we will be talking about the process of changing the commit messages that are already pushed into the remote. But, before talking about changing those messages we must know about the basics commands of GitHub. Please refer to [this post](https://ranvirsinghprojects.wordpress.com/2016/06/10/basic-commands-in-github/), if you have less knowledge about the Git.

Also, it is good to know about the git reset command which is used to reset any changes made by a user in a repo. Use the command git reset --help for more information.

Now let's dive right into the topic. First thing is to check the changes that you have done in the recent past. For that use the following command.

    
    <code>$ git log 
    
    # This command will show one change in each line
    # -5 represent the number of messages that you want to read.
    $ git log --oneline -5</code>


Now for changing the commit messages use the amend command. The command is written below.

But before that think that you don't want to change the last commit message but you want to change a commit message that is somewhat old. Say it is shown at number 5 when you used git log. Use this command to change your head to that commit message.

    
    $ git rebase -i HEAD~5


Next step was hard to figure out but I found it by some proper reading. Now this will open a panel for you where you can make changes for you commit messages. This panel will look something like this.

    
    pick 2f8e279 another message
    pick a04482b One more another message 2
    pick 97d5145 no new changes available
    
    # Rebase 3bb9b41..a1c796c onto 3bb9b41 (3 command(s))
    #
    # Commands:
    # p, pick = use commit
    # r, reword = use commit, but edit the commit message
    # e, edit = use commit, but stop for amending
    # s, squash = use commit, but meld into previous commit
    # f, fixup = like "squash", but discard this commit's log message
    # x, exec = run command (the rest of the line) using shell
    # d, drop = remove commit
    #
    ...few other lines


Now if you look at the comments properly you will come to know about how to do this. So as you can see that in the first three lines commit messages are written. In the beginning of each line "pick" is written and in the comments, we can see the description. So,  remove the word pick and change it to the word that you want to use for yourself. I removed pick in all the three lines and changes it with r.

I am not using "e" as it was not required in my case. So, if anyone out there uses it, share it in the comments.

After that, you will be asked to change the commit message one by one in the end.

Now say you only want to change a single commit message (last commit message) it is a bad choice to use something like rebase. You can use this command rather.

    
    $ git commit --amend


This command will open the editor in the terminal. Make the changes and save it. Now is the time to push the changes to the remote. Use the following command. Keep in mind to include that + sign, otherwise, your changes will be ignored.

    
     $ git push origin +branch_name


Thanks for reading this post. Keep reading and Happy coding.
