# Renaming a commit

Lets say you made a mistake in your most recent commit message and want to
change it before pushing to remote.

##### Renaming a commit message in your editor 

This will open up whatever your default editor is, allowing you to modify the
most recent commit message.

`git commit --amend`



##### Renamding a commit and passing in a message via the CLI

You can also use `-m` to pass in a new message from the command line without
being prompted to open an editor.

`git commit --amend -m "Updated commit message"`



#### What if I need to change it on remote as well?

If you are changing a commit message that you also pushed to remote, you need
to then push again after running `git commit --amend ...`.

`git push --force origin branch-name`

It should be noted that using `--force` can be dangerous as it will destory any
changes that anyone has done upstream on your branch. Instead, use
`--force-with-lease`. This will abort if there were any upstram changes.

`git push --force-with-lease origin branch-name`

