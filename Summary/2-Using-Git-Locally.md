# 2 Using Git Locally
## 2.1 Advanced Git interaction
```
git commit -a -m "commit message"
```
This command stages all changes to tracked files and commits them with the specified message in a single command.

```
git log -p
```
This command shows the commit history with detailed patch information:

-   **Commit Information**: Displays commit hash, author, date, and commit message.
-   **Patch Information**: Shows file changes with lines added (preceded by `+`) and lines removed (preceded by `-`).

```
git log --stat
```
This command displays the commit history along with a summary of changes for each commit:

-   **Commit Information**: Shows commit hash, author, date, and commit message.
-   **File Change Summary**: Lists files that were changed in each commit and includes the number of insertions and deletions for each file.
-   **Stat Summary**: Provides a brief summary of the total insertions, deletions, and number of files changed for each commit.

```
git show [commit_id]
```
This command provides a detailed view of the specified commit, including metadata and the changes made to the files.

```
git diff [file_name]
```
This command shows the changes made to a specific file in your working directory that are not yet staged for commit.

```
git diff --staged [file_name]
```
This command shows the changes that have been staged for the next commit for a specific file.

```
git add -p
```
This command allows you to interactively stage changes in your working directory:
-   **Interactive Staging**: Splits the changes into manageable hunks and prompts you to decide whether to stage each hunk.
-   **Hunk-by-Hunk Decisions**: You can choose to stage (`y`), skip (`n`), split into smaller hunks (`s`), or view the diff (`d`), among other options.

```
git rm [file_name]
```
This command removes a file from both the working directory and the staging area:

-   **File Removal**: Deletes the specified file from the working directory.
-   **Staging for Removal**: Stages the file's removal for the next commit.

```
git mv [old_file_name] [new_file_name]
git mv [file_name] [dir_path]
```
This command is used to rename or move a file or directory and stage the changes for the next commit:

-   **Renaming/Moving**: Renames or moves the specified file or directory.
-   **Staging the Changes**: Automatically stages the renaming or moving operation for the next commit.

