# Renaming a commit

Lets say you made a mistake in your commit message and want to change it
before pushing to remote.

##### Renaming a commit adding a commit message in your editor 

This will open up whatever your default editor is, allowing you to modify the
most recent commit message.

`git commit --amend`



##### Renamding a commit and passing in a message via the CLI

You can also use `-m` to pass in a new message from the command line without
being prompted to open an editor.

`git commit --amend -m "Updated commit message"`

