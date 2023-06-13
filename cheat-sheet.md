| git command                        | Description                                                           |
| ---------------------------------- | --------------------------------------------------------------------- |
| `git clone <url>`                  | Create a local copy of the given repository                           |
| `git checkout -b <branch_name>`    | create a new local branch                                             |
| `git checkout <branch_name>`       | Checkout existing branch                                              |
| `git checkout -`                   | Checkout branch before the last `git checkout`                        |
| `git status`                       | Show local changes                                                    |
| `git add <file>`                   | Add a changed file to the index                                       |
| `git add -p`                       | Add local changes interactively                                       |
| `git add -A`                       | Add all local changes to the index                                    |
| `git commit`                       | Create a commit                                                       |
| `git commit -m "message"`          | Create a commit with message                                          |
| `git commit --amend`               | Change/Adjust the current commit and/or its message                   |
| `git fetch --all`                  | Get all branches from all remote repositories                         |
| `git pull`                         | Update current branch to the remote state                             |
| `git pull --rebase`                | Update local branch to remote, apply changes via rebase               |
| `git push`                         | Upload local changes to remote                                        |
| `git push -u origin <branch_name>` | Upload a new local branch to remote                                   |
| `git push --force-with-lease`      | Rewrite remote commits                                                |
| `git rebase <branch>`              | Rebase you local branch on the specified branch                       |
| `git merge <branch>`               | Merge the specified branch into your branch (creating a merge commit) |

# Possible Workflow

```sh
# Get a new repo
git clone git@github.com:openknowledge/git-tutorial.git
# Or pull an existing repo to get latest changes
git pull --rebase
# Create a branch to work on
git checkout -b feat/awesome-feature
# Do some file change
echo "Test" > new_file.txt
# Stage the changes I want create a commit for
git add new_file.txt
# Create a commit
git commit -m "feat: Adds this awesome feature"
# Upload branch
git push -u origin feat/awesome-feature

# You keep working by creating commits
git commit -m "fix: Fixes some bug"
git push
# ...

# The commit you just pushed has errors: You want to fix them
# Adjust the code
echo "This is correct now" > new_file.txt
# Add local change to index
git add new_file.txt
# Change the current commit
# Maybe change the commit message, or keep it as it is.
git commit --amend
# Change upstream branch to have the fixed commit
git push --force-with-lease

# Time passes. You want to update your branch to the current main state

# check for a clean state (no local changes, no unpushed commits)
git status
# checkout main branch
git checkout main
# update to current upstream state
git pull
# checkout former branch (the one we were working on)
git checkout -
# Rebase changes
git rebase main
# Push your changes (rewriting the history since you rebased on main)
git push --force-with-lease
```
