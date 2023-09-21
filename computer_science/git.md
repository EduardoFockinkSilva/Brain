# Git

![Git Logo](https://git-scm.com/images/logo@2x.png)

## Description

Git is a Distributed Version Control System (DVCS) engineered for efficiency and speed, accommodating everything from small to extensive projects. Created in 2005 by Linus Torvalds, Git provides non-linear, distributed workflows. It maintains full history, ensuring cryptographic integrity via SHA-1 hashes.

[Wikipedia](https://en.wikipedia.org/wiki/Git)

[Official Git Website](http://git-scm.com/)

## Installation  
### By Terminal

#### Linux

To install Git on a Debian-based Linux distribution like Ubuntu, execute the following command:
```bash
sudo apt update
sudo apt install git
```

#### Windows

To install Git on Windows, you can use the Windows Package Manager (`winget`). Open PowerShell as an administrator and run:
```powershell
winget install Git
```

#### Mac

To install Git on macOS, you can use the Homebrew package manager. Open Terminal and execute:
```bash
brew install git
```

### By Download

You can also manually download and install Git for your specific operating system.

[Download Link](https://git-scm.com/downloads)





## Initial Configuration
### Setting User and Email

Before you can start committing changes to a Git repository, it's crucial to configure your user name and email address. These details will be associated with any commits you make and are important for collaborating with other developers.

To list all the configuration settings, you can use:

```bash
git config --list
```

To set your username and email globally across all repositories on your machine, execute the following commands in your terminal:

```bash
git config --global user.name "your_github_username"
git config --global user.email "your_email@github.com"
```

These settings will be saved in your global Git configuration file, usually located at `~/.gitconfig` on Linux/Mac or `C:\\Users\\<username>\\.gitconfig` on Windows. 

After setting your username and email, it's a good practice to confirm that they have been correctly set. To do that, you can list all the configuration settings again:

```bash
git config --list
```

Look for `user.name` and `user.email` in the list to ensure your configuration changes have taken effect.





## Usage

### Create a Temporary Directory and Navigate Into It

Firstly, navigate to the temporary directory (`temp`) and create a new project directory (`projeto`):

```bash
cd temp
mkdir projct
cd projct
```

### Initialize Git in the Directory

Initialize a new Git repository in the project directory and list the hidden files to confirm `.git` folder's presence:

```bash
git init
ls -la
```

### Create a File in the Directory

Create a file named `doc.txt` with the content "Hello":

```bash
echo "Hello" > doc.txt
ls
cat doc.txt
git status
```

### Add File to the Index (Staging Area)

Add the file `doc.txt` to the Git index, also known as the staging area:

```bash
git add doc.txt
git status
```

### Commit Staged Files

Commit the changes in the staging area to the repository. The options `-a` and `-m` have specific functions:

| Option | Description                                |
|--------|--------------------------------------------|
| `-a`   | Automatically stage files that have been modified and deleted |
| `-m "text"` | Add a commit message |

```bash
git commit -a -m "first commit"
git status
```

The `-a` flag will stage all modified and deleted files, but it does not include new files. The `-m` flag allows you to include a commit message directly from the command line, without opening an editor.

Use `git status` to confirm that the repository is in a clean state after the commit.





## History

### Viewing Commit History

To view the commit history, use the `git log` command. To see the commit history for a specific file (`file_name`), use the `-p` flag:

```bash
git log
git log -p "file_name"
```

## Undo Operations

### Reverting to Last Commit / Discarding Local Changes

Suppose you've made a change to `doc.txt` that you wish to discard:

```bash
echo "World" >> doc.txt
cat doc.txt
git status
git diff
```

To revert the file back to the last committed state:

```bash
git checkout -- doc.txt
git diff
cat doc.txt
```

### Discarding Local File Changes

If you want to discard changes in a specific file (`file_name`), you can use:

```bash
git restore "file_name"
```

### Undoing to a Previous Version

To revert to an older version, you'll first need the commit hash:

```bash
git log
```

View the current state of `doc.txt`:

```bash
cat doc.txt
```

To reset the repository to the state of a previous commit:

```bash
git reset --hard <commit_hash>
cat doc.txt
```

### Removing File from the Index

To remove `doc.txt` from the index:

```bash
git rm doc.txt
```

### Deleting the File

To permanently delete `doc.txt` and commit this change:

```bash
git rm doc.txt
git commit -am "Deleting doc.txt"
git status
```

This section describes a range of commands for managing history and undoing changes, aimed at users with advanced understanding of Git functionalities.





## Branches

### Listing All Branches

To display all available branches, including remote-tracking branches:

```bash
git branch -av
```

### Creating a Branch

To create a new branch named `testing`:

```bash
git branch testing
```

After running `git log`, both branches (`master` and `testing`) will be visible. The HEAD pointer will indicate that you're still on the `master` branch.

```text
(HEAD -> master, testing)
```

### Switching Between Branches

To switch to the `testing` branch:

```bash
git checkout testing
```

Upon running `git log`, the HEAD will now point to the `testing` branch:

```text
(HEAD -> testing, master)
```

Create a new file `code.c` and commit it:

```bash
echo "code" >> code.c
git add code.c
git commit -m "Added code.c"
git log
```

### Switching Back to the `master` Branch

To return to the `master` branch:

```bash
git checkout master
```





## Merging

### Merging a Branch into `master`

Ensure you're on the `master` branch:

```bash
git checkout master
```

Then merge changes from the `testing` branch:

```bash
git merge testing
```





## Ignoring Files in Commits

To ignore certain files or patterns from being committed, create a `.gitignore` file in the repository root. List the files or patterns to ignore, one per line.

For instance, to ignore all `.log` files:

```text
*.log
```

Remember to commit the `.gitignore` file so that the rules are shared with other collaborators.

