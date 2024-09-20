# Tags
You can mark a particular moment in time with a tag. Tags are labels for commits. There are two types of tags:

- lightweight tags are just a label that points to a particular commit.
- annotated tags store extra meta data including the author's name, e-mails, date, tag message.

You can use tags for version releases, like v2.5.3. According to semantic versioning, the numbers mean that "<major release>.<minor release>.<patch release>" 

`git tag` views a list of all tags.

`git tag -l <pattern>` like `git tag -l <*alpha*>` views a list of all tags including "alpha".

`git checkout <tagname>` to check the changes according to the taged commit.

`git diff <tagname1> <tagname2>` to check the  changes between tag.

`git tag <tagname>` to create a lightweight tag refering to the commit which HEAD referencing. `git tag <tagname> <commit hash>`

`git tag -a <tagname>` to create an annotated tag refering to the commit which HEAD referencing. `git tag -a <tagname> <commit hash>`. You can use "-m" to set your message like "git commit -m".

`git show <tagname>` to see the detail about tag.

If you move your tag to another commit, you can use "-f"  option to force it.

`git tag -d <tagname>` to delete a tag.

`git push --tags` to push tags to remote repository. `git push`
