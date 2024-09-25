# .git/
You can see ".git" folder in any git repositories. There are lots of file and folder inside of it. Here are some of them.

## config
The config file is for configuration of your repository.
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

For more option: git-scm.com/docs/git-config

## refs
The refs folder has a "heads" folder. The heads folder has one file per a branch. Each file is named by its branch and has the last commit hash of the branch. For instance, refs/heads/main contains the commit hash of the last commit on the main branch.

The refs folder has another folder for tags, refs/tags containing one file for each tag.

The refs structure is same for all folders inside it.

## HEAD
HEAD is a text file contains track of where HEAD is.

If the HEAD contains refs/heads/<branch name>, HEAD is pointing to the branch.

If the HEAD contains a commit hash, it means HEAD is detached and pointing to a commit.

## objects
The objects folder has all the repository files. It has the backups of file, the commits and more. The files are encrypted.

If you want to retrieving the encripted "object hash" file, you can use `git cat-file -p <object-hash>`.

### Blobs
Git Blobs are the object type to store the contents of files (binary large objects).

### Trees
Git Trees are the objects to store the contents of a directory. Each tree contains pointers that can refer to blobs and trees. To list the trees and blobs `git cat-file -p main^{tree}`.

### Commits
Commit hashs has tree, and more information. You can use commit hash to reach out to the files. Example, here are two commit `git log`:

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

