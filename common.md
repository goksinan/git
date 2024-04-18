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

# 9. `git bisect`

Let's say you have a lot of commits, but at the last commit you noticed a bug. Now, you want to figure out where the bug was introduced and its root cause. You can use `git bisect` to debug the commits and pinpoint to the exact commit when the bug was introduced. This procedure requires to compile commits, run them, and label it as GOOD or BAD commit (has the bug or not)

# 10. `git fetch`

This is to download changes from a remote repository, but in a way safer than the `git pull`.
Check all branches after fetching a remote branch:
```
git fetch origin master
git branch --all

> * master
>  remotes/origin/HEAD -> origin/master
>  remotes/origin/master
```
As you see that the local branch remained unchanged, but all the changes from remote branch is copied locally to a new branch called origin/master. After examining the content of of the remote repo, you can merge it into the local branch:
```
git merge origin/master
```

# 11. `git submodule`

Submodules allow you to keep a Git repository as a subdirectory of another Git repository. This lets you clone another repository into your project and keep your commits separate.

When checkout a project that includes git submodules, the submodules are not automatically downloaded with the main project. You have to separately initialize and update those submodules:
```
git submodule init
git submodule update
```

Fortunately, there is an easier way. You can clone the repository with a --recursive flag to automatically init and update any submodules (and submodules of those submodules ad infinitum) within the cloned repository:
```
git clone --recursive <repo>
``
