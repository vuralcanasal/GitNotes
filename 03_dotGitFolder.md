# .git/
You can see ".git" folder in any git repositories. There are lots of files and folders inside of it. Here are some of them.

## config
The config file is for the configuration of your repository.
Example:1
- You can set your username globally by `git config user.name <name>`.
- You can set your username locally by `git config --local user.name <name>`.
If you set your local username, you can see under the "[user]" section in the config file. Also, you can set it or modify it in the config file.

Example:2
You can change your git diff output colors in the config file.
> [color]
>
> [color "diff"]
>
>   new = magenta

For more information: git-scm.com/docs/git-config

## refs
The refs folder has a "heads" folder. The heads folder has one file per branch. Each file is named by its branch and has the last commit hash of the branch. For instance, refs/heads/main contains the commit hash of the last commit on the main branch.

The refs folder has another folder for tags, refs/tags containing one file for each tag.

The refs structure is the same for all folders inside it.

## HEAD
HEAD is a text file containing a track of where HEAD is.

If the HEAD contains refs/heads/<branch name>, HEAD is pointing to the branch.

If the HEAD contains a commit hash, it means HEAD is detached and pointing to a commit.

## objects
The objects folder has all the repository files. It has the backups of files, the commits, and more. The files are encrypted.

If you want to retrieve the encrypted "object hash" file, you can use `git cat-file -p <object-hash>`.

### Blobs
Git Blobs are the object types that store the contents of files (binary large objects).

### Trees
Git Trees are objects that store the contents of a directory. Each tree contains pointers that can refer to blobs and trees. To list the trees and blobs `git cat-file -p main^{tree}`.

### Commits
Commit hashes have a tree and more information. You can use commit hash to reach out to the files. For example, here are two commit `git log`:

> commit 163116ce7e6341af63b216a43fd5033223a84999
> 
> Author: vuralcanasal <vuralcanasal@gmail.com>
> 
> Date:   Tue Sep 24 16:10:04 2024 +0300
>
>    add git diff stash
>
> commit c1153a42d3c4bf024e44e6d90ba5a1363d732c8d
>
> Author: vuralcanasal <vuralcanasal@gmail.com>
>
> Date:   Tue Sep 24 11:31:18 2024 +0300
>
>    git diff to 01

`git cat-file -t 163116ce7e6341af63b216a43fd5033223a84999`

> commit

`git cat-file -p 163116ce7e6341af63b216a43fd5033223a84999`

> tree 5d2029931787500c74eb0fa82991b24c3fd7f678
>
> parent c1153a42d3c4bf024e44e6d90ba5a1363d732c8d
> 
> author vuralcanasal <vuralcanasal@gmail.com> 1727183404 +0300
> 
> committer vuralcanasal <vuralcanasal@gmail.com> 1727183404 +0300
>
> add git diff stash

View the tree, `git cat-file -p 5d2029931787500c74eb0fa82991b24c3fd7f678`

> 100644 blob 5843cacd44fd4d06fafc7bfcdc49d83d93af78d9	01_git.md
>
> 100644 blob fc8d5ee5bfc8872979188a8e357e05d2bacdfd94	06_Undo.md
>
> 100644 blob 0d451455640af19d834435189064ea6fcf7eab75	07_GitHub.md
>
> 100644 blob 49c28aac343f3c14fbfc385f3f88c0565d43fdc8	08_Tags.md
> 
> 100644 blob 82051459de37338d0e37893c81ef5c0e71b5c985	README.MD
>
> 040000 tree f251d0ee18b6bbb4c4ae1b823e986a505021062b	images

Then you can view the contents of the blobs or view the tree "images"...

## logs
The logs folder stores the reflogs in the repository. In the logs folder, there is a file HEAD. It keeps the HEAD log such as commits, switches, etc. It is readable:

> <vuralcanasal@gmail.com> 1726560823 +0300	checkout: moving from main to origin/main
>
> d279cf8fff01e1252bf033b59ae0621ea5e0948e 90394f34643cf17794bc4e0ce4fdd06a6b82c09c vuralcanasal <vuralcanasal@gmail.com> 1726560834 +0300	checkout: moving from d279cf8fff01e1252bf033b59ae0621ea5e0948e to main
>
> 90394f34643cf17794bc4e0ce4fdd06a6b82c09c aad42d079a46104a5baf27d17cf9b11bb4cdd418 vuralcanasal <vuralcanasal@gmail.com> 1726573292 +0300	commit: git fech
> 
> aad42d079a46104a5baf27d17cf9b11bb4cdd418 66dee2b8b27a92e930c8d85359279ac66167bd26 vuralcanasal <vuralcanasal@gmail.com> 1726642016 +0300	commit: git fetch - pull
>
> 66dee2b8b27a92e930c8d85359279ac66167bd26 604ab600b267a43cf5eb61b114f05c0e0186f58e vuralcanasal <vuralcanasal@gmail.com> 1726642530 +0300	commit: 07 typo fixed

Also, You can see the reflogs by `git reflog`. Reflogs are local.

`git reflog show <branch-name>` to show the reflogs for the branch. The default it is HEAD.

`git reflog show merge` for merge branch:

> 9d570ff (merge) merge@{0}: Branch: renamed refs/heads/master to refs/heads/merge
>
> 9d570ff (merge) merge@{1}: Branch: renamed refs/heads/merge to refs/heads/master
>
> 9d570ff (merge) merge@{2}: commit: merge test
>
> 4fdd949 merge@{3}: merge master: Fast-forward
>
> 2a855b7 merge@{4}: commit: merge conflicts
>
> 1abf1fb (switch) merge@{5}: branch: Created from master

`git reflog show HEAD@{n}` shows  all from the beginning to n moves ago.

<name>@{qualifier} to access a specific git ref.

Time Reference:
* <name>@{2.days.ago}

* <name>@{one.week.ago}

* <name>@{yesterday}

For example, you can see the differences between now and 2 days ago.
`git diff main main@{2.days.ago}`

You can remove any commit by `git reset --hard <commit-hash>`. It also removes the work from the working directory. If you lose any work like that, you can get that commit back from reflogs. After the command `git reflog show <branch>` and finding the lost work with the commit-hash and the qualifier, you can use `git reset --hard` to get your work back. `git reset --hard <branc>@{qualifier}`.

Also, you can use `git reflog` and `gir resert --hard` for wrong rebase actions.

For more information, git-scm.com/docs/git-reflog.

