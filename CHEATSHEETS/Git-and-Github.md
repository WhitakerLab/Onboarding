# Git and GitHub cheat sheet

This file contains top tips for using git and GitHub.
Anyone is welcome to submit a PR to it whenever they find themselves googling for an answer more than once!

The file was created on 17 March 2019 inspired by [Yo Yehudi's](http://github.com/yochannah) [tweet](https://twitter.com/yoyehudi/status/1106543147415412736) about renaming remotes and branches.

### Table of contents

* [Renaming remotes and branches](#renaming-remotes-and-branches)
* [Reset local repository branch to be just like remote repository](#reset-local-repository-branch-to-be-just-like-remote-repository)

### Renaming remotes and branches

*Taken from [Yo Yehudi's](http://github.com/yochannah) [tweet](https://twitter.com/yoyehudi/status/1106543147415412736) and [this blog post](https://multiplestates.wordpress.com/2015/02/05/rename-a-local-and-remote-branch-in-git/) by [Multiple States](https://multiplestates.co.uk).*

Yo says:

> Need to rename your git remote?
> Maybe you accidentally set your upstream to origin, which I do often enough I know how to fix it...

Run: `git remote rename oldRemoteName newRemoteName`

Confusingly, to change branch names it is a different syntax.

Use: `git branch -m oldName NewName` where `-m` is for move.

If you're on the branch itself then use `git branch -m NewName`.

Changing branch names is useful if you - as Kirstie often does - put the date in the branch and then don't actually do the work until 2 weeks later! 🤦‍♀️

Once you've renamed the local branch you need to rename it on the remote:

The command `git push origin :OldName NewName` will delete the old branch and push the new one.

Then switch to the new branch (if you aren't already on it) and `git push origin -u NewName` so that this branch tracks the remote one.

### Reset local repository branch to be just like remote repository

*Taken from this [StackOverflow question](https://stackoverflow.com/questions/1628088/reset-local-repository-branch-to-be-just-like-remote-repository-head) and two of the fantastic answers (the accepted answer with [5169 up votes](https://stackoverflow.com/a/1628334) & the one just below with [299 up votes](https://stackoverflow.com/a/27664932)).
Thank you!* :heart_eyes:

Sometimes you just want to get rid of all the local changes and reset a branch to be exactly the same as the one on GitHub (the remote).

This is particularly useful if you have a few different branches going on in your local repository and you don't want to "contaminate" a simple change with the changes in the other branches.

The answer given to the StackOverflow To reset to the same as the `master` branch at your `origin` remote location.

```
git fetch origin
git reset --hard origin/master
```

If you need to remove *untracked files* then you'll need to also run: `git clean -f`.
We recommend running `git clean -n -f` before you do to double check what *will* be deleted without removing the files....just in case!
