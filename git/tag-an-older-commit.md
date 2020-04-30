# Tag an older commit

While learning semver and gitflow, I had to get familiar with git tagging. I had some older feature/hotfix branches
that had since been merged into develop, but lacked any tagging. Fortunately, git allows you to go back and add tags
to any commit ref.

#### To tag an an older commit, while keeping the current date, run the following:


`git tag -a v0.1.2 bc1ef8c -m "Your message here"`


#### If you want the tag to be dated with the original commit date:


```
# Set the HEAD to the old commit that we want to tag
git checkout 9fceb02

# temporarily set the date to the date of the HEAD commit, and add the tag
GIT_COMMITTER_DATE="$(git show --format=%aD | head -1)" \
git tag -a v1.2 -m"v1.2"

# set HEAD back to whatever you want it to be
git checkout master

```




# Further reading
- https://git-scm.com/book/en/v2/Git-Basics-Tagging
- https://github.com/openmelody/melody/wiki/devbest-tagging
- https://stackoverflow.com/questions/4404172/how-to-tag-an-older-commit-in-git/21759466#21759466
