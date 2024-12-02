# Git and GitHub for Project Management

_"To put you in context, I'm working on a side project that I haven't uploaded to GitHub (until this moment). So I'm leaving the folder wherever I am and going to the folder of the project I want to upload."_

![virtual_envs_repo](https://github.com/user-attachments/assets/ce774a23-3059-4573-bc28-496de73228be)

## *Part I: Git and Version Control Fundamentals*

### **1. Initial Git Setup: init and config**

This section introduces you to setting up Git for your project and configuring it to use the default branch `main` and your personal information.

- `git --version`: To check if Git is installed on your system by running the following command:

```sh
andrewbavuels@the-Legionnaire:~/git_github$ git --version
git version 2.34.1
```
This shows the version of Git installed on your system.

- **Navigate to your project folder:** Move to the directory where your project is stored:

```sh
andrewbavuels@the-Legionnaire:~/git_github$ cd ..
andrewbavuels@the-Legionnaire:~$ cd virtual_envs/
andrewbavuels@the-Legionnaire:~/virtual_envs$ ls
Content.docx  README.md  conda-cheatsheet.pdf  conda-cheatsheet.pdf:Zone.Identifier  pilot_env
```
Here, you're entering the folder where your project files are located.

To start tracking changes in a project,  initialize a Git repository using `git init`:

- `git init`: Initializes a Git repository in the current folder.
- `git config --global init.defaultBranch main`: Sets the default branch name to `main`.

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git init
Initialized empty Git repository in /home/andrewbavuels/virtual_envs/.git/
```

Let's set the default branch **from master to main:**

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git config --global init.defaultBranch main

andrewbavuels@the-Legionnaire:~/virtual_envs$ git branch -m main
```
There are too many commands to memorize. So how do we know which commands we will need and how to read them?

- `git --help`: Lists available commands and options for Git.

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git --help
```

**Git Configuration Commands:** Include commands for setting up username, email, and default branch. To configure my user for all my repositories with the main branch, we execute the following code:

- `git config --global user.name "<username>"`
- `git config --global user.email "<email>"`

```sh
andrew.bavuels@gmail.com
andrewbavuels@the-Legionnaire:~/virtual_envs$ git config --global user.name "Andrew Bavuels"

andrewbavuels@the-Legionnaire:~/virtual_envs$ git config --global user.email "andrew.bavuels@gmail.com"
```
To display all current Git configurations on your system, including global, local, and system settings, do the following:

- `git config --list`: Displays the current configuration settings for Git.

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git config --list
...
```

[GIT CHEAT SHEET](https://education.github.com/git-cheat-sheet-education.pdf)

### **2. Basic Git Commands: add, commit and log**

- `ls -a`: lists all files in the current directory, including hidden files (those that begin with a dot, such as .git):

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ ls -a

.   .git          README.md             conda-cheatsheet.pdf:Zone.Identifier  testing.txt
..  Content.docx  conda-cheatsheet.pdf  pilot_env
```
The folder `.git` is a hidden directory where Git stores all the version control information, such as commit history, configurations, and branch data.

- `git status`: shows the state of your working directory. It will tell you if you have untracked files or changes that need to be committed:

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Content.docx
        README.md
        conda-cheatsheet.pdf
        conda-cheatsheet.pdf:Zone.Identifier
        pilot_env/
        testing.txt
```

**Untracked files** are those that Git is not currently tracking. You need to add them to the staging area with `git add` before you can commit them.

- `git add .`: stages files, preparing them for the next commit. To stage all untracked files:

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git add .
```
The `.` after `git add` stages all files in the directory, including new files and modified files. 

In this case, I don't need to stage them all, so I'll remove them by using the command `git rm -r .`

- `git rm -r .`: If you accidentally added files you don’t want to commit, you can use this command to untrack and delete them:

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git rm -r .
```
This removes the files from both the staging area and the working directory.

- `git rm -r --cached .`: Removes all staged files but keep them in the working directory (they’ll no longer be tracked by Git):

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git rm -r --cached .
```
Use this command if you want to stop tracking files without deleting them from your local machine.

### Kind Reminder:
Always use `git status` to check the state of your repository before and after adding or committing files. This command helps you track:

- **Untracked files:** Files that are not yet added to the staging area.
- **Changes to be committed:** Files that are staged and ready to be committed.
- **Unstaged changes:** Files that have been modified but not yet staged.

By regularly using `git status`, you ensure you are always aware of which files are being tracked and which changes are staged for the next commit.

_Let's keep going:_

- `git add <file>`: Stage files that you want to commit (e.g., git add testing.txt).

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git add testing.txt
andrewbavuels@the-Legionnaire:~/virtual_envs$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   testing.txt
...
```
- `git commit -m "<message>"`: Commit the staged files with a descriptive message (e.g., git commit -m "new file testing.txt").

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git commit -m "new file testing.txt"
Auto packing the repository in background for optimum performance.
See "git help gc" for manual housekeeping.
[main (root-commit) 0bd688c] new file testing.txt
 1 file changed, 1 insertion(+)
 create mode 100644 testing.txt
 ```
```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git status
On branch main
Untracked files:
...
```
Now I'm going to create a new empty file called `testing_2.txt` and repeat the previous steps:

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ touch testing_2.txt
```
- After creating the file, always use `git status` to check the state of your repository. It will show the file as untracked:

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Content.docx
        README.md
        conda-cheatsheet.pdf
        conda-cheatsheet.pdf:Zone.Identifier
        pilot_env/
        testing_2.txt
```

- To track the new file, use `git add testing_2.txt` to move the file to the staging area, preparing it for commit:

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git add testing_2.txt
```
- Again, use `git status` to confirm the file has been staged. Once the file is staged, commit it with:

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git commit -m "second file created as testing_2.txt"
```
...and then `git status` once more.

- `git log`: To view the commit history and confirm your recent commit:

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git log
commit cfe574c203d374f238986661f5534b5a814ead0e (HEAD -> main)
Author: Andrew Bavuels <andrew.bavuels@gmail.com>
Date:   Fri Nov 29 13:24:53 2024 +0100

    second file created as testing_2.txt

commit 0bd688cb463fc0954e5c6202ebfe893f4d009c4a
Author: Andrew Bavuels <andrew.bavuels@gmail.com>
Date:   Fri Nov 29 13:02:47 2024 +0100

    new file testing.txt
andrewbavuels@the-Legionnaire:~/virtual_envs$
```

### **3. Branches and Merging Changes: branch, merge, switch and checkout**

- `git branch`: Displays the list of branches. The asterisk (*) indicates the current branch:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git branch
    * main
    ```

- `git checkout <branch-name>`: Switch to the `main` branch:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git checkout main
    Switched to branch 'main'
    ```

- `git switch <branch-name>`: Switch to the `virtual_envs` branch:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git switch virtual_envs
    Switched to branch 'virtual_envs'
    ```

- Switch back to `main` branch:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git switch main
    Switched to branch 'main'
    ```

- `git merge <branch-name>`: Merge the `virtual_envs` branch into `main`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git merge virtual_envs
    Updating cfe574c..d06a822
    Fast-forward
    testing_virtual_envs.txt | 0
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 testing_virtual_envs.txt
    ```

- Check branches: List branches to confirm the merge:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git branch
    * main
      virtual_envs
    ```

- `git log`: View the commit history, confirming that the merge has been recorded:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git log
    commit d06a82266d962381b146f3c0f60faf65a982fe59 (HEAD -> main, virtual_envs)
    Author: Andrew Bavuels <andrew.bavuels@gmail.com>
    Date:   Fri Nov 29 14:29:51 2024 +0100

        new file for virtual envs testings

    commit cfe574c203d374f238986661f5534b5a814ead0e
    Author: Andrew Bavuels <andrew.bavuels@gmail.com>
    Date:   Fri Nov 29 13:24:53 2024 +0100

        second file created as testing_2.txt

    commit 0bd688cb463fc0954e5c6202ebfe893f4d009c4a
    Author: Andrew Bavuels <andrew.bavuels@gmail.com>
    Date:   Fri Nov 29 13:02:47 2024 +0100

        new file testing.txt
    ```

- `git branch -D <branch-name>`: After merging, delete the `virtual_envs` branch:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git branch -D virtual_envs
    Deleted branch virtual_envs (was d06a822).
    ```

### **4. Going Back in Time in Git: reset and revert**

In this section, we demonstrate how to use the `git reset` and `git revert` commands to undo changes in your Git history.

- Reverting a Commit with `git revert`: To demonstrate git revert, we start by viewing the commit log:

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git log
commit d06a82266d962381b146f3c0f60faf65a982fe59 (HEAD -> main)
Author: Andrew Bavuels <andrew.bavuels@gmail.com>
Date:   Fri Nov 29 14:29:51 2024 +0100
    new file for virtual envs testings

commit cfe574c203d374f238986661f5534b5a814ead0e
Author: Andrew Bavuels <andrew.bavuels@gmail.com>
Date:   Fri Nov 29 13:24:53 2024 +0100
    second file created as testing_2.txt

commit 0bd688cb463fc0954e5c6202ebfe893f4d009c4a
Author: Andrew Bavuels <andrew.bavuels@gmail.com>
Date:   Fri Nov 29 13:02:47 2024 +0100
    new file testing.txt
```

Next, a new file `error_file.txt` is added, committed, and logged:

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git add error_file.txt
andrewbavuels@the-Legionnaire:~/virtual_envs$ git commit -m "new file created for error simulation"
[main 80918e0] new file created for error simulation
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 error_file.txt
```

To revert this commit, we use the `git revert` command, which creates a new commit that undoes the changes made in the original commit:

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git revert 80918e020620025d82a15188517c5cd77fa6a124
```

After confirming, the revert is committed:

```sh
[main 626c27f] Revert "new file created for error simulation"
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 error_file.txt
```

- Resetting to a Previous Commit with `git reset`: To demonstrate git reset, a new file `reset_test.txt` is created and committed:

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git add reset_test.txt
andrewbavuels@the-Legionnaire:~/virtual_envs$ git commit -m "new file for reset testing"
[main f9c398a] new file for reset testing
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 reset_test.txt
 ```

Now, the `git reset --hard` command is used to reset the repository to a specific commit:

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git reset --hard cfe574c203d374f238986661f5534b5a814ead0e
HEAD is now at cfe574c second file created as testing_2.txt
```
Finally, the commit log shows that the repository has been reset to the commit where `testing_2.txt` was created:

```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git log
commit cfe574c203d374f238986661f5534b5a814ead0e (HEAD -> main)
Author: Andrew Bavuels <andrew.bavuels@gmail.com>
Date:   Fri Nov 29 13:24:53 2024 +0100
    second file created as testing_2.txt

commit 0bd688cb463fc0954e5c6202ebfe893f4d009c4a
Author: Andrew Bavuels <andrew.bavuels@gmail.com>
Date:   Fri Nov 29 13:02:47 2024 +0100
    new file testing.txt
```

### Types of git reset:

- --hard: Resets commit history, staging area, and working directory.
Use: Completely discards changes.

- --soft: Resets commit history but keeps changes staged.
Use: Keep changes ready for recommitting.

- --mixed (default): Resets commit history and unstages changes but keeps them in the working directory.
Use: Unstage changes but keep them locally.

### Kind Reminder:
- Use `revert` to safely undo changes while preserving project history.
- Use `reset` to modify or remove commits locally, with the option to keep or discard changes in the working directory.

### **5. Version Management: Tag and Checkout**

### Creating and Viewing Tags

- `git tag -a <tag-name> -m "<message>"`: Create an annotated tag at the current commit with a message. For example, creating tag `v1.0`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git tag -a v1.0 -m "my first version"
    ```

- `git tag`: List all tags in the repository:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git tag
    v1.0
    ```

- `git show <tag-name>`: View the commit associated with the tag. For example, inspecting `v1.0`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git show v1.0
    ```

- `git tag -d <tag-name>`: Delete a tag from the local repository. For example, deleting tag `v1.0`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git tag -d v1.0
    ```

### Switching Between Commits and Branches

- `git tag <tag-name>`: Create a new tag at any commit. For example, creating tag `v2.0`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git tag v2.0
    ```

- `git checkout <commit-hash>`: Checkout a specific commit to enter a detached HEAD state. For example, checking out a commit:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git checkout 0bd688cb463fc0954e5c6202ebfe893f4d009c4a
    ```

- `touch <file-name>`: Create a new file while in the detached HEAD state. For example, creating `testing3.txt`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ touch testing3.txt
    ```

- `git checkout <branch-name>`: Return to a branch from the detached HEAD state. For example, returning to the `main` branch:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git checkout main
    ```

### Git Branching

- `git branch`: List branches and show the current branch. For example, viewing the active branch:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git branch
    * main
    ```

### Key Takeaways:
- **Tagging**: Use `git tag` to mark important commits, such as version releases.
- **Detached HEAD**: Checkout commits directly to explore or experiment, but be aware that changes made here are not tied to any branch unless a new branch is created.
- **Switching Back**: Use `git checkout <branch>` to return to a branch after exploring a specific commit.

### **6. How to Resolve Branch Conflicts in Git**

### Step-by-Step Process

- `git branch`: View the current branch. For example, checking the active branch:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git branch
    * main
    ```

- `nano <file-name>`: Create and edit a file in the current branch. For example, creating `conflict.txt`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ nano conflict.txt
    ```

- `git add <file-name>`: Stage the new file for commit. For example, staging `conflict.txt`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git add conflict.txt
    ```

- `git commit -m "<commit-message>"`: Commit the file to the current branch. For example, committing the file:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git commit -m "conflict file created"
    [main 27dfe92] conflict file created
    1 file changed, 1 insertion(+)
    create mode 100644 conflict.txt
    ```

- `git checkout -b <branch-name>`: Create and switch to a new branch. For example, creating `developer` branch:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git checkout -b developer
    Switched to a new branch 'developer'
    ```

- `nano <file-name>`: Edit the same file in the new branch. For example, editing `conflict.txt`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ nano conflict.txt
    ```

    Example content in `conflict.txt`:
    ```
    original line
    changes from the dev branch
    ```

- `git add <file-name>`: Stage the changes in the new branch. For example, staging the edited `conflict.txt`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git add conflict.txt
    ```

- `git commit -m "<commit-message>"`: Commit the changes in the new branch. For example, committing the changes in the `developer` branch:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git commit -m "New changes from dev"
    [developer 502bb73] New changes from dev
    1 file changed, 2 insertions(+)
    ```

- `git checkout <branch-name>`: Switch back to the main branch. For example, switching to `main`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git checkout main
    Switched to branch 'main'
    ```

- `nano <file-name>`: Modify the file in the main branch. For example, editing `conflict.txt`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ nano conflict.txt
    ```

    Example content in `conflict.txt`:
    ```
    original line
    second change from main
    ```

- `git add <file-name>`: Stage the changes in the main branch. For example, staging the edited `conflict.txt`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git add conflict.txt
    ```

- `git commit -m "<commit-message>"`: Commit the changes in the main branch. For example, committing the changes in the `main` branch:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git commit -m "changes to conflict"
    [main 20b54b3] changes to conflict
    1 file changed, 2 insertions(+)
    ```

- `git merge <branch-name>`: Attempt to merge the `developer` branch into `main`. For example, merging `developer`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git merge developer
    Auto-merging conflict.txt
    CONFLICT (content): Merge conflict in conflict.txt
    Automatic merge failed; fix conflicts and then commit the result.
    ```

- `nano <file-name>`: Resolve the conflict manually by editing the file. For example, opening `conflict.txt`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ nano conflict.txt
    ```

    The file will contain conflict markers:
    ```
    <<<<<<< HEAD
    second change from main
    =======
    changes from the dev branch
    >>>>>>> developer
    ```

    After resolving the conflict, the file should look like this:
    ```
    original line
    second change from main
    changes from the dev branch
    ```

- `git add <file-name>`: Stage the resolved file. For example, staging `conflict.txt`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git add conflict.txt
    ```

- `git commit -m "<commit-message>"`: Commit the merge resolution. For example, committing the resolution:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git commit -m "new changes"
    [main 6a1db20] new changes
    ```

- `git merge <branch-name>`: Ensure the branches are up to date after the merge. For example, checking if `developer` is merged:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git merge developer
    Already up to date.
    ```

---

### Key Takeaways:
- **Conflicts** occur when changes in different branches overlap, and Git cannot automatically merge them.
- **Manual Resolution**: Edit the conflicting files, remove conflict markers, and then stage and commit the changes.
- **Finalizing Merge**: Always commit after resolving conflicts to complete the merge process.

## *Part II - GitHub Fundamentals*

### **7. Managing Repositories on GitHub**

If you already have a **README.md file in your local folder created using Visual Studio Code (VSC)** and want to upload it to a remote repository on GitHub, the best option is to use the second alternative: "push an existing repository from the command line", since you already have an existing repository:

### Uploading an Existing Repository to GitHub

- `git init`: Initialize a Git repository in your local folder. If you haven't already initialized the repository, run this command:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git init
    Reinitialized existing Git repository in /home/andrewbavuels/virtual_envs/.git/
    ```

- `git add README.md`: Stage the `README.md` file for commit:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git add README.md
    ```

- `git commit -m "<message>"`: Commit the staged changes with a message. For example, committing the `README.md`:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git commit -m "Add initial README.md"
    ```

- `git remote add origin <repository-url>`: Link the local repository to a remote repository on GitHub. Use either SSH or HTTPS. For example:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git remote add origin git@github.com:AndrewBavuels/Virtual-Environments-with-Anaconda-and-Jupyter.git
    ```

- `git branch -M main`: Rename the current branch to `main` (if not already set):

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git branch -M main
    ```

- `git push -u origin main`: Push your changes to the remote repository on GitHub:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git push -u origin main
    Enumerating objects: 8787, done.
    Counting objects: 100% (8787/8787), done.
    Delta compression using up to 16 threads
    Compressing objects: 100% (8726/8726), done.
    Writing objects: 100% (8787/8787), 64.46 MiB | 3.65 MiB/s, done.
    Total 8787 (delta 846), reused 3 (delta 0), pack-reused 0
    remote: Resolving deltas: 100% (846/846), done.
    To github.com:AndrewBavuels/Virtual-Environments-with-Anaconda-and-Jupyter.git
     * [new branch]      main -> main
    Branch 'main' set up to track remote branch 'main' from 'origin'.
    ```

### Key Takeaways:
- **Efficient Workflow**: This method is ideal when you already have local files and want to sync them with GitHub.
- **Remote Link**: Use `git remote add origin` to connect your local repository to a remote one.
- **Branch Management**: Ensure your main branch is properly set with `git branch -M main` and push to GitHub with `git push`.
- **Authentication**: Choose between SSH and HTTPS for repository URL depending on your setup.

### **8. How to Setup SSH for GitHub: Step-by-Step Guide**

### Generating a New SSH Key Pair

- `ssh-keygen -t ed25519 -C "<your-email@example.com>"`: This command generates a new SSH key pair using the ED25519 algorithm. Replace `<your-email@example.com>` with your GitHub email address. For example:

    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ ssh-keygen -t ed25519 -C "andrew.bavuels@gmail.com"
    Generating public/private ed25519 key pair.
    Enter file in which to save the key (/home/andrewbavuels/.ssh/id_ed25519):
    /home/andrewbavuels/.ssh/id_ed25519 already exists.
    Overwrite (y/n)? y
    Enter passphrase (empty for no passphrase):
    Enter same passphrase again:
    Your identification has been saved in /home/andrewbavuels/.ssh/id_ed25519
    Your public key has been saved in /home/andrewbavuels/.ssh/id_ed25519.pub
    ```

### Adding the SSH Key to the SSH Agent

- `eval "$(ssh-agent -s)"`: Start the SSH agent to manage your keys. For example:

    ```sh
    andrewbavuels@the-Legionnaire:~/.ssh$ eval "$(ssh-agent -s)"
    Agent pid 12943
    ```

- `ssh-add ~/.ssh/id_ed25519`: Add your SSH key to the SSH agent for authentication. For example:

    ```sh
    andrewbavuels@the-Legionnaire:~/.ssh$ ssh-add ~/.ssh/id_ed25519
    Enter passphrase for /home/andrewbavuels/.ssh/id_ed25519:
    Identity added: /home/andrewbavuels/.ssh/id_ed25519 (andrew.bavuels@gmail.com)
    ```

### Copying the Public Key to GitHub

- `nano ~/.ssh/id_ed25519.pub`: Open the public key file in a text editor to copy it. For example:

    ```sh
    andrewbavuels@the-Legionnaire:~/.ssh$ nano id_ed25519.pub
    ```

    Copy the entire contents of the file, which starts with `ssh-ed25519`.

### Adding the SSH Key to GitHub

- Go to GitHub:
  - Navigate to **Settings** > **SSH and GPG keys** > **New SSH key**.
  - Paste the public key you copied and give it a title (e.g., `andrew.bavuels@gmail.com`).
  - Click **Add SSH key** to save it.

### Testing the SSH Connection

- `ssh -T git@github.com`: Test the connection to GitHub using SSH. You should see a success message:

    ```sh
    andrewbavuels@the-Legionnaire:~/.ssh$ ssh -T git@github.com
    Hi AndrewBavuels! You've successfully authenticated, but GitHub does not provide shell access.
    ```
### Key Takeaways:

- **SSH Key Generation**: Use `ssh-keygen` to create a new SSH key pair for secure authentication with GitHub.
- **SSH Agent**: Add your SSH key to the agent to securely authenticate with GitHub without entering your password every time.

### **9. Clone and Fork Repositories**

### Cloning a Repository Using SSH

- `git clone git@github.com:<username>/<repository>.git`: Clone a repository from GitHub using SSH. For example:

    ```sh
    andrewbavuels@the-Legionnaire:~$ mkdir datacamp_clone
    andrewbavuels@the-Legionnaire:~$ cd datacamp_clone/
    andrewbavuels@the-Legionnaire:~/datacamp_clone$ git clone git@github.com:datacamp/datacamp-light.git
    Cloning into 'datacamp-light'...
    remote: Enumerating objects: 1599, done.
    remote: Counting objects: 100% (113/113), done.
    remote: Compressing objects: 100% (67/67), done.
    remote: Total 1599 (delta 71), reused 73 (delta 46), pack-reused 1486 (from 1)
    Receiving objects: 100% (1599/1599), 1.67 MiB | 2.66 MiB/s, done.
    Resolving deltas: 100% (931/931), done.
    ```

### Forking a Repository

- Forking a repository allows you to create a copy of an existing repository under your GitHub account. This lets you freely experiment with changes without affecting the original project.

- To fork a repository:
  1. Navigate to the repository's page on GitHub.
  2. Click on the **Fork** button in the top-right corner.
  3. Select where you want to fork the repository (your personal GitHub account or an organization).
  4. The repository is now copied to your GitHub account, and you can begin working on it.

- Example: Forking the `shinybones` repository:

    ```sh
    andrewbavuels@the-Legionnaire:~/datacamp_clone$ git clone git@github.com:AndrewBavuels/shinybones.git
    Cloning into 'shinybones'...
    remote: Enumerating objects: 774, done.
    remote: Counting objects: 100% (4/4), done.
    remote: Compressing objects: 100% (4/4), done.
    remote: Total 774 (delta 0), reused 4 (delta 0), pack-reused 770 (from 1)
    Receiving objects: 100% (774/774), 283.95 KiB | 690.00 KiB/s, done.
    Resolving deltas: 100% (440/440), done.
    ```

You now have a fork of the `shinybones` repository under your GitHub account and can make changes independently of the original project.

### Key Takeaways:

- **Cloning with SSH**: Once the SSH key is set up, you can clone repositories from GitHub securely using SSH.

- **Difference between Cloning the Repo and Forking + Cloning the Repo**:

  - **Cloning a Repository**: When you clone a repository, you create a local copy of that repository on your computer. Any changes you make are local to your machine until you push them back to the remote repository (if you have write access). This is typically used for contributing to public repositories or when you need a working copy of a project.

  - **Forking + Cloning a Repository**: Forking a repository creates a copy of the repository under your own GitHub account. This is typically used when you want to contribute to a project but don't have write access to the original repository. After forking the repository, you clone it to your local machine to work on the project. The forked repository allows you to freely experiment with changes, and later you can submit a pull request to the original repository to propose your changes.

### **10. Working with Remote Repositories: Push, Pull, and Fetch**

### Pushing Changes from Local Repository to GitHub

1. Check your branch:
    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git branch
    * main
    ```

2. Edit files locally (e.g., in Visual Studio Code) and commit changes from the VSC source control panel.

3. Verify the commit:
    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git status
    On branch main
    Your branch is ahead of 'origin/main' by 1 commit.
      (use "git push" to publish your local commits)
    ```

4. Push changes to GitHub:
    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git push -u origin main
    Enter passphrase for key '/home/andrewbavuels/.ssh/id_ed25519':
    Enumerating objects: 22, done.
    Counting objects: 100% (22/22), done.
    Delta compression using up to 16 threads
    Compressing objects: 100% (19/19), done.
    Writing objects: 100% (19/19), 2.16 MiB | 1.64 MiB/s, done.
    Total 19 (delta 2), reused 17 (delta 0), pack-reused 0
    remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
    To github.com:AndrewBavuels/Virtual-Environments-with-Anaconda-and-Jupyter.git
       c4654dd..6de57bd  main -> main
    Branch 'main' set up to track remote branch 'main' from 'origin'.
    ```

### Pulling Changes from GitHub to Local Repository

1. Edit a file directly on GitHub, commit the changes, and confirm they don’t appear locally.

2. Pull the updates:
    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git pull
    Enter passphrase for key '/home/andrewbavuels/.ssh/id_ed25519':
    remote: Enumerating objects: 5, done.
    remote: Counting objects: 100% (5/5), done.
    remote: Compressing objects: 100% (3/3), done.
    remote: Total 3 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
    Unpacking objects: 100% (3/3), 982 bytes | 196.00 KiB/s, done.
    From github.com:AndrewBavuels/Virtual-Environments-with-Anaconda-and-Jupyter
       6de57bd..17ceb80  main       -> origin/main
    Updating 6de57bd..17ceb80
    Fast-forward
     README.md | 6 +++++-
     1 file changed, 5 insertions(+), 1 deletion(-)
    ```

3. Verify that the changes appear locally.

### Fetching Updates from GitHub Without Merging

1. Make additional changes on GitHub (e.g., another README edit) and commit them.

2. Fetch updates from GitHub:
    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git fetch origin
    Enter passphrase for key '/home/andrewbavuels/.ssh/id_ed25519':
    remote: Enumerating objects: 5, done.
    remote: Counting objects: 100% (5/5), done.
    remote: Compressing objects: 100% (3/3), done.
    remote: Total 3 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
    Unpacking objects: 100% (3/3), 966 bytes | 966.00 KiB/s, done.
    From github.com:AndrewBavuels/Virtual-Environments-with-Anaconda-and-Jupyter
       17ceb80..ca79316  main       -> origin/main
    ```

3. Compare local and remote branches:
    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git log main..origin/main
    commit ca79316af7bce801edbc76588609160213c552ed (origin/main)
    Author: Andres Buelvas Diago <52129944+AndrewBavuels@users.noreply.github.com>
    Date:   Sun Dec 1 17:20:53 2024 +0100

        Learning git fetch
    ```

4. Merge the fetched changes:
    ```sh
    andrewbavuels@the-Legionnaire:~/virtual_envs$ git merge origin/main
    Updating 17ceb80..ca79316
    Fast-forward
     README.md | 2 ++
     1 file changed, 2 insertions(+)
    ```

### Key Takeaways:

1. **Push Updates to Remote Repository**  
   - Use `git push` to send committed changes from the local repository to the remote repository.
   - Add the `-u origin <branch>` flag to set up tracking for the branch.

2. **Pull Updates from Remote Repository**  
   - Use `git pull` to fetch and merge updates from the remote branch into the local branch.  
   - Automatically synchronizes the local branch with the latest remote changes.

3. **Fetch Without Merge**  
   - Use `git fetch` to download changes from the remote repository without merging them into the local branch.  
   - Use `git log main..origin/main` to inspect new changes before merging.

4. **Merge Changes After Fetch**  
   - Use `git merge origin/<branch>` to integrate fetched updates into the current branch.

5. **Track File Changes and Status**  
   - `git status` reveals untracked, modified, and committed changes.
   - Committing frequently keeps the working tree clean and manageable.

6. **SSH Passphrase**  
   - A passphrase secures your SSH key. You must enter it whenever performing remote operations unless an SSH agent is running.

7. **Resolving Conflicts and Fast-Forwards**  
   - When remote updates are ahead of the local branch, `git pull` or `git merge` ensures the branches are in sync.
   - Fast-forward merges apply changes directly when no diverging commits exist.

8. **Working with Visual Studio Code**  
   - Use the integrated source control feature in VSC for seamless commit management.
   - Terminal commands can be complemented with UI operations for efficiency.

### **11. Pull Requests on GitHub**

### Steps to Create and Merge a Pull Request (PR)

#### 1. Create and Switch to a New Branch
Start by creating a new branch and switching to it:
```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git checkout -b developer_01
Switched to a new branch 'developer_01'
```

#### 2. Make Changes in the Local Branch
Edit files (e.g., `README.md`), then stage and commit your changes:
```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git add README.md
andrewbavuels@the-Lionnaire:~/virtual_envs$ git commit -m "changes from developer_01"
[developer_01 b38c1f4] changes from developer_01
 1 file changed, 2 insertions(+)
```

#### 3. Push the Local Branch to GitHub
Push your branch to GitHub for the first time and set the upstream branch:
```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git push -u origin developer_01
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 16 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 352 bytes | 352.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'developer_01' on GitHub by visiting:
remote:      https://github.com/AndrewBavuels/Virtual-Environments-with-Anaconda-and-Jupyter/pull/new/developer_01
```

#### 4. Create a Pull Request on GitHub
- Visit the link provided in the terminal or go to your GitHub repository.
- Select the branch `developer_01` to create a Pull Request (PR).
- Add details:
    - **Title**: e.g., `Added updates to README.md from developer_01`
    - **Description**: e.g., `Updated the README with new examples and steps.`
- Submit the Pull Request for review.

#### 5. Review and Merge the Pull Request
After reviewing the PR, click **Merge** to integrate the changes into the main branch.

#### 6. Syncing the Local Repository After Merging
Switch back to the main branch:
```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git checkout main
Switched to branch 'main'
```

Pull the merged changes from the remote repository:
```sh
andrewbavuels@the-Legionnaire:~/virtual_envs$ git pull origin main
Updating b38c1f4..df4c2e9
Fast-forward
 README.md | 2 ++
 1 file changed, 2 insertions(+)
```

### Key Takeaways:
1. **Branch Management**  
   - Use `git checkout -b <branch-name>` to create and switch to a new branch.
   - Push with `git push -u origin <branch-name>` to set the upstream branch.

2. **Collaboration via Pull Requests**  
   - Always create PRs for changes to ensure review and maintain a clean history.
   - Add detailed titles and descriptions for context to facilitate the review process.

3. **Synchronize After Merging**  
   - Switch to `main` and pull the latest changes using `git pull origin main` to ensure local and remote branches are aligned.

4. **Inspect and Manage Changes**  
   - Use `git status` and `git log` to review changes and branch differences before and after merging.
