# GitHub
GitHub is a hosting platform which you can put your Git repositories and access them from anywhere and share them with others.

You can use GitHub for:
- Stay up to date
- Collaboration
- Open source projects
- Exposure

## Cloning
You can clone a remote repository. When cloning a repository, you need to be sure that you are not inside of a repository.
`git clone <repository-url>`

## Adding A Remote Repository
After you worked on your project locally, you can push it into your remote repository.
- Create a new repository on your github account.
- Add the remote repository on your local.

`git remote add <name> <url>`

Note: Name will refer to the url. The common name is "origin".

`git remote rename <old> <new>`

`git remote remove <name>`

`git push <name> <branch>` to push your branch to your remote repository. `git push origin master`

`git push <name> <local-branch>:<remote-branch>`, so remote and local branches do not have to have same names.

`git push -u <name> <local-branch>` or `git push -u <name> <local-branch>:<remote-branch>` it is set your local branch to remote branch. You can use `git push` only.

`git branch -M <new-name>` to change your branch name.

`git branch -r` to view remote branches

## Git Fetching & Pulling
You can download changes from a remote repository by using `git fetch <remote>` or `git fetch <remote> <branch>`, those changes is not integrated into your working files.

`git pull <remote> <branch>` updates your HEAD branch with whatever changes are in remote repository.

`git pull` = `git fetch` + `git merge`

If you use `git pull` without any remote and branch, git assume that remote will default to origin and branch will default to whatever remote branch configured for your current branch.

> Working area --`git add`-> Staging area
> 
> Staging area --`git commit`-> Local Repository
> 
> Local repository --`git push`-> Remote Repository
>
> Remote Repository --`git fetch`-> Local Repository
>
> Remote Repository --`git pull`-> Working area
