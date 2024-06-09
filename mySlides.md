---
marp: true
---

# **Git Commands\:**

- ## **pre-commit**

pre-commit is a tool intended for use within software development processes, and allows you to run automatic tests and tools before committing the code. That is, it is designed to help developers test their code and make sure it meets certain standards before committing to changes in a version control system, such as *Git*.

### Pros/cons

- **+ Save time on CI**
 you will save some time
- **- Force developers to test before pushing**
This point is distrust in your workers, just disguised. If you don't trust your developers, fire them, or fire yourself.

### Coding examples

- run

```bash
pre-commit install
```

to install pre-commit into your git hooks.

- run

```bash
pre-commit run --all-files
```

 to manually run all pre-commit hooks on a repository

- run

```bash
git commit --no-verify
```

If you don't want on a specific occasion to go through the hooks

### Alternative

JavaScript, Git, GitHub, Python, and jQuery are the most popular alternatives and competitors to pre-commit.

### Screenshots

![pre-commit](/assets/pre-commit-install.png)

---

- ## **.gitignore**

gitignore file is used in a git repository to ignore the files and directories which are unnecessary to project this will be ignored by the git once the changes as been committed to the Remote repository

### Pros/cons

- **+ Improves the “signal to noise ratio” for any Git command.**
- **+ Allows builds to come from one source.**
- **+ Avoids potentially costly commits of files that shouldn’t be versioned.**

### Coding examples

- This is an example of what the .gitignore file could look like:

```bash
# Ignore Mac system files
.DS_store

# Ignore node_modules folder
node_modules

# Ignore all text files
*.txt

# Ignore files related to API keys
.env

# Ignore SASS config files
.sass-cache
```

- To add or change your global .gitignore file, run the following command:

```bash
git config --global core.excludesfile ~/.gitignore_global
```

This will create the file ~/.gitignore_global. Now you can edit that file the same way as a local .gitignore file. All of your Git repositories will ignore the files and folders listed in the global .gitignore file.

### Alternative

- assume-unchanged

The assume-unchanged option was envisioned as a performance aid but is often mentioned in the context of workarounds to ignore files. You explicitly tell Git not to check if the file has been changed. This method is planned to be applied to files that you want TRACKED, LOCAL CHANGES IGNORED.

Here are the commands you will need for this method:

To ignore local changes to tracked files:

```bash
git update-index --assume-unchanged [<file>...]
```

To track local changes again:

```bash
git update-index --no-assume-unchanged [<file>...]
```

To list all files assumed unchanged:

```bash
git ls-files -v | grep '^[[:lower:]]'
```

### Screenshot

![ignore](/assets/gitignore.png)

---

- ## **git remote**

   The git remote command lets you create, view, and delete connections to other repositories. Remote connections are more like bookmarks rather than direct links into other repositories.

### Coding examples

- run

```bash
git remote -v 
```

to see the current remote URL.

- run

```bash
git remote set-url <old-url> <new-url>
```

to update the remote URL

### Alternative

Initialize your local git repository:

```bash
 git init --bare
```

Now, you can work with your repository as it has a remote server. But it actually doesn’t have a remote one. The server of this repository is a local one hosted in the folder.

### Screenshots

![git-remote](/assets/git-remote.png)

---

- ## **git pull**

    The git pull command is used to retrieve and download content from a remote repository and update the local repository once it has been downloaded. In Git-based workflows, it's common to merge remote upstream changes into your local repository.
    The Git pull command is used to retrieve and merge code changes from the remote repository to the local repository.    Git pull is a combination of two commands, Git fetch followed by Git merge.    In the first step, a Git fetch is performed that downloads content from the required remote repository. The Git merge command then merges multiple commit sequences into a single branch.

### Pros/cons

- **+ If a developer finds out that there are new, updated files on a remote repository like GitHub, they will likely want to copy those changes from GitHub to both their local repository and into their working directory.**  

- **+ git pull is basically a shortcut for**

```bash
 git fetch ... 
 ```

followed by

 ```bash
  git merge ...
 ```

- **- using git pull , puts us at risk of turning our PR branch**
(and the upstream branch if the changes are merged) into a merge-commits spaghetti or even merging changes from unexpected remote branches into our PR branch.

### Coding examples

- run

```bash
git pull --rebase
```

to change the default pull strategy

### Alternative

`git fetch` + `git merge`

### Screenshots

![git pull](/assets/pull-vs-fetch.png)
![pull](/assets/pull.jpg)

---

- ## **git push**

    The command git push is used to transfer the commits or pushing the contect fron the local repository to the remote repository.
    The command is used after a local repository has been modified, and the modifications are to be shared with the remote team members.

### Pros/cons

- **+ Far Updated:**

Allows to update the distant databases with the changes made in local reservoirs.

- **- Risk to delete changes:**

Incorrect use of the command can cause important changes in the remote reservoir.

### Coding examples

- run

```bash
git push -u origin [branch]
```

this creates an upstream tracking branch with a lasting relationship to your local branch

### Alternative

- Using external files:

 The code can be shared using external files such as network drives, mobile drives or cloud storage services (Dropbox, Google Drive, etc.).

### Screenshots

![git push](/assets/git-push.png)

---

- ## **git stash**

    The git stash command takes your uncommitted changes (both staged and unstaged), saves them away for later use, and then reverts them from your working copy.

### Pros/cons

- **+ The git stash command will help a developer switch branches to work on something else without committing to incomplete work**  

- **+ git stash is a flexible tool that helps maintain a smooth and clean workflow.**

- **- Forgot to restore the changes**

It's easy to forget that the changes have been kept in STASH. If you do not recover the changes at the appropriate time, they may remain aside and not enter your current job.

### Coding examples

- run

```bash
git stash pop
```

to restore the stashed changes and schedules the stash for deletion from the reference

- run

```bash
git stash list
```

 to get the stash list.

### Alternative

Instead of keeping the changes aside with Git Stash, you can create a temporary branch and keep the changes.

```bash
git checkout -b temporary-branch
```

### Screenshots

![stash](/assets/stash.png)

---

- ## **git fetch**

The git fetch command downloads commits, files, and refs from a remote repository into your local repo. Fetching is what you do when you want to see what everybody else has been working on.
### Pros/cons

- **+ Keeping the current work tree:**

Git Fetch does not change your current work tree or local branches, allowing you to check the changes before merging.

- **+ Tracking remote changes:**

Allows to see all the updates and changes made in the remote reservoir.
Conflict Prevention:

- **+ Allows to check the changes and prepare for mergers in a neat way**

- **- The complexity of the process:**

Requires additional actions to perform the merger after FETCH, which may be complicated to beginner users. branches to work on something else without committing to incomplete work**

### Coding examples:

- run

```bash
git fetch origin
```

 to synchronize your local repository with the central repository's main branch.

### Alternative

Git Pull is a combination of `Git Fetch` and `Git Merge` in one action. It brings the changes from the remote reservoir and automatically merges them with your local industry.

```bash
git pull
```

---

- Git's command which force.
- Good git commit messages.
- Advanced markdown: (mermaid, math).
