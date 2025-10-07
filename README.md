# Introduction to Version Control with Git

---

## 1. What Is a Version?

A version refers to the specific state of a file at a certain point in time. It includes:

- Content: The actual data or code inside the file.
- Metadata: Key information like:
  - Author of the file
  - File location
  - File type
  - Last saved timestamp

**Visual aid suggestion**: A diagram showing the same document at three different points in time with labeled metadata.

---

## 2. What Is Version Control?

Version control is a system for managing changes in documents, code, or directories. It's essential for:

- Projects that evolve over time
- Collaborative work across teams

Functions of version control:

- Tracking file changes
- Supporting multiple contributors
- Merging file versions
- Identifying specific versions
- Reverting unwanted changes

**Image suggestion**: A branching timeline showing different contributors making changes to the same file.

---

## 3. Why Version Control Matters?

Without version control:

- Changes can be overwritten
- It’s difficult to track who did what and when
- Collaborating is chaotic

With version control:

- You gain transparency, traceability, and control

**Image suggestion**: Side-by-side comparison — a chaotic manual workflow vs. an organized version-controlled system.

---

## 4. What Is Git?

Git is a popular version control system used especially in software and data projects. Features:

- Open-source  
- Scalable  
- Tracks everything (history is never lost)

**Note**: Git is not the same as GitHub  
- Git is the tool  
- GitHub is a platform for hosting Git repositories

---

## 5. Benefits of Git

- Keeps history safe: Nothing is lost
- Flags conflicting changes
- Syncs work across people and computers

**Visual idea**: Diagram of a team collaborating across devices, with Git syncing everything.

---

## 6. Git and The Shell

Git works in the command line interface (CLI), or "the shell":

- A tool to run commands
- Useful for navigating and editing files


# Important Shell and Git Commands Summary

```bash
pwd
# Prints the current working directory

ls
# Lists files and directories in the current location

cd folder_name
# Changes the current directory to 'folder_name'

nano filename
# Opens 'filename' in the nano text editor

echo "text" > filename
# Creates or overwrites 'filename' with "text"

echo "text" >> filename
# Appends "text" to the end of 'filename'


git --version
# Displays the installed Git version

git init
# Initializes a new Git repository in the current directory

git add filename
# Stages the specified file for the next commit

git add .
# Stages all modified and new files in the current directory

git commit -m "message"
# Commits staged changes with a descriptive message

git status
# Shows the status of working directory and staged changes

git diff filename
# Shows differences between the working directory and the last commit for 'filename' (comparing unstage file)

git diff -r HEAD filename
# Shows differences between the staged version of 'filename' and the last commit

git diff -r HEAD
# Shows differences between all staged files and the last commit
```
---

## Commit Structure and History

```bash
git log
# Shows the full commit history with metadata (author, date, message)
```

**Tips**:
- Press `space` to scroll through the log, `q` to quit.
- Useful to identify previous changes or retrieve commit hashes.

```bash
git show <commit_hash>
# Displays the full details and changes of a specific commit
```

**Tips**:
- Only the first 6–8 characters of the hash are usually needed.
- Helps verify the contents and impact of a specific commit.

---

## Working with Commits and HEAD

```bash
git diff -r HEAD
# Compares staged files to the latest commit (HEAD)
```

```bash
git show HEAD~n
# Shows the changes in a previous commit, n steps back from HEAD
```

```bash
git diff <commit1> <commit2>
# Compares changes between two specific commits
```

```bash
git diff HEAD~3 HEAD~2
# Compares the 4th and 3rd most recent commits
```

```bash
git annotate <file>
# Shows line-by-line history of a file with the author and commit for each line
```

**Tips**:
- Use `HEAD~1`, `HEAD~2`, etc., to navigate older commits.
- Avoid spaces before or after the tilde (`~`).
- `git annotate` is useful for auditing or blame tracking.

---

## Staging, Unstaging, and Committing

```bash
git add <file>
# Stages the specified file for the next commit
```

```bash
git add .
# Stages all modified and new files in the current directory
```

```bash
git commit -m "Your commit message"
# Commits all staged changes with a descriptive message
```

