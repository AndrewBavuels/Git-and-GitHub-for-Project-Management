# Git and GitHub for Project Management

## (In working progress..)

### Table of Contents

1. [Intro - Personal Journey starting this Repository](#1-Intro---Personal-Journey-starting-this-Repository)

## 1. Intro - Personal Journey starting this Repository

Git and GitHub together provide robust version control capabilities, enabling efficient and collaborative software development while GitHub extends these capabilities with project hosting, social features, and collaboration tools. Understanding these tools is crucial for modern software development practices.

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


- `git status`: Describes the state of files.
```sh
andrewbavuels@the-Legionnaire:~/git_github$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

andrewbavuels@the-Legionnaire:~/git_github$ git commit -m "Update README"
[master f7739e2] Update README
 1 file changed, 6 insertions(+)
```
**Suggestion:** Do `git status` for every action taken, one after another. ALWAYS.

**Branches in Git:**

- `git branch -M main`: rename the current branch master to master (RECOMMENDED).
```sh
andrewbavuels@the-Legionnaire:~/git_github$ git branch -M main
andrewbavuels@the-Legionnaire:~/git_github$ git status
On branch main
```
- `git remote add origin <remote_url>`: sets up a connection between your local repository and a remote repository, typically hosted on platforms like GitHub.

(insert image here)
```sh
andrewbavuels@the-Legionnaire:~/git_github$ git remote add origin git@github.com:AndrewBavuels/Git-and-GitHub-for-Project-Management.git
```

- `git push -u origin main`: upload your project from your local main branch to the main branch of the remote repository in GitHub.

```sh
andrewbavuels@the-Legionnaire:~/git_github$ git push -u origin main
To github.com:AndrewBavuels/Git-and-GitHub-for-Project-Management.git
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'git@github.com:AndrewBavuels/Git-and-GitHub-for-Project-Management.git'
```
## What did it just happen!?

- `git pull origin main`: integrate changes from a remote repository (origin) into your current branch (main) back in your local repository.
```sh
andrewbavuels@the-Legionnaire:~/git_github$ git pull origin main
...
fatal: refusing to merge unrelated histories
```
- `git pull origin main --allow-unrelated-histories`: I've started a new local repository and then pulled changes from a remote repository that I did not create at first.
```sh
andrewbavuels@the-Legionnaire:~/git_github$ git pull origin main --allow-unrelated-histories
...
error: Your local changes to the following files would be overwritten by merge:
        README.md
Please commit your changes or stash them before you merge.
```
Now:
```sh
andrewbavuels@the-Legionnaire:~/git_github$ git push origin main
```
(Insert Image here)
## Wrap up:

**Basic Git Commands:**
- `git init`: Initializes a Git repository.
- `git add`: Adds specified files to the staging area.
- `git commit -m "commit description"`: Commits staged files to the repository.
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

## 2. About Git and GitHub

#### What is Git?
Git is a distributed version control system designed by Linus Torvalds to manage changes to files and facilitate collaboration in software development projects. It tracks changes incrementally, allowing users to revert to previous versions and integrate new features. Originally for Linux, Git is now cross-platform (Linux, MacOS, Windows), operated via command-line with commands like merge, pull, add, commit, and rebase.

#### Uses of Git for Projects
Git enhances efficiency with plain text files by efficiently storing incremental changes. It's not recommended for binaries due to size increases; small, static binaries (e.g., logos) are exceptions. Binaries should be stored in a CDN (Content Delivery Network) rather than in Git repositories.

#### Git Stash Usage
Git stash allows temporarily storing changes without committing them, useful for switching contexts or saving work in progress.

#### Features of Git
Git facilitates organized and collaborative software development with features including:
- **Version Control:** Tracks file changes for easy rollback.
- **Branching:** Allows creating branches for parallel development.
- **Collaboration:** Enables multiple contributors to work simultaneously.
- **Security:** Detects file changes and ensures integrity with staged, modified, and committed states.
- **Flexibility:** Operates locally with minimal external dependencies.
- **Commands:** Simple command syntax, accessible for beginners in programming.

#### Version Control Systems (VCS)
VCS records changes to files over time, managing project history, comparing changes, identifying contributors, and enabling rollbacks.

#### Git vs. GitHub
GitHub is a collaborative platform using Git for version control. It hosts computer program source code, acts as a social network for developers, and serves as a portfolio. GitHub offers free public repository hosting and paid private options.

#### GitHub Features

- **Free Project Hosting:** Public repositories available at no cost.
- **Project Sharing:** Easy sharing of projects.
- **Collaboration:** Enables collaboration and contribution.
- **Error Reduction:** Enhances maintenance, environment management, and error detection.
- **Teamwork:** Ideal for team projects, integrating Git's version control benefits with additional project management tools.

## 3. Installing Git on Linux

`apt-get` is a command line interface for retrieval of packages and information about them from authenticated sources and for installation, upgrade and removal of packages together with their dependencies.

```sh
andrewbavuels@the-Legionnaire:~/git_github$ apt-get
```
**For Development Best Practices:**

`sudo apt-get update` before installing anything. This will update your system for new features to install. **Sudo** stands for **Super User DO.** It is used to run commands as an administrator (without restrictions).
```sh
andrewbavuels@the-Legionnaire:~/git_github$ sudo apt-get update
andrewbavuels@the-Legionnaire:~/git_github$ apt-get
```
`sudo apt-get update` upgrade all the currently installed packages to the newest versions available based on the repositories configured in your system.
```sh
andrewbavuels@the-Legionnaire:~/git_github$ sudo apt-get upgrade
```
**Now we are going to install Git:**

`sudo apt-get install git` installs the Git version control system on your computer.

```sh
andrewbavuels@the-Legionnaire:~/git_github$ sudo apt-get install git
```
**Let's verify that Git is installed and check which version is installed:**

```sh
andrewbavuels@the-Legionnaire:~/git_github$ git --version
git version 2.25.1
```

