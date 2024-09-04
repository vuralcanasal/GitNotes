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

The output says you there are changes in 03_Git_Diff.md file. If the line start with "-", it means that it is the old line. If the line start with "+", it means that it is the new line. "# Git Diff" is the old line and "# Git Diff (Comparisions)", "We can see changes between branches, files, working directory, etc.", " " and "`git diff` shows the changes in your working directory." are the new lines in 03_Git_Diff.md file. 