```bash
git reset HEAD <file>
# Unstages a specific file but keeps the changes in the working directory
```

```bash
git reset HEAD
# Unstages all staged files
```

**Tips**:
- Use `reset` if you accidentally staged the wrong file.
- Commit messages should be short and meaningful.

---

## Undoing Changes (Unstaged)

```bash
git checkout -- <file>
# Reverts the specified unstaged file to the last committed version
```

```bash
git checkout .
# Reverts all unstaged changes in the current directory and subdirectories
```

**Tips**:
- These actions are irreversible. All unsaved work will be lost.
- Run from the root of the repo if you want to affect the entire project.

---

## Restoring Past States

```bash
git checkout <commit_hash> <file>
# Restores a specific file to its version in a particular commit
```

```bash
git checkout HEAD~1 <file>
# Restores the file from the previous commit
```

```bash
git checkout <commit_hash>
# Restores the entire repository to the state of that commit
```

**Tips**:
- Use this to test older versions or reverse a change.
- Do not make commits while in a detached HEAD state unless intentional.

---

## Customizing git log Output

```bash
git log -3
# Shows the last 3 commits
```

```bash
git log -3 <file>
# Shows the last 3 commits affecting a specific file
```

```bash
git log --since='Apr 2 2022'
# Shows commits made since April 2, 2022
```

```bash
git log --since='Apr 2 2022' --until='Apr 11 2022'
# Shows commits made between April 2 and April 11, 2022
```

**Tips**:
- Great for narrowing down commit history in large projects.
- Use for audits, rollback, or investigating issues.

---

## Cleaning the Working Directory

```bash
git clean -n
# Previews untracked files that would be deleted
```

```bash
git clean -f
# Deletes untracked files (cannot be undone)
```

**Tips**:
- Always use `-n` first to see what will be removed.
- Use carefully to avoid accidental data loss.

---

## Configuring Git

---

## Configuring Git Settings

```bash
git config --list
# Lists all current Git configuration settings at every level
```

```bash
git config --global user.email "you@example.com"
# Sets the global email for Git commits
```

```bash
git config --global user.name "Your Name"
# Sets the global username for Git commits
```

**Tips**:
- Use `--local`, `--global`, or `--system` depending on the scope.
- Use quotes if the name contains spaces.
- Configuration avoids repeatedly entering identity info.

---

## Git Configuration Levels

- `--local`: For a specific repository
- `--global`: Applies to all repositories for the current user
- `--system`: Applies to all users on the system

---

## Creating Git Aliases

```bash
git config --global alias.ci "commit -m"
# Creates a shortcut 'ci' for 'git commit -m'
```

```bash
git config --global alias.unstage "reset HEAD"
# Creates an alias 'unstage' to unstage files easily
```

**Tips**:
- Use quotes to preserve spacing and characters.
- Aliases save time and reduce repetitive typing.
- Use `git config --global --list` to see all defined aliases.

---

## Ignoring Files

```bash
nano .gitignore
# Opens the .gitignore file to specify untracked files to be ignored
```

**Tips**:
- Use wildcards like `*` to ignore patterns (e.g., `*.log`)
- Common uses: ignore `.env`, API keys, system files, compiled assets

---

## Branch Management

```bash
git branch
# Lists all local branches and highlights the current branch
```

```bash
git checkout -b new_branch
# Creates and switches to a new branch called 'new_branch'
```

```bash
git checkout existing_branch
# Switches to an already existing branch
```

**Tips**:
- Each branch can represent a separate feature, fix, or task.
- Prevents mixing unrelated work and reduces merge conflicts.

---

## Comparing Branches

```bash
git diff branch1 branch2
# Shows the differences between two branches
```

**Tip**:
- Useful before merging to understand the changes involved.

---

## Merging Branches

```bash
git merge source destination
# Merges 'source' branch into 'destination' branch
```

Example:

```bash
git merge summary-statistics main
# Merges summary-statistics branch into main
```

**Tips**:
- Always commit or stash changes before merging.
- Only merge completed and tested work into `main`.

---

## Resolving Merge Conflicts

```bash
git merge conflicting_branch
# Attempts to merge; may result in a conflict
```

