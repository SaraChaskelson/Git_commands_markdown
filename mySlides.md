---
marp: true
math: mathjax
---
<!-- markdownlint-disable MD033 -->
# **Git Commands\:**

## <t>1.Pre-commit

pre-commit is a tool intended for use within software development processes, and allows you to run automatic tests and tools before committing the code. That is, it is designed to help developers test their code and make sure it meets certain standards before committing to changes in a version control system, such as *Git*.

### 1.1 Pros/cons

- **+ Save time on CI**
you will save some time
- **- Force developers to test before pushing**
This point is distrust in your workers, just disguised. If  you don't trust your developers, fire them, or fire yourself.

### 1.2 Coding examples

- Run

```bash
pre-commit install
```

to install pre-commit into your git hooks.
<br>

- Run

```bash
pre-commit run --all-files
```

to manually run all pre-commit hooks on a repository
<br>

- Run

```bash
git commit --no-verify
```

If you don't want on a specific occasion to go through the hooks

### 1.3 Alternative

JavaScript, Git, GitHub, Python, and jQuery are the most popular alternatives and competitors to pre-commit.

### 1.4 Screenshots

![pre-commit](/assets/pre-commit-install.png)

---

## 2.gitignore

gitignore file is used in a git repository to ignore the files and directories which are unnecessary to project this will be ignored by the git once the changes as been committed to the Remote repository

### 2.1 Pros/cons

- **+ Improves the “signal to noise ratio” for any Git command**
- **+ Allows builds to come from one source.**
- **+ Avoids potentially costly commits of files that shouldn’t be versioned.**
- **- Accidentally ignoring important files:** If an important file is added to .gitignore by mistake, it will not be included in the Git repository and will not reach other developers. This can cause severe problems in identifying and resolving bugs.

### 2.2 Coding examples

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

<br>
- To add or change your global .gitignore file, run the following command:

```bash
git config --global core.excludesfile ~/.gitignore_global
```

This will create the file ~/.gitignore_global. Now you can edit that file the same way as a local .gitignore file. All of your Git repositories will ignore the files and folders listed in the global .gitignore file.

### 2.3 Alternative

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

### 2.4 Screenshot

![ignore](/assets/gitignore.png)

---

## 3.git remote

The git remote command lets you create, view, and delete connections to other repositories. Remote connections are more like bookmarks rather than direct links into other repositories.

### 3.1 Coding examples

- Run

```bash
git remote -v 
```

to see the current remote URL.

- Run

```bash
git remote set-url <old-url> <new-url>
```

to update the remote URL

### 3.2 Alternative

Initialize your local git repository:

```bash
git init --bare
```

Now, you can work with your repository as it has a remote server. But it actually doesn’t have a remote one. The server of this repository is a local one hosted in the folder.

### 3.3 Screenshots

![git-remote](/assets/git-remote.png)

---

## 4.git pull

The git pull command is used to retrieve and download content from a remote repository and update the local repository once it has been downloaded. In Git-based workflows, it's common to merge remote upstream changes into your local repository.
The Git pull command is used to retrieve and merge code changes from the remote repository to the local repository.    Git pull is a combination of two commands, Git fetch followed by Git merge.    In the first step, a Git fetch is performed that downloads content from the required remote repository. The Git merge command then merges multiple commit sequences into a single branch.

### 4.1 Pros/cons

- **+ Easy updating:** If a developer finds out that there are new, updated files on a remote repository like GitHub, they will likely want to copy those changes from GitHub to both their local repository and into their working directory.  

- **+** git pull is basically a shortcut for:

    ```bash
    git fetch ... 
    ```

    followed by

    ```bash
    git merge ...
    ```

- **- using git pull , puts us at risk of turning our PR branch:**
(and the upstream branch if the changes are merged) into a merge-commits spaghetti or even merging changes from unexpected remote branches into our PR branch.

### 4.2 Coding examples

- Run

```bash
git pull --rebase
```

to change the default pull strategy

### 4.3 Alternative

`git fetch` + `git merge`

### 4.4 Screenshots

![git pull](/assets/pull-vs-fetch.png)
![pull](/assets/pull.jpg)

---

## 5.git push

The command git push is used to transfer the commits or pushing the contect fron the local repository to the remote repository.
The command is used after a local repository has been modified, and the modifications are to be shared with the remote team members.

### 5.1 Pros/cons

- **+ Far Updated:** Allows to update the distant databases with the changes made in local reservoirs.

- **- Risk to delete changes:** Incorrect use of the command can cause important changes in the remote reservoir.

### 5.2 Coding examples

- Run

    ```bash
    git push -u origin [branch]
    ```

    this creates an upstream tracking branch with a lasting relationship to your local branch

### 5.3 Alternative

- Using external files:

The code can be shared using external files such as network drives, mobile drives or cloud storage services (Dropbox, Google Drive, etc.).

### Screenshots

![git push](/assets/git-push.png)

---

## 6.git stash

The git stash command takes your uncommitted changes (both staged and unstaged), saves them away for later use, and then reverts them from your working copy.

### 6.1 Pros/cons

- **+** The git stash command will help a developer switch branches to work on something else without committing to incomplete work

- **+ smooth and clean workflow:** git stash is a flexible tool that helps maintain a smooth and clean workflow.

- **- Forgot to restore the changes:** It's easy to forget that the changes have been kept in STASH. If you do not recover the changes at the appropriate time, they may remain aside and not enter your current job.

