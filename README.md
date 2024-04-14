# Useful git commands

# 1. `git status`

To quickly check the modified, untracked, and staged files. Very useful to double check and avoid mistakes.

# 2. `git log`

To check the history of changes. The most recent change is at the top of the list

# 3. `git log --decorate --graph --oneline --all` 

Displays branching history

# 4. `git diff`

To quickly see the changes made since the last commit. Note that the changes have not been committed yet.

# 5. `git reset --mixed`

`--mixed` is the default flag for `git reset`. It takes items out of their added status but keeps them altered.

# 6. `git reset --hard`

`--hard` not only takes items out of their added status but cancels all changes and resets current state to the last commit. 

# 7. `git checkout`

This is used to checkout to a branch. However, it can also be used to point to a specific commit ID. In that case, the `HEAD is detached` meaning it is not pointing to a branch. You can make changes without affecting any branch. To keep the changes, you can create a new branch with `git checkout -b <branch name>`

# 8. `tag`

While `branch` is a pointer that points to a line if changes, `tag` is a pointer that points to a single change. `branches` have history, `tags` don't.

# git undo operations

# 1. `git revert`

This is git's the most basic undo method. If you make a commit and pushed it to the remote repository, but then realized the commit included a mistake and should be discarded, you can use this method to revert the changes done by the last commit. This will preserve the history and should be preferred for public repos.

```
git revert <SHA>
git push origin master
```

# 2. `git commit --amend`

Let's say you made a type in the most recent commit message. This method fixes that typo.

```
git commit -m "Fxies bug #42"
git commit --amend -m "Fixes bug #42"
```

# 3. `git checkout`

Undo local, uncommitted changes. This will delete all the changes that have been made, and restore the provided commit.

```
git checkout <SHA>
```

# 4. `git reset` or `git reset --hard`

Let's say you made some commits but you are not happy with them and want to delete them. `git reset` only undoes the commits, `git reset --hard` also undoes the changes.

# 5. `git reflog`

Let's say you used `git reset --hard` to undo some commits but later realized you want them back. `git reflog` provides a history for HEAD movements, so that you can pinpoint to a specific time in history. Some caveats:

- HEAD changes only.HEAD changes when you switch branches, make commits with git commit and un-make commits with git reset.
- git reflog doesn’t last forever. Don’t expect to find months-old commits lying around in the reflog forever.
- Your reflog is yours and yours alone. You can’t use git reflog to restore another developer’s un-pushed commits.

# 6. `git branch`

You made some commits, then realized you were checked out on `master`. You wish you could make those commits on a `feature` branch instead.

```
git branch feature
git reset --hard origin/master
git checkout feature
```

# 7. `git rebase`

You started a new branch feature based on master, but master was pretty far behind origin/master. Now that master branch is in sync with origin/master, you wish commits on feature were starting now, instead of being so far behind.

```
git checkout feature
git rebase master
```

1. First it locates the common ancestor between your currently-checked-out branch and master.
2. Then it resets the currently-checked-out branch to that ancestor, holding all later commits in a temporary holding area.
3. Then it advances the currently-checked-out-branch to the end of master and replays the commits from the holding area after master‘s last commit.

# 8. `git rm`

You accidentally added `application.log` to the repository, now every time you run the application, Git reports there are unstaged changes in `application.log`. You put *.log in the .gitignore file, but it’s still there—how do you tell git to to “undo” tracking changes in this file?

```
git rm --cached application.log
```
