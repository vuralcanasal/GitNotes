# GitHub
GitHub is a hosting platform which you can put your Git repositories and access them from anywhere and share them with others.

You can use GitHub for:
- Stay up to date
- Collabration
- Open source projects
- Exposure

## Cloning
You can clone a remote repository. Whne cloning a repository, you need to be sure that you are not inside of a repository.
`git clone <repository-url>`

## Adding A Remote Repository
After you worked on your project locally, you can push it your remote repository.
- Create a new repositoru on your github account.
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

## Git Feching
You can download changes from a remote repository by using `git fetch <remote>`, those changes is not integrated into your working files.

`git pull <remote>` updates your HEAD branch with whatever changes are.

> Working area --`git add`-> Stageing area
> 
> Staging area --`git commit`-> Local Repository
> 
> Local repository --`git push`-> Remote Repository
>
> Remote Repository --`git fetch`-> Local Repository
>
> Remote Repository --`git pull`-> Working area