### 6.2 Coding examples

- Run

```bash
git stash pop
```

to restore the stashed changes and schedules the stash for deletion from the reference
<br>

- Run

```bash
git stash list
```

to get the stash list.

### 6.3 Alternative

Instead of keeping the changes aside with Git Stash, you can create a temporary branch and keep the changes.

```bash
git checkout -b temporary-branch
```

### 6.4 Screenshots

![stash](/assets/stash.png)

---

## 7.git fetch

The git fetch command downloads commits, files, and refs from a remote repository into your local repo. Fetching is what you do when you want to see what everybody else has been working on.

### 7.1 Pros/cons

- **+ Keeping the current work tree:**
Git Fetch does not change your current work tree or local branches, allowing you to check the changes before merging.

- **+ Tracking remote changes:**
Allows to see all the updates and changes made in the remote reservoir.
Conflict Prevention:

- **+** Allows to check the changes and prepare for mergers in a neat way

- **- The complexity of the process:** Requires additional actions to perform the merger after FETCH, which may be complicated to beginner users. branches to work on something else without committing to incomplete work**

### 7.2 Coding examples

- Run

```bash
git fetch origin
```

to synchronize your local repository with the central repository's main branch.

### 7.3 Alternative

Git Pull is a combination of `Git Fetch` and `Git Merge` in one action. It brings the changes from the remote reservoir and automatically merges them with your local industry.

```bash
git pull
```

---

## 8.Git's command which force

In `Git`, there are several commands that use the `--force` flag. Using this option can be very powerful, but also dangerous if not used correctly, as it can change existing history and bypass restrictions.

### 8.1 Pros/cons

- **+ Clean and tidy history: Proper** use of the `--force` option can lead to a project with a clean and tidy history, making it easier to track and manage the code over time
- **- Dangerous if not used correctly:** As it can change existing history and bypass restrictions.

### 8.2 Coding examples

- Run

```bash
git checkout  --force
```

To force Git to switch branches, undo any uncommitted changes or local
changes to the current branch.

- Run

```bash
git branch -f <branch_name> <commit_hash>
```

To forces Git to move a certain branch to a new commit.

- Run

```bash
git push --force -u origin 
```

To replace the remote repository to match exactly what your
local repository looked like when you ran the command

### 8.3 Alternative

In general, the --force option exists in various Git commands, so there is no
general alternative, but each command has its own equivalent alternative: **without the `--force` flag**.
I will give an example:

- Run

```bash
git push --force-with-release origin
```

To verify that there are no additional changes in the remote repository since the last time you performed a fetch or pull.
If there are more changes, this flag will raise an error to prevent you from overriding the new commits.

### 8.4 Screenshots

![force](/assets/pull-with-force.png)

---

## 9.Good git commit messages

A commit message is descriptive text that is added to the commit object by the developer who made the commit. It has a title line, and an optional body.

A **good commitment message** is one that clearly and succinctly says what has changed, and why it has changed.

### 9.1 Pros/cons

**+ creating quality commit messages makes using and collaborating with Git a lot easier:**

1. To help a future reader quickly understand what changed and why it changed
2. To assist with easily undoing specific changes
3. To prepare change notes or bump versions for a release

### 9.2 Coding examples

- Run

```bash
git commit -m "Add Account Delete Route"
```

To add the header message directly from the command line.

- Run

```bash
git log
```

In order to view the list of commits performed in the current repository

### 9.3 Alternative

Writing a good commitment message is too important to find an alternative...
If in any case you want to commit to a change without notice, use the command

- Run

```bash
git commit -a --allow-empty-message -m ""
```

To commit without a message.

### 9.4 Screenshots

![commit](/assets/commit.png)

---

## 10.Advanced markdown

Sometimes we will want to use an illustration for a more detailed description or explanation.
For this we will use advanced notation.
There are different types of advanced markdowns, for example:

- Mermaid
- Math

**Mermaid** is a JavaScript-based tool that transforms Markdown-style text into dynamic diagrams, allowing you to create and modify them effortlessly.

With Mermaid, you can generate the following diagram types:

- Flowchart
- Sequence Diagram
- Class Diagram
- Gantt
- Pie Chart

In order to combine mathematical expressions we will use `$` or `$$`.

### 10.1 Pros/cons

- **+ Saves cumbersome descriptions and explanations:**
Any process or distribution can be illustrated using Mermaid.
- **-** You need to know well the syntax of writing used for illustration.

### 10.2 Coding examples

- Write

```bash
    '```mermaid
    flowchart TD;
        A[Start] --> B[Process 1];
        B --> C[Process 2];
        C --> D[End];
    '```
```

To get the following flowchart.

```mermaid
flowchart TD;
    A[Start] --> B[Process 1];
    B --> C[Process 2];
    C --> D[End];
```

- Write

```bash
$a \ne 0$ 
or
$(ax^2 + bx + c = 0)$
```

To get the mathematical expressions:

$a \ne 0$
$(ax^2 + bx + c = 0)$

### 10.3 Alternative

If you get into trouble, you can attach pictures instead of messing with mermaid and math
You can display an image by adding ! and wrapping the alt text in [ ]. Alt text is a short text equivalent of the information in the image. Then, wrap the link for the image in parentheses ().

### 10.4 Screenshots

![mermaid](/assets/pie-chart.png)
<br>
<br>
**Hope you enjoyed reading the article!**
🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓
