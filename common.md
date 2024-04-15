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

