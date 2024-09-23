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

## Git Init
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

### .git Folder
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
  working directory-->staging area;
  staging area-->repository;
```

### .gitignore
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

## Git Add
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

## Git Commit 
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

### Git Commit --amend
If you forgot to commit a file, you can use `git commit --amend` to add it to your last commit. For example, if you committed file1 and file2 but forgot file3, just stage file3 and run:
```
git add file3
git commit --amend
```
This will include file3 in your last commit, and you can keep the same commit message or write a new one. Also, you can use `git commit --amend` to change your last commit message.

## Git Log
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

