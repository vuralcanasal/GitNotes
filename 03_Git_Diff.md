# Git Diff (Comparisions)
We can see changes between branches, files, working directory, etc.

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
> +# Git Diff (Comparisions)
>
>
> +We can see changes between branches, files, working directory, etc.
>
> \+
>
> +`git diff` shows the changes in your working directory.

The output says you there are changes in 03_Git_Diff.md file. If the line start with "-", it means that it is the old line from the old version of the file. If the line start with "+", it means that it is the new line from the new version of the file. "# Git Diff" is the old line and "# Git Diff (Comparisions)", "We can see changes between branches, files, working directory, etc.", " " and "`git diff` shows the changes in your working directory." are the new lines in 03_Git_Diff.md file. 

`git diff HEAD` compares working directory and last commit.

`git diff --staged` or `git diff --cached` compares staging area and last commit.

`git diff <option> <file name> <file name> ...` If you want to check changes for specific files, you should add the names of the files. 

`git diff <branch name>..<branch name>` compare two branches.

`git diff <commit1>..<commit2>` compare two commits.

