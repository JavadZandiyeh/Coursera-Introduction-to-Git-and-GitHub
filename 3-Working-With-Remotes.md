# 3 Working With Remotes
## 3.1 Introduction to GitHub
> ### Basic Interaction with GitHub:
> There are various remote repository hosting sites:
> -   [GitHub](http://github.com/)
> -   [BitBucket](https://bitbucket.org/product)
> -   [Gitlab](https://gitlab.com/).
> 
> Follow the workflow at [https://github.com/join](https://github.com/join) to set up a free account, username, and password. After that, [these steps](https://help.github.com/articles/create-a-repo/) will help you create a brand new repository on GitHub.

```
git clone [repository] [directory]
```
This command creates a copy of an existing repository from a remote or local source, where `repository` is the URL or path and `directory` is the optional target directory name.

```
git push [remote] [branch]
```
This command uploads local repository content to a remote repository, where `remote` is the name of the remote repository and `branch` is the name of the branch to push.

```
git pull [remote] [branch]
```
This command fetches changes from a remote repository and merges them into the current branch, where `remote` is the name of the remote repository and `branch` is the name of the branch to pull.

```
git config --global credential.helper cache
```
This command configures Git to cache user credentials in memory for a specified time. This avoids repeatedly entering credentials for multiple operations.

> This can be useful for keeping your local workspace up to date.
> -   [https://help.github.com/en/articles/caching-your-github-password-in-git](https://help.github.com/en/articles/caching-your-github-password-in-git)
> -   [https://help.github.com/en/articles/generating-an-ssh-key](https://help.github.com/en/articles/generating-an-ssh-key)

## 3.2 Using a Remote Repository
```
git remote -v
```
This command lists all remote repositories associated with the local repository, showing their names and the corresponding fetch and push URLs, helping you manage and verify remote connections.

```
git remote
```
This command is used to manage remote repositories, with the basic usage listing the names of all remotes. Additional options allow you to add, remove, rename, and display detailed information about remotes.

```
git remote show [remote]
```
This command provides a detailed overview of the specified remote repository, including URLs and branch tracking information.

```
git branch -r
```
This command shows all remote-tracking branches, allowing you to view branches from remote repositories that your local repository is aware of.

```
git fetch
git fetch [remote] [branch]
```
This command updates your local repository with changes from the remote repository, without modifying your local branches.

```
git log [remote]/[branch]
```
This command shows the commit history of the specified remote branch, allowing you to view changes and commits made to that branch on the remote repository.

```
git merge [remote]/[branch]
```
This command merges the specified remote branch into the current local branch, incorporating changes from the remote repository into your local branch.

> Note: `git pull` = `git fetch` and then (`git merge` or `git rebase`)

```
git checkout [remote]/[branch]
```
This command creates a new local branch from the specified remote branch and switches to it, allowing you to work with the remote branch locally.

```
git remote update
```
This command refreshes all remote-tracking branches by fetching updates from all configured remotes, keeping your local view of the remote repositories up-to-date.

## 3.3 Solving Conflicts
```
git log --oneline --graph --all
```
This command presents a concise, visual overview of the commit history across all branches, showing commits in a single-line format with a graphical representation of branch structures.

```
git rebase [branch]
```
This command reapplies your current branch's commits on top of the specified branch.

```
git rebase --abort
```
This command stops the rebase operation and returns your branch to its previous state before the rebase began.

```
git rebase --continue
```
This command resumes the rebase operation after resolving conflicts, continuing to apply the remaining commits.

```
git rebase --skip
```
This command skips the problematic commit during a rebase and continues with the next commit, useful when a specific commit is causing issues.

```
git push -u [remote] [branch]
```
This command uploads the specified branch to the remote repository and sets up tracking, simplifying future synchronization between the local and remote branches.

```
git push --delete [remote] [branch]
```
This command removes the specified branch from the remote repository, cleaning up branches that are no longer needed.

```
git branch -d [branch]
```
This command deletes the specified local branch, provided it has been fully merged to prevent loss of unmerged work.

## 3.4 Practical Tips
1. **Always pull changes from the remote repository before pushing your local changes** to ensure that you resolve any conflicts between your local and remote changes. Follow these steps:

   A) **Fetch the latest changes from the remote repository**:
   ```sh
   git fetch
   ```
   - This updates your local remote-tracking branches with the latest changes from the remote repository.

   B) **Merge the fetched changes into your current branch**:
   ```sh
   git merge [remote]/[branch_name]
   ```
   - Replace `[branch_name]` with the name of your current branch.
   - Resolve any merge conflicts that arise during this process.

   C) **Commit any resolved changes** (if there were conflicts):
   ```sh
   git add [file_name]
   git commit -m "Resolved merge conflicts"
   ```
   - Replace `[file_name]` with the names of files you modified to resolve conflicts.

   D) **Push your local changes to the remote repository**:
   ```sh
   git push
   ```
   - This updates the remote repository with your local commits.

2. **Use the rebase option rather than the merge option to make the commit history linear**. Follow these steps:

   A) **Rebase your local branch onto the latest changes from the remote branch**:
   ```sh
   git fetch
   git rebase [remote]/[branch_name]
   ```
   - Replace `[branch_name]` with the name of your current branch.
   - This updates your local branch to include the latest changes from the remote branch and re-applies your local commits on top of these changes, creating a linear history.

   B) **Resolve any conflicts that occur during the rebase**:
   ```sh
   git add [file_name]
   git rebase --continue
   ```
   - Replace `[file_name]` with the names of files you modified to resolve conflicts.

   C) **Push your rebased changes to the remote repository**:
   ```sh
   git push --force
   ```
   - This updates the remote branch with your rebased commits. The `--force` option is needed because the rebase rewrites commit history.

   D) **(Optional) If necessary, delete the remote branch** (e.g., if you are cleaning up branches):
   ```sh
   git push --delete [remote] [branch]
   ```
   - Replace `[remote]` with the remote name and `[branch]` with the branch name.

   E) **(Optional) Delete your local branch** (e.g., if it’s no longer needed):
   ```sh
   git branch -d [branch]
   ```
   - Replace `[branch]` with the branch name you wish to delete.

