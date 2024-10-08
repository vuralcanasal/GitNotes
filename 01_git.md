![git logo](/images/Git-Icon-1788C.svg)

# What is Git?
Git is a tool that tracks changes to files over time. It helps you view previous versions of files, undo changes, and compare differences.

## Git vs. GitHub
+ Git: Runs on your local machine. No registration or internet is needed.
+ GitHub: An online service that stores and shares Git repositories. Requires registration and an internet connection.

You can download Git from git-scm.com/downloads. It is available for Linux, macOS, and Windows in terminal and GUI versions. After installing, remember to set up your name and email:
```
git config --global user.name <username>
git config --global user.email <useremail>
```

# Git Init
To create a new Git repository, use the `git init `command. You need to initialize a repository before starting a new project with Git. Git should be initialized only once per project and should be done at the top level of the project directory. 

__DO NOT INIT A REPO INSIDE OF A REPO__

To check if Git is initialized for a project, use `git status` command. If Git is not initialized, the output message will be:
> not a git repository (or any of the parent directories): .git

Example of `git init` for a new project:

+ Create a new folder for your git project
+ Inside of the project folder, initialize the git project:
```
git init
```

## .git Folder
This is a hidden folder created by `git init`. The .git folder contains all related data, such as logs, branches, descriptions, configurations, and more. If you delete this folder, you will lose all historical data for your project.

_The basic workflow for Git is:_
1. Work on project (working directory)
   - Create new files, delete files, edit files etc.
2. Add changes (staging area)
   - Group specific changes by `git add` command
3. Commit (repository)
   - Commit added changes with a comment by `git commit` command

```mermaid
graph TD;
  working_directory-->staging_area;
  staging_area-->repository;
```

## .gitignore
A ".gitignore" file tells Git which files or directories to ignore in a project. This is useful for keeping sensitive information, like secrets or API keys, and unnecessary files, like dependencies, out of your repository. Examples of ".gitignore" entries:
* .FileName --> ignore files named .FileName
* FolderName/ --> ignore an entire directory
* *.extension --> ignore any files with the .extension

You can add comments in a ".gitignore" file by starting the line with a "#".
To include a file that would otherwise be ignored, prefix the pattern with an exclamation mark "!".
> #Ignore all .log files
>
> *.log
>
> #Include a specific file that would otherwise be ignored
>
> !important.log

This is a hidden file which you need to create.

# Git Add
After working on your project, you can see the changed files by using `git status`:
> On branch main
> Your branch is up to date with 'origin/main'.
>
> Untracked files:
>   (use "git add <file>..." to include in what will be committed)
>       01_Init_Add_Commit.md
>       02_Branches.md
>
> nothing added to commit but untracked files present (use "git add" to track)

As you see in the output, you can use `git add <file1>, <file2>, ..., <file(n)>`

Currently, the files are untracked. To move them into the staging area (tracked files), use the `git add` command. Since we have two different files, you will need to add them both to the staging area.

The steps:
1. move 01_Init_Add_Commit.md file to staging area.
2. commit 01_Init_Add_Commit.md to repository with comment "git init / git add / git commit sections"
3. move 02_Branches.md file to stagin area.
4. commit 02_Branches.md file to repositoru with comment "create empty 02_Branches.md file"

