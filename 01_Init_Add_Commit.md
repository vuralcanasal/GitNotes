# Git Init
To create a new git repository, `git init` command is used. You need to initialize a repo before starting a new project related with Git. Git should be initialized one time per project. Also, it should be initialized on the top level of the project. 

__DO NOT INIT A REPO INSIDE OF A REPO__

To check if Git is initialized for a project use `git status` command. If it is not initialized, the output message would be like this:
> not a git repository (or any of the parent directories): .git

Example of Git init for a new project:
```
mkdir new_project
cd new_project
git init
```

## .git Folder
This is a hidden file created by `git init`. You can see it by typing `ls -a`. You can see all related material "logs, branches, description, configuration, etc" in this hidden folder ".git". If you remove this file, you lose all the historical data in your project.

_The basic workflow for Git is:_
1. Work on project (working directory)
   - Create new file, delete files, edit files etc.
2. Add changes (staging area)
   - Group specific changes by `git add` command
3. Commit (repository)
   - Commit added changes with a comment by `git commit` command

# Git Add
After working on your project, you can see changed files in `git status`:
> On branch main
> Your branch is up to date with 'origin/main'.
>
> Untracked files:
>   (use "git add <file>..." to include in what will be committed)
>       01_Init_Add_Commit.md
>       02_Branche.md
>
> nothing added to commit but untracked files present (use "git add" to track)

As you see in the output, you can use `git add <file1>, <file2>, ..., <file(n)>`

Now, the files are untacked. We will move our files into staging area (tranked files) by using git add. In this movement, we have two different files, so we need to group them by moving into staging area.

The steps:
1. move 01_Init_Add_Commit.md file into staging area.
2. commit 01_Init_Add_Commit.md into repository with comment "git init / git add / git commit sections"
3. move 02_Branche.md file into stagin area.
4. commit 02_Branche.md file into repositoru with comment "create empty 02_Branche.md file"

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
>   	02_Branche.md

Now, we can commit 01_Init_Add_Commit.md with its comment, but we recognized a mistake on the file, and want to fix it. As you can see on the output, we can move the file to unstage by:
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
>       02_Branche.md
>
> nothing added to commit but untracked files present (use "git add" to track)

# Git Commit 
We use `git commit` command to commit chages from staging are to repository, and create a snapshot. By using commit, we need a message summarizing the changes.

If you use only `git commit`, it will commit all staged to repository, and open a text editor for your commit message. Instead of it, you can use "-m" option to provide your message `git commit -m "<your message>"`.

Now, we can contionu our example in the git add part. Now, we have two untraked file which are 01_Init_Add_Commit.md and 02_Branche.md. Firstly, we add 02_Branche.md to staging area, then commit it to repository. After that, we will do same thing our 01_Init_Add_Commit.md.

`git add 02_Branche.md`
`git status`
> On branch main
> Your branch is up to date with 'origin/main'.
>
>Changes to be committed:
>   (use "git restore --staged <file>..." to unstage)
>       new file:   02_Branche.md
>
>Untracked files:
>  (use "git add <file>..." to include in what will be committed)
>   	01_Init_Add_Commit.md
`git commit -m "Create an empty 02_Branche.md file"`
> [main 9f27a05] Create an empty 02_Branche.md file
>  1 file changed, 0 insertions(+), 0 deletions(-)
>  create mode 100644 02_Branche.md
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

Therefore, we commited 02_Branche.md to repository with its own message. We can use `git add` and `git commit` to group works and commit them to repository with our own messages.
