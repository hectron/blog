---
layout:     post
title:      Rewriting Git history for fun and profit
date:       2015-02-22 12:00:00
summary:    If you are paranoid like me, you make a lot of commits. Sometimes, you need to arrange changes in logical segments.
---

## TL; DR

You can appear like a competent programmer by rewriting your commit
history with the following commands:

`git reset HEAD~n` where n is the number of prior commits.

`git add --patch` to select the changes you want to include in a commit.

----------

If you are like me, then you are likely to make a lot of Git commits.
Your commits might address spacing issues in code, or renaming variables
only to rename them back. You might be forced to fix a bug in the
process of working on your feature.

If you find a lot of unrelated data in a commit, you might want to
consider rewriting your commit history. This good shows you how to
rewrite history assuming that your changes are the latest changes in the
branch.

**NOTE**: I oppose rewriting history on your **master** branch. This is
considered bad practice and is discouraged.

## Developing a plan

When you are going to rewrite your Git commit history, you need to
identify what the purpose of the rewrite is. Are you trying to group all
your changes to a test suite? Are you creating new database migrations?
Are you working on two different components that are unrelated?
_Identify what you want to accomplish_.

For the purpose of this tutorial, we will suppose that I grouped a
commit where I modified an HTML page, along with tweak it's CSS and
added some javascript functions. My desired goal is to group all the
changes I made to the HTML markup in one commit, group all the CSS
changes in another commit and group all the Javascript changes in their
own commit.

Here is what my original commit looked like:

    commit 23106d0d38bd5a774d61f4632839d6fb61f20c66 Author: Hector Rios
    <my@email.com> Date:   Fri Feb 13 15:26:22 2015 -0600

        Updated my Contact page.

## Breaking (the) bad

The first step you need to do is rollback the changes in that commit so
that we can split them up into individual commits. To do this, do the
following:

`git reset HEAD^`

This will go back one commit and unstage your commit's changes. So now,
you want to run the command `git add --patch`. This will bring an
interactive prompt in which you can select whether or not to stage that
change. In our case, we want to include only the changes we made to the
`*.html` file.

Once we selected all the changes, we commit that change, and move on to
the next file. When we do this to our stylesheets and javascript files,
we will now have three commits.

Pretty nifty right? How about if we wanted to group by feature? Let's do
that instead now.

## Undoing our changes and grouping by feature

Since we now have three commits of our theoretical HTML/CSS/JS pages, we
need to undo all three commits. I personally squash the commits and then
repeat the trick above. So the commands look like:

    git rebase -i HEAD~3 (Then squash them into one commit) 
    git reset HEAD^ 
    git add --patch (select the chunks that relate to your feature)

This way you can combine the changes per feature and commit them
individually.

## Final notes

The idea is that you combine your commits into one, then undo the
changes so that they are all unstaged. You then strategically stage them
and commit them. This way, your git history is logical.