3. **Always synchronize your branches before starting any work on your own.**
4. **Avoid having very large changes that modify a lot of different things.**
5. **When working on a big change, it makes sense to have a separate feature branch.**
6. **Regularly merge changes made on the master branch back onto the feature branch.**
7. **Have the latest version of the project in the master branch, and the stable version of the project on a separate branch.**
8. **You shouldn't rebase changes that have been pushed to remote repos.**
9. **Having good commit messages is important.**

## 3.4 Glossary Terms
**Application Programming Interface (API) key:** This is an authentication token that calls an API, which is then called to identify the person, programmer, or program trying to access a website

**Computer protocols:** Guidelines published as open standards so that any given protocol can be implemented in various products

**Distributed:** Each developer has a copy of the whole repository on their local machine

**GitHub:** A web-based Git repository hosting service, allowing users to share and access repositories on the web and copy or clone them to a local computer

**Merge:** An operation that merges the origin/master branch into a local master branch

**Private key:** A secret and secure cryptographic key that must be kept confidential and protected and is used to decrypt data that has been encrypted with the corresponding public key

**Public key**: A safety cryptographic structure frequently employed to establish secure communication through data encryption or to validate the authenticity of a digital signature

**Rebasing:** The base commit that's used for a branch is changed

**Remote branches:** Git uses read-only branches to keep copies of the data that's stored in the remote repository

**Remote repositories:** Repositories that allow developers to contribute to a project from their own workstations making changes to local copies of the project independently of one another

**Secure Shell (SSH):** A robust protocol for connecting to servers remotely

**SSH client:** This establishes a connection to the SSH server, ensuring a secure interaction, where the client makes access requests

**SSH key:** An access credential

**SSH protocol:** Standard commonly used for logging in to servers remotely on the principle of public-key encryption

**SSH server:** This establishes secure network connections, undergoes mutual authentication, and initiates encrypted login sessions or file transfers
