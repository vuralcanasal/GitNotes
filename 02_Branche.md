# What is Branch?
Branches are pointers to specific snapshots of your changes. You can work on multiple things simultaneously without affecting the main project until you merge your changes back in. In basic words, branches are alternative timelines for projects.

## Master and Main Branch
The default branch name is "master". It is not a special branch. It is like any other branch. For example, GitHub renamed the default branch from "master" to "main", but the default Git branch name is "master".

## HEAD
Head is a pointer refering to current location in your repository. There can be multiple branchs and commits in a project, and head shows you where you are.

# Git Branch
`git branch` to view your existing branches.
`git branch <new branch name>` to create new branch. You are still on the current branch after this.
`git switch <branch name>` to switch to a branch. Also, you can create a new branch and switch to it by `git switch -c <new branch name>`.
`git checkout <branch name>` to switch to a branch, so it is older version of switch. Both work.

__If you switch to another branch without committed your work, you can lost your work. Always commit your work before switching branches to avoid losing changes.__

`git branch -d <branch name>` to delete a branch. You can not delete the branch you are currently on. Switch to another branch first. If the branch you want to delete is not fully merged, you should force to delete the branch by `git branch -D <branch name>`.

`git branch -m <branch rename>` to rename a branch. Actully, you move the branch to new name. You need to be on the branch you want to rename.

# Git Merge
You can work on different features for your project in parallel thanks to branches. When you need to combine these features, `git merge` will help you. You always merge to the current HEAD branch. It means that you need to switch to master branch if you want to merge any branch into the master branch. In sortly, you switch to the branch you want to merge into, and type `git merge <the branch you want to merge>`.


Merge conflicts:

Here is the output example of a merge conflic example:

`git merge <branch name>` command and the output:
> git merge merge
> Auto-merging 02_Branche.md
> CONFLICT (content): Merge conflict in 02_Branche.md
> Automatic merge failed; fix conflicts and then commit the result.

File you need to fix:
> <<<<<
> >>>>>>> merge

You need to resolve it manually. Decide which content you want to keep in each conflict, edit and save the file.

Why there is a conflicted:
* Somebody modified a file, and somebody deleted the same file.
* Somebody edit some lines of some files, and somebody edit same lines of the the same files or one of the same files.

