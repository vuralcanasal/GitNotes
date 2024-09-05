# Git Stash (like a stack)
If you need to switch to another branch without commiting your work, and it causes a conflicted, you can use `git stash` or `git stash save`. Thanks to that, you do not have to make unnecessary commits.

`git stash pop` removes the recently stashed changes and re-apply them to your working area.You can apply them for same branch or different branch. After poping, changes are removed from stash-stack.

`git stash apply` helps you to apply changes withour removing changes from stash. Thanks to that, you can apply same changes to multiple branches.

__stash stack is firts in - first out__

`git stash list` lists all stahes.

`git stash apply stash@{<index number>}` applies the specific changes from stash.

`git stash drop stash@{<index number>}` deletes the specific changes from stash without appling.

`git stash clear` to delete all changes from shash.