After step 1 - adding 01_Init_Add_Commit.md file, the output of `git status':
> On branch main
> Your branch is up to date with 'origin/main'.
>
>Changes to be committed:
>   (use "git restore --staged <file>..." to unstage)
>       new file:   01_Init_Add_Commit.md
>
>Untracked files:
>  (use "git add <file>..." to include in what will be committed)
>   	02_Branches.md

Now, we can commit 01_Init_Add_Commit.md with a comment. However, if you notice a mistake in the file and want to fix it, you can unstage the file by using the following command:
```
git restore --staged 01_Init_Add_Commit.md
```
The output of git status again:
> On branch main
> Your branch is up to date with 'origin/main'.
>
> Untracked files:
>   (use "git add <file>..." to include in what will be committed)
>       01_Init_Add_Commit.md
>       02_Branches.md
>
> nothing added to commit but untracked files present (use "git add" to track)

# Git Commit 
We use `git commit` command to commit changes from the staging area to the repository and create a snapshot. When committing, you need a message summarizing the changes.

If you use only `git commit`, it will commit all staged to the repository, and open a text editor for your commit message. Alternatively, you can use "-m" option to provide your message directly `git commit -m "<your message>"`.

Continuing with our example in the git add section, we have two untraked files which are 01_Init_Add_Commit.md and 02_Branches.md. First, add 02_Branches.md to the staging area and commit it to the repository. After that, repeat the process for 01_Init_Add_Commit.md.

`git add 02_Branches.md`

`git status`
> On branch main
> Your branch is up to date with 'origin/main'.
>
>Changes to be committed:
>   (use "git restore --staged <file>..." to unstage)
>       new file:   02_Branches.md
>
>Untracked files:
>  (use "git add <file>..." to include in what will be committed)
>   	01_Init_Add_Commit.md

`git commit -m "Create an empty 02_Branches.md file"`
> [main 9f27a05] Create an empty 02_Branches.md file
>  1 file changed, 0 insertions(+), 0 deletions(-)
>  create mode 100644 02_Branches.md

`git status`
On branch main
>Your branch is ahead of 'origin/main' by 1 commit.
>  (use "git push" to publish your local commits)
>
> Untracked files:
>   (use "git add <file>..." to include in what will be committed)
>	    01_Init_Add_Commit.md
>
> nothing added to commit but untracked files present (use "git add" to track)

Therefore, we committed 02_Branches.md to the repository with its own message. We can use `git add` and `git commit` to stage and commit changes to the repository with their own messages.

## Git Commit --amend
If you forgot to commit a file, you can use `git commit --amend` to add it to your last commit. For example, if you committed file1 and file2 but forgot file3, just stage file3 and run:
```
git add file3
git commit --amend
```
This will include file3 in your last commit, and you can keep the same commit message or write a new one. Also, you can use `git commit --amend` to change your last commit message.

# Git Log
`git log` is a command to show the committed changes. If you use --name-only option you can see them with the related files.

`git log --name-only`
> commit c57ef243a08cca97c14c5a52f632a69f22c0c607 (HEAD -> main)
> Author: vuralcanasal <vuralcanasal@gmail.com>
> Date:   Sat Aug 31 18:15:31 2024 +0300
>
>    fixed typo mistakes for 01_Init_Add_Commit.md, and create empty 03_Git_Diff.md
>
> 01_Init_Add_Commit.md
> 03_Git_Diff.md
>
> commit 50f3897b371069c789860a7c41aa7d304c318e8a (origin/main)
> Author: vuralcanasal <vuralcanasal@gmail.com>
> Date:   Sat Aug 31 17:26:18 2024 +0300
>
>    fix typo mistake - continue
>
> 01_Init_Add_Commit.md
>
> commit cbbb037444badc7e195d8907829e55a993408e0e
> Author: vuralcanasal <vuralcanasal@gmail.com>
> Date:   Sat Aug 31 17:13:32 2024 +0300
>
>    git init / git add / git commit sections
>
> 01_Init_Add_Commit.md

`git log --oneline` very short.

# Git Branch
Branches are pointers to specific snapshots of your changes. You can work on multiple things simultaneously without affecting the main project until you merge your changes back in. In basic words, branches are alternative timelines for projects.

## Master and Main Branch
The default branch name is "master". It is not a special branch. It is like any other branch. For example, GitHub renamed the default branch from "master" to "main", but the default Git branch name is "master".

## HEAD
Head is a pointer referring to a current location in your repository. There can be multiple branches and commits in a project, and the head shows you where you are.

## Git Branch Command
* `git branch` to view your existing branches.
* `git branch <new branch name>` to create new branch. You are still on the current branch after this.
* `git switch <branch name>` to switch to a branch. Also, you can create a new branch and switch to it by `git switch -c <new branch name>`.
* `git checkout <branch name>` to switch to a branch, so it is an older version of the switch. Both work.

__If you switch to another branch without committing your work, you can lose your work. Always commit your work before switching branches to avoid losing changes.__

* `git branch -d <branch name>` to delete a branch. You can not delete the branch you are currently on. Switch to another branch first. If the branch you want to delete is not fully merged, you should force the branch to be deleted by `git branch -D <branch name>`.
* `git branch -m <branch rename>` to rename a branch. Actually, you move the branch to a new name. You need to be on the branch you want to rename.

## Git Merge
You can work on different features for your project in parallel thanks to branches. When you need to combine these features, `git merge` will help you. You always merge to the current HEAD branch. It means that you need to switch to the master branch if you want to merge any branch into the master branch. In short, you switch to the branch you want to merge into and type `git merge <the branch you want to merge>`.


### Merge conflicts:

Here is the output example of a merge conflict example:

`git merge <branch name>` command and the output:
> git merge merge
> Auto-merging 02_Branches.md
> CONFLICT (content): Merge conflict in 02_Branches.md
> Automatic merge failed; fix conflicts and then commit the result.

File you need to fix:
> <<<<<<< HEAD
>
> The content from your current HEAD is displayed between:
> <<<<<<<<< HEAD and ============
>
> =======
>
> The content from your the branch you try to merge is displayed between:
> ============ and >>>>>>>>>>>
>
> \>\>\>\>\>\>\> merge

You need to resolve it manually. Decide which content you want to keep in each conflict, edit and save the file.

Why is there a conflict?
* Somebody modified a file, and somebody deleted the same file.
* Somebody edits some lines of some files, and somebody edits the same lines of the same files or one of the same files.

## Git Rebase
`git rebase` is a kind of merge command. `git rebase <branch>`.

You can use `git rebase` to get a cleaner and linear project history.

!!! You should NOT rebase commits shared with others !!!

Because rebase changes the history.

Therefore, you can re-write the history by `git rebase`. This is "interactive rebase". `git rebase -i HEAD~<n>`

After you use `git rebase -i HEAD~<n>`, you will see a list of commands you can choose from. Here are some common commands:
- pick: use the commit
- reword: use the commit, but edit the commit message
- edit: use commit, but stop for amending
- fixup: use commit contents, but meld it into the previous commit and discard the commit message
- drop: remove commit

## Git Stash (like a stack)
If you need to switch to another branch without committing your work, and it causes a conflict, you can use `git stash` or `git stash save`. Thanks to that, you do not have to make unnecessary commits.

`git stash pop` removes the recently stashed changes and re-apply them to your working area. You can apply them for the same branch or a different branch. After popping, changes are removed from the stash-stack.

`git stash apply` helps you to apply changes without removing changes from the stash. Thanks to that, you can apply the same changes to multiple branches.

__stash stack is first in - first out__

`git stash list` lists all stashes.

`git stash apply stash@{<index number>}` applies the specific changes from stash.

`git stash drop stash@{<index number>}` deletes the specific changes from stash without appling.

`git stash clear` to delete all changes from the stash.

# Git Diff (Comparisons)
You can see changes between branches, files, etc.

`git diff` shows the changes in your working directory.

> diff --git a/03_Git_Diff.md b/03_Git_Diff.md
>
> index 15776cd..7e2072c 100644
>
> --- a/03_Git_Diff.md
>
> +++ b/03_Git_Diff.md
>
> @@ -1 +1,4 @@
>
> -# Git Diff
>
> +# Git Diff (Comparisons)
>
>
> +You can see changes between branches, files, etc.
>
> \+
>
> +`git diff` shows the changes in your working directory.

The output says there are changes in 03_Git_Diff.md file. If the line starts with "-", it means that it is the old line from the old version of the file. If the line starts with "+", it means that it is the new line from the new version of the file. "# Git Diff" is the old line and "# Git Diff (Comparisons)", "You can see changes between branches, files, etc.", " " and "`git diff` shows the changes in your working directory." are the new lines in 03_Git_Diff.md file. 

`git diff HEAD` compares the working directory and the last commit.

`git diff --staged` or `git diff --cached` compares the staging area and the last commit.

`git diff <option> <file name> <file name> ...` If you want to check changes for specific files, you should add the names of the files. 

`git diff <branch name>..<branch name>` compare two branches.

`git diff <commit1>..<commit2>` compare two commits.

# Undo
You can use `git checkout` to create new branches, switch to another branch, restore files, and undo history.

`git checkout commit <commith-hash>` to view a previous commit.

> __DETACHED HEAD__
>
> You are in "detached HEAD" state. You can look around, make experimental changes and commit them, and you can discard any commits you make in this state without impacting any branches by switching back to a branch.

This means HEAD points at that commit not at the branch.
1- You can stay detached HEAD to view old commits.
2- Re-attach the HEAD.
3- Create a new branch and switch to it.

To re-attach the HEAD `git switch <branch name>`

To create a new branch `git switch -c <new branch name>`

`git checkout HEAD~n` to view the commit HEAD - n (before n commit)

`git checkout HEAD~n <file name>` to revert a file n step back to its last commit. To discard changes.

`git restore --source HEAD~n <file name>` to revert a file n step back to its last commit. To discard changes.

`git restore --staged <file name>` to move a staged file as an unstaged file.

`git reset <commit hash>` to reset the repo back to a specific commit. The commits are gone, you still have changes. If you have mistakes about your commit (wrong branch, wrong message, etc.), you can use reset.

`git reset --hard <commit hash>` delete last commits and changes.

`git revert <commit hash>` is the same as reset, but revert creates a new comment with the changes.

# Tags
You can mark a particular moment in time with a tag. Tags are labels for commits. There are two types of tags:

- lightweight tags are just a label that points to a particular commit.
- annotated tags store extra metadata including the author's name, e-mails, date, and tag message.

You can use tags for version releases, like v2.5.3. According to semantic versioning, the numbers mean that "<major release>.<minor release>.<patch release>" 

`git tag` views a list of all tags.

`git tag -l <pattern>` like `git tag -l <*alpha*>` views a list of all tags including "alpha".

`git checkout <tagname>` to check the changes according to the tagged commit.

`git diff <tagname1> <tagname2>` to check the  changes between tag.

`git tag <tagname>` to create a lightweight tag referring to the commit which HEAD referencing. `git tag <tagname> <commit hash>`

`git tag -a <tagname>` to create an annotated tag referring to the commit which HEAD referencing. `git tag -a <tagname> <commit hash>`. You can use "-m" to set your message like "git commit -m".

`git show <tagname>` to see the details about tag.

If you move your tag to another commit, you can use "-f"  option to force it.

`git tag -d <tagname>` to delete a tag.

`git push --tags` to push tags to the remote repository. `git push <remote> <tag-name>` for one tag.