```bash
nano conflicted_file
# Opens file for manual conflict resolution
```

```bash
git add resolved_file
# Marks conflict as resolved
```

```bash
git commit -m "Resolved conflict in resolved_file"
# Finalizes the merge after resolving conflicts
```

**Tips**:
- Conflicts occur when the same lines are changed in different branches.
- Avoid editing the same file across multiple branches to minimize conflicts.
- Resolve carefully and review the full file before committing.

---

## Conflict Prevention Best Practices

- Use each branch for one task or feature
- Coordinate changes with teammates
- Frequently pull changes from shared branches to stay up-to-date
- Keep `main` clean and functional at all times

---

# Creating Repositories & Working with Remotes

---

## Creating and Initializing Repositories

```bash
git init <directory-name>
# Initializes a new Git repository in a specified folder
```

```bash
cd <directory-name>
# Enters the newly created Git repository directory
```

```bash
git status
# Shows the current state of the working directory and staging area
```

**Tips**:
- Use `git init` inside a project folder to start tracking it with Git.
- Avoid nesting Git repos (i.e., a .git directory inside another .git).

---

## Tracking Files

```bash
git add <file>
# Starts tracking the specified file
```

```bash
git add .
# Adds all files in the current directory to staging
```

```bash
git commit -m "Message"
# Commits staged files with a commit message
```

**Tip**:
- Run `git status` to see what is being tracked or untracked.

---

## Cloning Repositories

```bash
git clone /path/to/local/repo
# Clones a local repository into a new directory
```

```bash
git clone /path/to/local/repo new_repo
# Clones a local repo into a specified new directory
```

```bash
git clone <remote-URL>
# Clones a remote repository (e.g., from GitHub)
```

**Tips**:
- Automatically sets up a remote called `origin`.
- Use for downloading remote projects to your local machine.

---

## Managing Remotes

```bash
git remote
# Lists names of remote repositories connected to your local repo
```

```bash
git remote -v
# Shows the URLs for the remotes (fetch and push)
```

```bash
git remote add <name> <url>
# Adds a new remote connection with a given name
```

**Tips**:
- Remote names (like `origin` or `upstream`) help identify where to push/pull from.
- Use `-v` to verify fetch and push URLs.

---

## Fetching and Pulling from Remotes

```bash
git fetch origin main
# Downloads changes from the remote's main branch but doesn’t merge
```

```bash
git fetch origin <branch-name>
# Fetches changes from a specific branch
```

```bash
git merge origin/main
# Merges the fetched changes into the current branch
```

```bash
git pull origin main
# Fetches and automatically merges changes from the main branch
```

```bash
git pull --no-edit origin main
# Pulls and merges changes without opening an editor for the merge message
```

**Tips**:
- Use `fetch` + `merge` to control when you integrate changes.
- `pull` is a shortcut for `fetch` + `merge`.
- Commit or stash local changes before pulling to avoid merge errors.

---

## Pushing to Remotes

```bash
git push origin main
# Pushes your local main branch to the origin remote
```

```bash
git push <remote> <branch>
# General format to push changes to any remote and branch
```

**Tips**:
- Always `commit` changes before pushing.
- Push regularly to back up work and share with collaborators.

---

## Dealing with Conflicts

```bash
git pull origin main
# May result in a conflict if remote and local files differ
```

```bash
nano <conflicted-file>
# Opens the conflicted file to manually resolve differences
```

```bash
git add <file>
# Marks the conflict as resolved
```

```bash
git commit -m "Resolved merge conflict in <file>"
# Commits the resolved file
```

**Tips**:
- Conflicts must be resolved manually.
- Use conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`) to identify sections.

---

## Summary of Common Commands

```bash
git init
# Start a new Git repo

git clone <url>
# Copy a repo to your machine

git status
# View changes and track file states

git add <file>
# Stage changes for commit

git commit -m "message"
# Save a snapshot of staged changes

git remote -v
# Show configured remotes

git pull
# Get changes from the remote repo and merge

git push
# Send committed changes to a remote repo
```

**Final Tips**:
- Use remotes for backup and collaboration.
- Commit often with clear messages.
- Keep your local repo in sync with the remote to avoid conflicts.

---












