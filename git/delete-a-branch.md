# Deleting A Branch

##### To delete a local branch (local meaning on your computer, and not on the server):

`git branch -d <branch_name>`

**-d** flag stands for --delete. Will only work if you have already merged/pushed with your remote branches.

`git branch -D <branch_name>`

**-D** flad stands for --delete --force, which will delete the branch regardless of its push and merge status. Use with caution!


##### To delete a remote branch:

`git push <remote_name> --delete <branch_name>`

`git push <remote_name> :<branch_ame>`

e.g. `git push origin --delete refactor`

