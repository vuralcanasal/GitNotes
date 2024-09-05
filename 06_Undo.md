# Undo
You can use `git checkout` to create new branches, switch to another branch, restore files, and undo history.

`git checkout commit <commith-hash>` to view a previous commit.

> __DETACHED HEAD__
>
> You are in "detached HEAD" state. You can look around, make experimental changes and commit them, and you can discard any commiys you make in this state without impacting any branches by switching back to a branch.

This means HEAD points at that commit not at the branch.
1- You can stay detached HEAD to view old commits.
2- Re-attach the HEAD.
3- Create a new branch and switch to it.

To re-attach the HEAD `git switch <branch name>`

To create a new branch `git switch -c <new branch name>`

`git checkout HEAD~n` to view the commit HEAD - n (before n commit)

`git checkout HEAD~n <file name>` to revert a file n step back to its last commit. To discard changes.

`git restore --source HEAD~n <file name>` to revert a file n step back to its last commit. To discard changes.

`git restore --staged <file name>` to move a staged file as unstaged file.

`git reset <commit hash>` to reset the repo back to a specific commit. The commits are gone, you still have changes. If you have mistakes about your commit (wrong branch, wrong message, etc.), you can use reset.

`git reset --hard <commit hash>` delete last commits and changes.

`git revert <commit hash>` it is same with reset, but revert create a new comment with the changes.