> There are many useful git command summaries online as well. Please take some time to research and study a few, such as [this one](https://education.github.com/git-cheat-sheet-education.pdf).

> ### .gitignore** files
> .gitignore files are used to tell the git tool to intentionally ignore some files in a given Git repository. For example, this can be useful for configuration files or metadata files that a user may not want to check into the master branch.
> 
> When writing a .gitignore file, there are some specific formats which help tell Git how to read the text in the file. For example, a line starting with # is a comment; a slash / is a directory separator. Visit [https://git-scm.com/docs/gitignore](https://git-scm.com/docs/gitignore) to see more examples.
>
> [This GitHub repository](https://gist.github.com/octocat/9257657) offers some examples of configurations which are often included in a .gitignore file. These examples include: compiled sources, packages, logs, databases, and OS generated files.

## 2.2 Undoing Things
```
git checkout [file_name]
```
command is used to discard changes in the working directory for a specific file:

-   **Undo Local Changes**: Replaces the file in the working directory with the last committed version from the current branch, discarding any changes made since the last commit.

- **Important Note**: This command only affects the working directory. It does not undo changes that have already been staged or committed.

```
git checkout -p [file_name]
```
This command allows you to interactively discard changes in a file, hunk by hunk:

-   **Interactive Undoing**: Splits the changes in the specified file into manageable hunks and prompts you to decide whether to discard each hunk.
-   **Hunk-by-Hunk Decisions**: You can choose to discard (`y`), skip (`n`), or view the diff (`d`), among other options.

```
git reset HEAD [file_name]
```
This command is used to unstage changes for a specific file that have been added to the staging area, without affecting the working directory:

-   **Unstaging Changes**: Removes the specified file from the staging area, effectively unstaging it.
-   **Preserving Working Directory**: Keeps the changes in the working directory, so they can be modified further or re-staged later.

```
git reset -p HEAD [file_name]
```
This command allows you to interactively unstage changes for a specific file, hunk by hunk:

-   **Interactive Unstaging**: Splits the staged changes into manageable hunks and prompts you to decide whether to unstage each hunk.
-   **Hunk-by-Hunk Decisions**: You can choose to unstage (`y`), skip (`n`), or view the diff (`d`), among other options.

```
git commit --amend
```
This command is used to modify the most recent commit. It allows you to combine staged changes with the previous commit or to update the commit message.

- **Combining Staged Changes with the Last Commit**:
    
    -   If you forgot to include some changes in your last commit, you can stage those changes and use `git commit --amend` to add them to the previous commit.
- **Updating the Commit Message**:
    
    -   If you want to change the commit message of the most recent commit, you can use this command to do so.

```
git revert [commit_id / HEAD]
```
This command is used to create a new commit that undoes the changes introduced by a specified commit without altering the commit history:

-   **Creating a Revert Commit**: Generates a new commit that reverses the changes of the specified commit.
-   **Preserving History**: Unlike `git reset`, which can change the commit history, `git revert` maintains a complete history by adding a new commit.

> For more information on these and other methods to undo something in Git, checkout this [Git Basics - Undoing Things](https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things) article.

>Additionally, there are some interesting considerations about how git object data is stored, such as the usage of SHA-1. This is what’s known as a _hash function_, a cryptographic function that generates a digital fingerprint of a file. Theoretically, it’s impossible for two different files to have the same SHA-1 hash, which means that SHA-1 can be used for two things:
>
> -   Confirming that the contents of a file have not changed (digital signature).
>  
> -   Serving as an identifier for the file itself (a token or fingerprint).
> 
> Git calculates a hash for every commit. Those hashes are displayed by commands like git log or in various pages on Github. For commands like git revert, you can then use the hash to refer to a specific commit.
>
> Feel free to read more here: [SHA-1 collision detection on GitHub.com](https://github.blog/2017-03-20-sha-1-collision-detection-on-github-com/)

## 2.3 Branching and Merging
```
git branch [branch_name]
```
This command creates a new branch named `branch_name` at the current commit without switching to it.

```
git checkout [branch_name]
```
This command switches the working directory to the specified branch, allowing you to work on different lines of development.

```
git checkout -b [branch_name]
```
This command creates a new branch named `branch_name` and switches to it, updating the working directory to reflect the state of the new branch. This is a convenient way to start working on a new branch immediately after creating it.

```
git branch -d [branch_name]
```
command safely deletes the specified branch if it has been fully merged into its upstream branch, ensuring no unmerged work is lost. If the branch has not been merged, you can use `git branch -D [branch_name]` to force delete it.

```
git merge [branch_name]
```
This command integrates changes from the specified branch into the current branch, combining their commit histories. Depending on the changes, it may create a merge commit or prompt for conflict resolution.

Possible Scenarios:

-   **Fast-Forward Merge**: If the current branch is directly behind the specified branch, the current branch pointer is simply moved forward.
-   **Merge Commit (Three-Way Merge)**: If there are divergent changes, a new commit is created to combine the histories of both branches.
-   **Conflicts**: If there are conflicting changes, Git will prompt you to resolve the conflicts manually before completing the merge.

```
git merge --abort
```
This command cancels an ongoing merge process and restores the repository to its state before the merge began, allowing you to start over or make different decisions without affecting the repository's history.

When to Use:

-   **Conflict Resolution**: If you encounter conflicts during a merge and decide not to proceed with resolving them, you can abort the merge.
-   **Incorrect Merge**: If you realize that you started a merge by mistake or need to re-evaluate the merge process.

```
git log --graph --oneline
```
This command provides a concise, graphical view of the commit history, showing the relationships between branches and commits in a clear and easy-to-read format.

## 2.4 Glossary Terms

**Branch:** A pointer to a particular commit, representing an independent line of development in a project

**Commit ID:** An identifier next to the word commit in the log

**Fast-forward merge:** A merge when all the commits in the checked out branch are also in the branch that's being merged

**Head:** This points to the top of the branch that is being used

**Master:** The default branch that Git creates for when a new repository initialized, commonly used to place the approved pieces of a project

**Merge conflict:** This occurs when the changes are made on the same part of the same file, and Git won't know how to merge those changes

**Rollback:** The act of reverting changes made to software to a previous state

**Three-way merge:** A merge when the snapshots at the two branch tips with the most recent common ancestor, the commit before the divergence
