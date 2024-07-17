# Git and GitHub for Project Management

### Table of Contents

1. [xxxx](#1-x-x-x-x)

A version control system like Git helps us save the history of changes and growth of our project files.

Changes and differences between project versions can be similar, sometimes only altering a word or a specific part of a file. Git is optimized to store these changes atomically and incrementally, applying changes on top of previous ones back to the start of the project.

To start a repository with Git, use `git init`. To track a file or its latest changes, use `git add`. This command stages updates in the "Staging Area." To commit changes from the staging area, use `git commit` with a message using the `-m` argument. To push commits to a remote server, use `git push`.

**Basic Git Commands:**
- `git init`: Initializes a Git repository.
```sh
andrewbavuels@the-Legionnaire:~/git_github$ git init
Initialized empty Git repository in /home/andrewbavuels/git_github/.git/
```
- `git add`: Adds specified files to the staging area.
```sh
andrewbavuels@the-Legionnaire:~/git_github$ git add README.md
```
- `git commit -m "commit description"`: Commits staged files to the repository.
```sh
andrewbavuels@the-Legionnaire:~/git_github$ git commit -m "Initial commit"
```
- `git commit -am "commit description"`: Adds to staging and commits in one command (not for new files).
- `git status`: Describes the state of files.
- `git rm (. -r, filename) (--cached)`: Removes files from the index.
- `git config --global user.email "you@example.com"`: Configures an email.
- `git config --global user.name "name"`: Configures a name.
- `git config --list`: Lists configurations.

**Analyzing File Changes:**
- `git log`: Lists commits.
- `git log --stat`: Lists commits with byte changes in files.
- `git log --all --graph --decorate --oneline`: Shows a compressed, graphical history.
- `git show filename`: Shows file change history.
- `git diff`: Compares changes between commits.

**Reverting with Branches and Checkout:**
- `git reset --soft/hard`: Reverts to a specified commit, removing changes made after it.
- `git checkout`: Reverts to a specified commit or branch without altering the staging area.
- `git checkout --`: Discards changes in a modified file not staged.

**Removing Files with git rm and git reset:**
- `git rm --cached`: Removes files from staging and the next commit, but keeps them on the hard drive.
- `git rm --force`: Removes files from Git and the hard drive, but history can be accessed with advanced commands.

**Using git reset:**
- `git reset --soft`: Reverts to a commit, keeping files in the working directory and staging area.
- `git reset --hard`: Deletes all commit and staging information.
- `git reset HEAD`: Removes files from staging without deleting them or their modifications.

**Branches in Git:**
- Creating a branch copies the last commit to the new branch. Changes in this branch do not affect the master branch until merged.
- `git branch`: Creates a new branch.
- `git checkout`: Switches to the specified branch.
- `git merge`: Merges the specified branch into the current branch.
- `git branch`: Lists created branches.
